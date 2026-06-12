---
title: "sudo rm -rf /usr/bin || recovery or other options?"
date: 2024-08-27
forum: General Help
---

### Post by infasyskey on 2024-08-27
Hello everyone!

Yes, you read the title right. I did a "sudo rm -rf /usr/bin" and now I am from a live kubuntu USB trying to recover somehow.
I know that the easy way is to do a reinstall, but let's try.


I tell you a little. After running the computer, I booted a pin from my BIOS and have been trying for two days to recover /usr/bin. 
I have followed two paths:
1 - I downloaded r-linux ([https://www.r-studio.com/es/free-linux-recovery/](https://www.r-studio.com/es/free-linux-recovery/)) a software to recover files. I have not recovered anything or I am not doing it right, can there be other alternatives?
2 - I followed this guide ([https://askubuntu.com/questions/906674/accidentally-removed-bin-how-do-i-restore-it](https://askubuntu.com/questions/906674/accidentally-removed-bin-how-do-i-restore-it)) , but when I chroot (chroot /mnt /bintmp/bash) I get this error:
/bintmp/bash: /lib/x86_64-linux-gnu/libc.so.6: version GLIBC_2.36' not found (required by /bintmp/bash)

I've had my head on a swivel for two days and I need a Jedi (I'm a little padawan in Linux).

First of all, thanks for everything!

Translated with DeepL.com (free version)

---

### Post by yancek on 2024-08-27
Do you have Kubuntu installed on the drive on which you deleted that directory?  If so, you could try booting from the Kubuntu USB, determining on which drive and partition the original /usr/bin existed then creating a mount point for that partition and mounting it from your Kubuntu USB and copying all the files from /usr/bin on the Kubuntu USB to the mount point you created.  I have no idea if this will work but given your current circumstances, there's not much to lose before reinstalling.  If you had software in that directory that was not in a default install it won't be there after the copy.

If you tried the method in the second link, you might try it again carefully copying/pasting the commands and making notes of exactly what happened.  Did you modify all the commands to use /usr/bin rather than /bin as used in that site?  Also, the script on that site is specifically to replace files in the /bin directory so you would need to modify that script  to make it work for /usr/bin.  I see  that thread is over 7 years old  which might be a problem .  Hard lesson to learn.  Good luck.

---

### Post by TheFu on 2024-08-28
Restore from the backups you made BEFORE deleting OS files.  That's the best option. 

2nd best option is to do a reinstall over the existing install.  There will be some installed packages that are missing files in /usr/bin/, so you'll need to force-reinstall each of those or the APT system will be corrupted too.

The safest option is to do a fresh install.

You've learned a valuable lesson. Hopefully, you won't do something similar again the rest of your life.

---

