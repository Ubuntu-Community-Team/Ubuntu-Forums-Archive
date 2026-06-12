---
title: "fsck problem"
date: 2007-03-15
forum: General Help
---

### Post by Tteddo on 2007-03-15
Hello! I have a strange problem mounting an share on a Win2000 computer during boot from fstab. It appears to want to run fsck on the volume and just hangs there. I have the last item in the line in fstab set to 0 so it should not try to check, but it still does. I noticed that fstab was using spaces instead of tabs (like I use in Fedora on another machine)  so i changed the appropriate line to spaces, but no go. Here is the line I have:
//Warpdrive/wwwroot /var/wwwroot smbfs credentials=/home/tteddo/.smbpassword,gid=1001 0       0
of course it is all on one line....
The line works with mount -a so I knopw that's not it.
any ideas?

---

### Post by Tteddo on 2007-03-26
To add a little more information, and bump me up, if I comment out the Warpdrive line it always boots normally, so it is definitaly that line that is causing the problem. Like I said, it works fine with mount -a.

---

### Post by Tteddo on 2007-04-04
:Bump!
More info...
I added a line to mount the mp3 folder on my eMac to /var/mp3 and it behaves exactly the same way.
Later. I went into the grub menu and made the startup visible and it stops at:
Waiting for /var/wwwroot
and just sits there forever.

Again, sudo mount -a works perfectly after I am already booted.

Anyone have any ideas?

---

