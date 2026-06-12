---
title: "[SOLVED] Package Repository issue."
date: 2008-06-19
forum: General Help
---

### Post by Greasy on 2008-06-19
Here's the error report. The repositories no longer update, and I can no longer download software from the repository as  I get a connection timeout error.



W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to 83.18.163.50:8080 (83.18.163.50), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_CA.bz2)  Unable to connect to 83.18.163.50 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_CA.bz2)  Unable to connect to 83.18.163.50 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_CA.bz2)  Unable to connect to 83.18.163.50 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_CA.bz2)  Unable to connect to 83.18.163.50 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Greasy on 2008-06-19
Oh sorry, I found the problem I had a proxy set in my GNOME proxies settings thing haha. Damnnn

---

### Post by iaculallad on 2008-06-19
--Nevermind--

---

