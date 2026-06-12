---
title: "Failed to install Dislocker on Live Ubuntu disk 17.10 or 16.04.3 LTS"
date: 2017-12-20
forum: General Help
---

### Post by avinaash291 on 2017-12-20
I want to access my Windows drives in Ubuntu. Tried to install **dislocker** to decrypt and mount the drive on Ubuntu. I could successfully install all the packages required but not *libmbedTLS*. I downloaded and installed *mbedTLS* package manually and performed check as per the instructions. All tests passed.


But when I used cmake . to install dislocker, it said Could NOT find POLARSSL. I manually installed *polarSSL_1.2.19* and all the tests passed. When I try installing dislocker, I got 'Could not find polarSSL errors' again. Please help!

I tried these steps using Ubuntu 17.10 and Ubuntu 16.04.3LTS.

---

### Post by slickymaster on 2017-12-25
*Thread moved to **General Help**.*

---

### Post by deadflowr on 2017-12-25
dislocker is available in Ubuntu's software packages for 17.10.
From a live cd you would need to enable the universe repository.
(to enable universe go to Software and Updates and check that the Community source is checked
then close Software and Updates and let it reload)
Then open a terminal and run
```
sudo apt install dislocker
```
if by chance it says no package found, then the reposiotry was not added, so you'll need to try to run the reload manually:
to do so run
```
sudo apt update
```
then re-try the install command.

---

### Post by avinaash291 on 2017-12-26
Thanks a lot deadflowr! It helped. I could install dislocker successfully.

---

