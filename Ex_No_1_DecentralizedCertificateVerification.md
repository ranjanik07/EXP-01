### Experiment 1: Decentralized Certificate Verification

### Name: Ranjani k
### Reg no: 212224230220

## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```

# Output

# Issue Certificate:

<img width="1600" height="940" alt="f7e9fb6d-3a71-436c-8e0f-ac95d0bc0090" src="https://github.com/user-attachments/assets/77e8206d-fd24-408d-a45d-28156e3e2ce1" />

# True:
<img width="1920" height="1128" alt="Screenshot 2026-08-14 112327" src="https://github.com/user-attachments/assets/7a6721b9-4c6b-44d2-b571-255ec800b52b" />

# False:
<img width="1920" height="1128" alt="Screenshot 2026-08-14 112459" src="https://github.com/user-attachments/assets/fa51c52d-8893-4cd3-b9eb-629fdeb2e22d" />


# Result:
Smart contract for issuing and verifying certificate on Ethereum is successfully executed.

