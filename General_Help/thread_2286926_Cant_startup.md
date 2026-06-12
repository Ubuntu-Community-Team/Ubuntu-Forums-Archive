---
title: "Cant startup"
date: 2015-07-15
forum: General Help
---

### Post by levibachman on 2015-07-15
Hello, I think I've really done myself in this time... I've been having problems with my boot space partition, idk if this is related or not, also i was trying to instll 7zip from the ubuntu software center and it kept failing, so i tried restarting my computer to see if that would fix the problem, when i tried to boot back up i got this: 




 [http://i.stack.imgur.com/LPWKu.jpg](http://i.stack.imgur.com/LPWKu.jpg)


Help me please, and please keep instructions on how to fix as simple as possible

---

### Post by oldfred on 2015-07-15
How did you restart computer. You never should force power down.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Forced shutdown often then requires fsck to repair file system. Run e2fsck on every ext4 partition.
       
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
There are many threads on boot partition being full.
Post this from live installer:
sudo parted -l

click on every partition with Nautilus using live installer so mounted, and then run this:
df -h

---

