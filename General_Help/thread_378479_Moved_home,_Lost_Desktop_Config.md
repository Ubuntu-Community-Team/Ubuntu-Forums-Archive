---
title: "Moved /home, Lost Desktop Config"
date: 2007-03-07
forum: General Help
---

### Post by Darko Beta on 2007-03-07
I followed the psychocats guide to moving my /home to it's own partition.  When I was done, all of the files and everything were transferred fine, but my desktop had lost all of the theme configurations I had changed, and firefox was wiped clean (I mean all settings, extensions, bookmarks, etc., the actual app is still there).  I have tried all my programs and everything works perfectly, and all of my files are where I expected them to be.  Additionally, my Ubuntu is much faster.  I can't remember if this is how snappy it was when I first installed it, but it is a very noticeable difference from before I moved /home.  So rather than try to reverse the process and start over, I chose to re-do my desktop and firefox and stick with it.

Anyone know why this would happen?  One thing I noted: when I created the /home partition, on the psychocats guide it was labeled as a logical partition.  When I created the partition in gparted, the "logical" choice was grayed out, so I made an ext3 "primary" partition.

Also, I am very happy with the speed increase.  My system is very snappy now, and I love it.  Is there a way to repeat whatever made this happen in the future if things are getting boggy?  Now that I have a separate /home partition, would re-installing Ubuntu help make things snappier (not necessarily right now, but down the road a bit)?

---

### Post by bapoumba on 2007-03-07
I'm not sure I can explain what happened. Anyway, with a separate /home partition, if you happen to install a new release for example, remember to tell where is your /home but do not format it. You'll keep all your files and settings. Back up your /home, in any case.

---

### Post by Irony on 2007-03-07
This is the method I use to move home;

[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[PHP]sudo mkfs.ext3 /dev/hda13
sudo mkdir /mnt/hda13_Edhome
sudo mount /dev/hda13 /mnt/hda13_Edhome
sudo init 1 (wait, wait... until prompt root@ubuntu:~#)
cd /home
cp -ax * /mnt/hda13_Edhome
cd /
mv /home /home_backup
mkdir /home
mount /dev/hda13 /home
exit  (or Ctrl D)[/PHP]

Now I'm back in graphical mode;

[PHP]gksudo gedit /etc/fstab[/PHP]

Add;

[PHP]/dev/hda13   /home   ext3   defaults   1   2[/PHP]

Basically I boot up into Ubuntu as normal then format the partition I am going to move home to (hda13).

I then make a directory in /mnt and mount hda13 to it.

Then I go to single user mode (text only screen) which means that I can then copy home in its entirety to the new partition.

I then change directory to home, copy the contents of home to the new partition, make a backup copy of the current home then create a new home folder.

I then mount the new home in partition hda13 and then edit fstab.

Once I'm satisfied that the new home is working okay I then delete the backup copy (not shown).

---

