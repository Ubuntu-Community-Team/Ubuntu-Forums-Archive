---
title: "Stuck at grub rescue! Help!"
date: 2013-07-09
forum: General Help
---

### Post by tooplanx on 2013-07-09
Hi,

I've got XP and Ubuntu dual booting and they've been working fine. However, today as it was booting up, as I skipped down through the boot options to boot XP at the bottom of GRUB, I must have accidentally knocked 'enter' on the XP recovery mode. It loaded up and I exited it as soon as I could. However, now when I boot all I get is "error: no such partition." and then "grub rescue>" prompt.

I've looked around on loads of forums and can't see a solution that applies to me. I need to restore GRUB but there doesn't seem to be an easy way of doing this. I can't believe that so much damage can be done from a slight slip of the finger!

I don't have any Windows recovery media to boot in to windows with. How can I recover the grub boot menu.

Also is there any way to hide the recovery partitions in GRUB so that in the future this can't happen again?

Thanks in advance.

---

### Post by tooplanx on 2013-07-09
bump

---

### Post by tooplanx on 2013-07-10
bump

---

### Post by oldfred on 2013-07-10
It seems that one of the first things recovery mode does is rewrite partition table. And of course it does not recognize new Linux partitions.

You may be able to recover old partition table with testdisk from Ubuntu live installer or just about any Linux repairCD. Testdisk is in the Ubuntu repository.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You can manually modify grub menu, turn off os-prober and add your own entries. I like to do that and just have the one's I use the most, but have copies of others on bootable flash drives or saved so I can either boot or manually enter a boot stanza from grub command line. 
Some have and like grub customizer, but I have not used it.

      
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

 # In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
# or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

      
 # Copy the  entries you want or edit menuentry only at will from this:
gedit /boot/grub/grub.cfg
# Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
# Then do:
sudo update-grub

---

### Post by tooplanx on 2013-07-10
Thanks loads for the help! 

I'll give this a go when I've got a bit of time later in the week.

Fortunately, I managed to regain access to Win XP by using 'boot-repair-disk' ([http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)), and so I can at least use my computer now. 

The linux partition seems to have disappeared though. Through XP I looked at all of the partitions using DiskInternals Linux Reader ([http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)) and, although it shows the Linux swap partition, the area that I had Ubuntu installed on shows with a '?' mark and says unallocated space... I don't know whether this means that the whole linux install has been wiped in a matter of seconds, or whether it's just not reading properly.

I'll have a look with the things you've set out about, and hope for the best! Looks like it could be a lost cause. It's a good job that I didn't have any important files saved on the linux partition. Just hours wasted setting up the OS so that it works fully etc. :(

---

### Post by oldfred on 2013-07-10
Best to use Windows tools for Windows and Linux tools for Linux. 

Testdisk should be able to add the missing space back as your Linux partition. Many fully recover a working system but no guarantees.

---

