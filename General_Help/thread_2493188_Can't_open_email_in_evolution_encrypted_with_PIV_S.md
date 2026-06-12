---
title: "Can't open email in evolution encrypted with PIV S/MIME"
date: 2023-12-06
forum: General Help
---

### Post by chubbypiper on 2023-12-06
I have a PIV compliant card that I have been able to use to S/MIME encrypt emails in Evolution.  Now whenever I encrypt an email, I get prompted for the passphrase for it, and it says it successfully encrypts the email, but I can no longer view it in Evolution.   When I try it on an Outlook install on a Windows desktop I have access to, I can't view the email either.  

However, I know this all works because I can encrypt an email in Outlook, and then view it in both Outlook and Evolution.  

I confirmed that the correct cert is being used for the encryption.  Signing is working correctly, it looks like encryption is the only thing that is affected. 

The error I am seeing is "Could not parse S/MIME message: The operation failed because the PKCS#11 token is not logged in. (-8037) - Decoder failed"  right before this I am prompted for my cert passphrase

I am currently on Ubuntu 22.04

evolution-common/jammy-updates,jammy-updates,jammy-security,jammy-security,now 3.44.4-0ubuntu2 all [installed,automatic]
evolution-data-server-common/jammy-updates,jammy-updates,jammy-security,jammy-security,now 3.44.4-0ubuntu1.1 all [installed,automatic]
evolution-data-server/jammy-updates,jammy-security,now 3.44.4-0ubuntu1.1 amd64 [installed,automatic]
evolution-ews/jammy,now 3.44.0-1 amd64 [installed]
evolution-plugin-bogofilter/jammy-updates,jammy-security,now 3.44.4-0ubuntu2 amd64 [installed,automatic]
evolution-plugin-pstimport/jammy-updates,jammy-security,now 3.44.4-0ubuntu2 amd64 [installed,automatic]
evolution-plugins/jammy-updates,jammy-security,now 3.44.4-0ubuntu2 amd64 [installed,automatic]
evolution/jammy-updates,jammy-security,now 3.44.4-0ubuntu2 amd64 [installed]
libevolution/jammy-updates,jammy-security,now 3.44.4-0ubuntu2 amd64 [installed,automatic]

opensc-pkcs11/jammy,now 0.22.0-1ubuntu2 amd64 [installed,automatic]
opensc/jammy,now 0.22.0-1ubuntu2 amd64 [installed]

---

