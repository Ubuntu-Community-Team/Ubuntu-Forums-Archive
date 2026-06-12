---
title: "DVDFab Decrypter 2.9.8.3 w/Wine = No go?"
date: 2006-08-13
forum: General Help
---

### Post by rjpa on 2006-08-13
Hi,

Is there any way to make [**DVDFab Decrypter Express 2.9.8.3**]("http://www.dvdidle.com") run on an Ubuntu Dapper box? If so how? Or is it just "no go"?

Cheers
rjpa

---

### Post by rbmorse on 2006-08-13
I run it under VMware workstation, but VMware server (no-cost) should work OK, too.

---

### Post by rjpa on 2006-08-13
> **rbmorse said:**
> I run it under VMware workstation, but VMware server (no-cost) should work OK, too.
OK,

But how do you then share files between Windows and Linux (using VMWare Tools or what)?

- rjpa

---

### Post by rbmorse on 2006-08-13
With the paid-for version of VMware, VMware Workstation, shared folders are established in VMWare setup. Just type in the path to the desired directories on the host machine. I just created a couple of VFAT partitions and I tell DVDFab to write it's output files to one of those. It is very straight forward.

I'm told the no-cost VMWare workstation requires SAMBA to do the sharing, but it is easily set up...I don't know because I have not had to do that.

---

