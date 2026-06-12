---
title: "Dual boot Gutsy and Feisty?"
date: 2007-11-08
forum: General Help
---

### Post by pdxken on 2007-11-08
Hi.
I am currently dual booting fedora 7.04 and kubuntu 7.04.
I have a /data partition that only kubuntu can use. I tried some suggestions in older posts but gave up trying to get kubuntu to share /data with fedora.
As a result I don't boot fedora any more. I think I like ubuntu better anyway. Still not sure if I like gnome or kde better.

My question: If I replace fedora with ubuntu 7.10, will it share my /data partition with kubuntu 7.04?

It's been several months sense I messed with permissions so I don't remember much. But I think there was a problem with (group?) ID 500 vs ID 1000 or some such. I lost track of how many times I installed and reinstalled ubuntu, kubuntu, and fedora.

I have a older Dell tower with Pentium 4 and 512M RAM. My old XP drive is disconnected, unplugged and unloved. :)

Thanks.
Ken.

---

### Post by dabl on 2007-11-08
> **pdxken said:**
> Hi.

My question: If I replace fedora with ubuntu 7.10, will it share my /data partition with kubuntu 7.04?



Yes, assuming you mount the partition in the new Ubuntu /etc/fstab file (or manually).  :)

---

### Post by pdxken on 2007-11-12
Thanks. ubuntu 7.10 installed and works fine with /data partition.

For some reason when I boot kubuntu 7.04 now it gives an error something like.
"File system check failed. apt-get is currently not installed"
It starts a shell and tells me I can install it by typing "apt-get install apt".
Fascenating. If it is not installed how can I use it to install it'self?

Anyway, It booted OK after control D. Everything seems OK.
I used synaptic to reinstall apt. I still get the error at boot.

IF I can't figure it out I'll just use gutsy for a while or do the CNTRL D thing until I decide to replace kubuntu 7.04 with 7.10.

Or. Any suggestions?

Thanks.
Ken

---

