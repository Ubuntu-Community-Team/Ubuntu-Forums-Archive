---
title: "Help - deleted kernel on encrypted system 14.04"
date: 2015-08-12
forum: General Help
---

### Post by davemoffsite on 2015-08-12
Hi All,
Okay, I was trying to do some cleanup, copied a script from online, and evidently it blew away my active kernel as well as the old ones. Arrgghh.

System is Ubuntu only, with full drive encryption.

Imediately after, it would only boot to memtest.

I ran Boot-repair disk, and now it boots to a grub prompt. At that time it gave me the URL paste.ubuntu.com/12063952

Reran the boot-repair disk and it gave me the attached file (had to break it into 2 parts to upload).

if I boot from a live disk I can decrypt the drive and get in just fine, but I don't know how to make it 'run' as it were.

How do I get it to rebuild the kernal so I can just get back into the system? OR how do I safely move all the info on to another drive and resinstall linux, then get it all back? I've got a GNUcash installation that I need to be sure to save.

Thanks
David

---

### Post by TheFu on 2015-08-12
> get it all back?

[https://nwrickert2.wordpress.com/2014/04/19/installing-ubuntu-14-04-in-an-encrypted-lvm/](https://nwrickert2.wordpress.com/2014/04/19/installing-ubuntu-14-04-in-an-encrypted-lvm/) looks promising, if you haven't seen it already.

Use your backups. Lacking backups, I think you are at reinstall time and have learned that whenever encryption is used, 100%, great, perfect, know-you-can-restore backups are needed.

I went through this recently myself. The guides I found for manually adding encrypted partitions to a system were out of date.  Took lots of notes as I figured different things out. By that time, I decided my backups would be easier and I'd get a more stable system with a fresh install.  So - you should backup whatever you think is important in the way it requires so it can be restored on a new system.  

If it doesn't work,  try [https://askubuntu.com/questions/403701/etc-crypttab-ignored-on-boot](https://askubuntu.com/questions/403701/etc-crypttab-ignored-on-boot) has a little information.  A vaguely recall there being some grub changes to ensure the initrd has the correctly built too.  

Good luck.

---

