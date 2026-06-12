---
title: "PXE boot Ubuntu NFS mount call fails"
date: 2007-07-25
forum: General Help
---

### Post by Mark Galeck on 2007-07-25
Hello,  

I am trying to PXE boot Ubuntu 7.04.  

I carefully follow the directions in [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

The target system starts to boot and everything seems fine, until it tries to nfs mount the remote filesystem.  I get

Mount call failed:  13
Done
Begin:  Retrying nfs mount...

Then there is a bunch of parameters for the NFS client and server, that seem correct, except perhaps
rootpath:  (nothing here)

and this goes on and on...

I know that nfs server is working properly, because, following the suggestion in the HowTo, I test it first.  During the boot, the IP address of the client asking the server to mount, is the same as tested, according to paramters mentioned above.  

Please tell me what could be wrong here?  Thank you!

Mark Galeck

---

