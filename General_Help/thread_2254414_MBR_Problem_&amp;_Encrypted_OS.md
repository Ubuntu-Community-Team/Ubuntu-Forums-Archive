---
title: "MBR Problem &amp; Encrypted OS"
date: 2014-11-27
forum: General Help
---

### Post by jamesturnernz on 2014-11-27
Hello,

I have been using Ubuntu for a while, but with 14.04 I wanted to try the encrypted volume option.

It was all working well, then I did something silly and I can not remember what it was.  I had to put the PC to the side until I had more time to fix it.

The drive is dedicated to Ubuntu, there are no other OS's installed.

At the moment, when it tries to boot, it will hang on a black screen with a flashing cursor, then fall back to GRUB.
When I use the Ubuntu option inside GRUB it just loops again.

Today I tried to repair the boot issue using Boot-Repair-Disk
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But it didn't fix the issue and has given me the following report
[http://paste.ubuntu.com/9262129/](http://paste.ubuntu.com/9262129/)

It would be really appreciated if someone might be able to shed some light on what is wrong and how I can fix it.
Thank you,

---

### Post by oldfred on 2014-11-27
Either you did not give passphrase to Boot-Repair to mount the encrypted partition or the partition is damaged & Boot-Repair could not mount it.
With encryption is is harder to resolve issues.

If at grub menu you use e for edit and remove the quiet splash from the linux line and boot, it should show the details of loading everything. While it often stops posting a few lines after the main error, you may get a clue on what is the error.

---

### Post by jamesturnernz on 2014-11-27
Hello oldfred, 

Thank you for the reply.

- Boot-Repair-Disk Boot-Repair never asked me for the password when making the repair
- Removing the `quiet splash` didn't give any new output

What I have done, is mount the encrypted partition inside B-R-D Lubuntu and I have been able to back up the files I wanted.

So I think I will just start again with a fresh install.

Thank you for the help.

---

