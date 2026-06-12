---
title: "SH&gt;grub a fix?"
date: 2012-12-16
forum: General Help
---

### Post by Whippersnapper on 2012-12-16
I've been using Ubuntu 10.04 LTS for many months through WUBI loaded into win XP. Recently after I attempt to boot into Ubuntu, I receive the sh>grub prompt. I've attempted to load boot-repair through the terminal of a 10.04 CD, but am unable to get that the program to load. 

I was considering reloading the WUBI install of Win XP but it only gives me the opportunity to un-install Ubuntu 10.04. I'm also interested in a way to copy or backup any of the files off this partition ( I have 2 hard drive partitions,  Win XP is loaded on the C drive, the WUBI install is loaded onto D). Is there a way to fix this grub or a way to get my data off of the D drive then uninstall then reinstall 10.04?  BTW, I have a Dell Vostro 1500 laptop with 2 GB ram and 160GB in hard drive space.

Thanks for any help. Funny thing is I'm planning to install a new larger hard drive with win XP in one partition, Ubuntu 12.04 in another, with a third partition for data of both.

---

### Post by oldfred on 2012-12-16
I do not know wubi. 

NTFS file corruption or internal corruption in the wubi root.disk file can cause issues.

       Type this at "grub sh>" prompt:
set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sda1 loop=$path ro
initrd /initrd.img
boot
You might have to replace /dev/sda1 by /dev/sda2, or some other value. It has to be the partition containing Wubi. You can use
search -f $path

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

# also change to your partition, example uses sda1, but it must be your wubi install.
 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

     
    
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Whippersnapper on 2012-12-17
Hey thanks for the info. I ended up updating the c:wubildr file, and was able to reboot into Ubuntu...simpler than I thought! Consider SOLVED!

---

