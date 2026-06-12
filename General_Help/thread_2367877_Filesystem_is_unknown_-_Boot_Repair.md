---
title: "Filesystem is unknown - Boot Repair"
date: 2017-08-04
forum: General Help
---

### Post by n2222 on 2017-08-04
Hello, 
I have this message:

error: unknown filesystem.
Entering rescue mode...
grub rescue>

After running Boot Repair CD, I got this answer on the link: [http://paste.ubuntu.com/25232025/](http://paste.ubuntu.com/25232025/)

So what I have to do now?

---

### Post by yancek on 2017-08-04
Your boot repair output shows one 500GB drive with a root filesystem partition and a swap partition.  If this is not a new install, something seriously bad happened.  If it is a new install, then it obviously did not complete successfully because the boot files one would normally see are not shown.  So is this a new install and if so, which version number release is it?  I saw a reference to 'saucy' in boot repair and that has been unsupported for years (Ubuntu 13.10).  If not a new install, what changes were made just prior to this problem?

---

### Post by oldfred on 2017-08-04
Did you have an abnormal shutdown or power failure. Or force shutdown. That often corrupts file system and then it cannot be seen.
Be sure to use a current version of Ubuntu live installer.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1 

If not then you need to check if hard drive is still good. In Disks you an click on icon in upper right corner and see what Smart Status says about drive. All I know if good or bad, but it can also run many tests.

---

### Post by n2222 on 2017-08-04
I installed Ubuntu in 2011 and accepted every new version suggested. That time I didn't have any new installation, my notebook hanged up sometimes for a couple of weeks. that day I tried to proceed an audio file (about 150 MB), it hung up, I pressed Ctrl+Alt+Del (as I do in Windows); my notebook restarted with the following message:

error: unknown filesystem.
Entering rescue mode...
grub rescue>

---

### Post by oldfred on 2017-08-04
Correct way to shutdown with Linux, if you cannot get to terminal and kill run away task.

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
[h]("https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292")

---

### Post by n2222 on 2017-08-11
I tried sudo e2fsck -C0 -p -f -v /dev/sda1, I got "... superblock is corrupt..."
on sudo e2fsck -f -y -v /dev/sda1  - "no such file or directory ..... Possibly non-existing device?
What I can do now?

---

### Post by oldfred on 2017-08-11
Have you checked if drive is still good?
In Disks you can use icon in upper right corner and Smart Data. It can run lots of tests, but all I know is good or bad drive.

You can try alternative superblock(s)

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1

---

### Post by n2222 on 2017-08-12
Thank you, I did it again more carefully, and now the system is repaired and I use my notebook again.

---

### Post by oldfred on 2017-08-12
Glad you got it working.
You can change to Solved.

And best to have good backups.

---

### Post by n2222 on 2017-08-20
But how can I change to Solved? I couldn't find such option

---

### Post by wildmanne39 on 2017-08-20
You use thread tools at the top of the page to mark the thread solved.

---

