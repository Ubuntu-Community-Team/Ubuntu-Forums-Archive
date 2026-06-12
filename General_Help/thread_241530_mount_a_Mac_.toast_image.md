---
title: "mount a Mac .toast image"
date: 2006-08-22
forum: General Help
---

### Post by drpepper on 2006-08-22
Hi

I have a .toast image that I want to mount in ubuntu on my pc, not a mac. When I tried mount:

sudo mount Mac.toast /media/iso/  -t iso9660 -o loop

i got: 

mount: wrong fs type, bad option, bad superblock on /dev/loop/0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I searched google and the forums, but i just keep getting questions about ubuntu on the mac. any ideas? Does it need converting to something else? unfortunatly I don't have access to a mac!

Thanks

---

### Post by shookone on 2006-10-26
mount -o loop -t hfsplus imagename.toast [mount point]

Try that

---

