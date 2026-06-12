---
title: "GRUB Error 16, Can't boot"
date: 2006-12-06
forum: General Help
---

### Post by eriefisher on 2006-12-06
I turned on my box this morning and received error 16 and then nothing. Please tell me there is a way to fix this without reinstalling. I'm presently dual booting with XP. I think if I remove the Kubuntu drive I will still be able to boot Windows but have not tried.

I'm typing this on the live CD. Please help.

---

### Post by divague on 2006-12-06
Try reinstalling just grub
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by eriefisher on 2006-12-06
Thanks for the link. I'll give it a try.

---

### Post by eriefisher on 2006-12-06
No luck. 
Error 15: file not found

I was able to mount the drive and navigate to /boot/grub but the folder is empty. However this allowed me to atleast copy my files to a usb stick to save.

I think I will just reload the OS and start fresh anyway. I was thinking of putting it on a new drive anyway.

---

### Post by TravMan63 on 2008-03-12
I know I'm posting to an old thread - just had this error occur last night

Dual boot (Ubuntu - ext3, Elive _RiserFS)

I booted Ubuntu recovery mode - (the text was scrolling by rapidly - I THINK it listed - hda5 umounted uncleanly, check forced)

Problem was solved.  I am uncertain which filesystem/partition had the error.

If unable to boot from HD, a live CD (like DSL) and running fsck may fix the error.


Posted in hopes it will help someone in the future!

See
[https://lists.ubuntu.com/archives/ubuntu-bugs/2006-November/342654.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2006-November/342654.html)

---

