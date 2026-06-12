---
title: "GRUB slow, Ubuntu frozen at startup"
date: 2015-09-16
forum: General Help
---

### Post by rettiseert on 2015-09-16
Hello everyone!

Yesterday I downloaded and installed the latest stable Ubuntu for desktop alongside with Windows. In Ubuntu I installed Oracle Java, and configured GRUB to boot the Windows partition by default (i.e. I set **GRUB_DEFAULT=4** in **/etc/default/grub** and executed **sudo update-grub**).

The default entry in GRUB was changed fine, but now there is something wrong with it:
[LIST]
[*]The GRUB timer at the bottom of the screen is slow or something: instead of going 10, 9, 8, 7... it goes 10..., 8..., 6... 
[*]Keyboard is very slow: you press a key but GRUB doesn't get it. You have to press 2 or 3 times to get a response. 
[/LIST]

Once you manage to select Ubuntu, you get the Ubuntu initial screen with the logo at the center but it doesn't prompt for login, it just freezes and you have to do a hard reset to boot again.

Do you know what to do?

Thanks!

---

### Post by oldfred on 2015-09-17
What hardware?
CPU, video card/chip, RAM?

What version of Ubuntu?

Do not do hard reset, that often corrupts file system and then that does cause issues. You often have to run fsck to repair file system. Which may be what you now need?

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]http://kember.net/articles/reisub-the-gentle-linux-restart/

      [/URL]
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    [URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]
[/URL]

---

