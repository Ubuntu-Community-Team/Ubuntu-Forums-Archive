---
title: "Boot Error"
date: 2015-02-25
forum: General Help
---

### Post by mistcloud-misty on 2015-02-25
This morning I ran some updates which included a Kernel change when my computer crashed and required a forced shutdown. Following that, when I turned my computer back on, it brought me immediately to the Grub 2 menu after a bunch of location errors. 

I tried to boot it using these instructions on this site: [http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/) , with no success have found my Ubuntu drive using the ls command, successfully grabbed a kernel and a initrd image, but following the 'boot' command, I get a kernel panic which requires an hard shutdown again.

I tried using the root /dev/sda command that is supposed to prevent the panic, but I have GUID partition, meaning the location for linux is hd0,gpt7 as opposed to the normal hd0,7. 

Currently, if I hold exit while booting my computer I can choose between loading the Ubuntu boot manager (grub) and the Windows boot manager because I am dual-booting. I can easily get into Windows so I am at least able to try and get help. I do not currently have access to a live CD or zip drive, and, at the same time had not made any backups (oops!). 

Just hoping for a few tips I could use for booting Ubuntu on GRUB so I can at least fix the problem there, if possible. Unfortunately my laptop does not have a built in disc drive, so can't use any discs! 

Also, I had to turn off Secure Boot in order to use the commands in GRUB - is that something to worry about? Thank you for any help! It's been awhile since I managed to screw up my computer so badly.

---

### Post by oldfred on 2015-02-25
How are you shutting down. If just turning power off or control alt del you may corrupt partition and add to the issues. Then you need to run fsck first before you can start resolving other issues.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Are you booting with UEFI or BIOS? If drive is gpt, and booting Windows I assume UEFI.

---

