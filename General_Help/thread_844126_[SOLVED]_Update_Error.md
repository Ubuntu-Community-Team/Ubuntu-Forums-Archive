---
title: "[SOLVED] Update Error"
date: 2008-06-29
forum: General Help
---

### Post by guss606 on 2008-06-29
I run Ubuntu 8.04 LTS, today i wanted to update using update manager, i get the following error message when i press on check:

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

I'm new to Ubuntu, i don't know whats that mean? and what do i have to do? i would appreciate your help very much.
thank you.

---

### Post by Rocket2DMn on 2008-06-29
Is this problem fixed?  It was most likely a problem with the repository.  Run
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kaola_linux on 2008-06-30
> **guss606 said:**
> I run Ubuntu 8.04 LTS, today i wanted to update using update manager, i get the following error message when i press on check:

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

I'm new to Ubuntu, i don't know whats that mean? and what do i have to do? i would appreciate your help very much.
thank you.


I have the same error also, I'm using Ubuntu 8.04 AMD64 version..Had this since my first update but I've managed to update some..can someone help? The above solution doesn't help because I've alread tried it..Anyone out there? :confused:

---

### Post by guss606 on 2008-06-30
i tried that before, and i got the same error message:-k

---

### Post by Rocket2DMn on 2008-06-30
You can try switching repositories from System->Administration->Software Sources and selecting a different mirror.

---

### Post by guss606 on 2008-06-30
> You can try switching repositories from System->Administration->Software Sources and selecting a different mirror.

i tried that, and clicked on (choose best server).. and it worked so fine,, thanks a lot.. the problem is solved:D:D

---

### Post by minhaaj on 2008-07-15
Had some problem. solved using the trick. Ubuntu rocks

---

### Post by allensaucier on 2009-04-28
thank you gentlemen!!! this worked for me too!:popcorn:

---

### Post by ceefour on 2009-05-07
if still unsolved, see:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

---

### Post by ceefour on 2009-05-07
if still unsolved, see:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

---

### Post by Demrtnz on 2010-08-06
> **Rocket2DMn said:**
> Is this problem fixed?  It was most likely a problem with the repository.  Run
```
sudo apt-get update
sudo apt-get upgrade
```
i had the same problem and this trick worked perfectly!!! thanks so much! you rock!:KS

---

### Post by energichen on 2010-08-07
I have a similar problem:
GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
Any idea how to solve this?

---

### Post by 14quartz on 2011-12-15
> **Rocket2DMn said:**
> You can try switching repositories from System->Administration->Software Sources and selecting a different mirror.


Yeah that really solved the problem. Thank You so much.

---

