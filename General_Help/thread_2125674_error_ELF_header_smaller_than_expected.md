---
title: "error: ELF header smaller than expected"
date: 2013-03-14
forum: General Help
---

### Post by DrScum on 2013-03-14
as described in thread 2125667 my system crashed. I had to hit the power button to turn it off. Upon rebooting I had a black screen not even access  to the bios was possible. After removing the battery (Dell Inspiron 1502 Laptop) I get the message error: ELF header smaller than expected...grub rescue>

What can I do?

---

### Post by oldfred on 2013-03-15
After forced power down file corruption is common.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Better to remember the elephants:


 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by DrScum on 2013-03-17
Thanks for the input oldfred.

I booted the system, was too slow to hit F2 in order to put the live DC in and got the grub rescue> promt, which was expected. Since I already knew that there is no way out from the grub rescue prompt than hitting the power button, I tried your Alt+SysRq R-E-I-S-U-B you're suggesting above. The system froze at the grub rescue promt and I again saw no other way out than the power button. When I reboot now the system doesn't even let me get to the setup. You can hear the drives clicking and the fan starting but the screen remains black. Ath this point I am a little desperate. Are there any key combinations to press during boot or something to get me back to a position to install a new system which I would be more than happy to do at this point.

---

### Post by oldfred on 2013-03-17
The Alt+SysRq R-E-I-S-U-B is when you are in Ubuntu and it locks up. If you force shutdown then you may corrupt file system and get grub rescue. I do not think it works from grub since that is not the operating system.

You may be able to manually boot from grub rescue.
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

