---
title: "apt-get question"
date: 2006-10-19
forum: General Help
---

### Post by Disastorm on 2006-10-19
I don't know how apt-get works but in 
[http://security.ubuntu.com/ubuntu/pool/main/g/glibc/](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/)
it has libc6 2.4 for amd64 but when i check synaptic it doesnt show up there, i have everything enabled in the repositories.  Is there any way to put the stuff in there into my repositories or whatever?  I'm on Dapper.  I know I can install it using dpkg and the .deb but when i tried that it broke some other packages, so i reverted back to fix them.

---

### Post by az on 2006-10-19
> **Disastorm said:**
> I don't know how apt-get works but in 
[http://security.ubuntu.com/ubuntu/pool/main/g/glibc/](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/)
it has libc6 2.4 for amd64 but when i check synaptic it doesnt show up there, i have everything enabled in the repositories.  Is there any way to put the stuff in there into my repositories or whatever?  I'm on Dapper.  I know I can install it using dpkg and the .deb but when i tried that it broke some other packages, so i reverted back to fix them.

It may be an edgy package.  They are all in the pool together.

You can change your sources to point to edgy instead of Dapper and dist-upgrade.

---

### Post by Disastorm on 2006-10-19
will that convert my dapper into edgy?  Is that a good idea?  Is there any reason why edgy is not the main ubuntu yet?

---

