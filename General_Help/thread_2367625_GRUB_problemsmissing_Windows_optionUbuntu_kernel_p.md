---
title: "GRUB problems/missing Windows option/Ubuntu kernel panic from restart during mounting"
date: 2017-08-01
forum: General Help
---

### Post by lazylinuxnoob on 2017-08-01
First off, I don't really know what I'm doing. Story goes like this: First in Windows, everything is fine. Want to switch to Ubuntu for a specific linux program. Restart to grub and attempt to boot into Ubuntu. Begins to load it seems until some sort of mount options appear and some directory is either not present or is being  slow. I skip a few things, not being aware of what I’m doing, and somehow now Ubuntu is mounting. Wait a bit, doesn't seem like anything is happening. Thinking everything has frozen, I restart my computer. Grub loads up with only ‘Ubuntu’ option(before there was ‘Ubuntu Advanced Options’, ‘memtest’, and ‘Windows 10’). I’m concerned but load Ubuntu. It immediately goes into a dead end error state.  I looked around on the forums but nothing was as specific as I am here. So I went to another computer, made a Ubuntu 17 live USB and loaded it up. Thats what I'm posting from now. Oddly, I can view the Windows partition on the primary drive, and the whole secondary drive, but not the first partition of Ubuntu on the first drive.

I need help getting it back to normal dual boot. Ultimately I'd like to upgrade from Ubuntu 14 to Ubuntu 17, switch secondary drive to primary, not lose anything in the process, and keep grub with dual boot options to Windows 10 and Ubuntu.

---

### Post by oldfred on 2017-08-01
First do not force reboot, unless absolute noting else works. Forced reboot often causes corruption and in Linux you need fsck or in Windows chkdsk.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power](https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power)
[URL="https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292"]https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292

[/URL]
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

[URL="https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292"]
[/URL]

---

### Post by lazylinuxnoob on 2017-08-01
I tried it all out. Nothing worked. REISUB doesn't work on a kernel panic but I'll use it next time I think Linux freezes. I tried fixing the errors, and it says they are but at the end it says 'e2fsck aborted'. The Live USB had a disk check when I loaded it up. I tried that, it said there were errors but I couldn't go further to fix them. Also a bunch of checksums were 0x0000.

---

### Post by oldfred on 2017-08-01
the e2fsck is only for Linux partitions, example was sdb1, but your sdb1 is NTFS. So only errors on sda1, your Linux partition may matter.
For NTFS repair you have to use a Windows repair flash drive and run chkdsk. You cannot run chkdsk from Linux.

Seems like too many errors.
What does Smart Status say about sda?
You can use Disks and in upper right corner icon is Smart Status. It also can run checks on drive, but all I know is if it says drive is good or not.

---

### Post by lazylinuxnoob on 2017-08-01
I'm only concerned with sda1, which is the main linux partition. So I switched from your example sdb1 to sda1. But yeah the post before did the e2fsck on sda1. I did Smart Status on the sda1 and benchmarked both drives. Results are shown, plus mount error message.

---

### Post by oldfred on 2017-08-01
With Smart Status all I know is if it says disk is ok, it probably is ok, but not guaranteed.

You can try a different superblock.
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1
One user could not get partition unmounted (may have needed swapoff), but used another live distro 

And this, but if this does not work then all you can do is reinstall and restore from your backups:

 Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)

---

