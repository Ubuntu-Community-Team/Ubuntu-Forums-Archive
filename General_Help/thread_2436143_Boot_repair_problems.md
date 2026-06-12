---
title: "Boot repair problems"
date: 2020-01-31
forum: General Help
---

### Post by Gnigma on 2020-01-31
I tried to remove WINE to reinstall a later version, and somehow managed to blow away my boot routine. At first it would pull up Grub (Grub2) and would just go to a blinking cursor when I selected Ubuntu. I ran Boot Repair. (It also boots into Windows 10 occasionally, and, at first it would boot into Windows, but now it doesn't even start Grub2.) I ran boot repair again, and now it says "No operating system." When I run the Boot Repair disk, it tells me to load a repository containing Grub 2 for Bionic. My system started as a 15, I think, but has been upgraded until it's now a 18.04. My problem is the Boot Repair disk directs me to a list of URLs for Bionic. When I use add-apt-repository, it tells me that I can only add one repository. I'm only trying to load one! I can't find the GUI package manager, which is what the program recommends, so I've been trying to add the repository from a terminal.

---

### Post by yancek on 2020-01-31
Boot repair has an option to Create BootInfo Summary which is what you should have done and posted that link here.  Hard to know what has been done by your repair attempts.  There are a number of people here who are very knowledgable about boot repair and Grub so I would suggest you do that.  Best is to go to the boot repair site and use the 2nd option to use the ppa before running boot repair if you have not done that.  You might also post the contents of your /etc/apt/sources.list.  No need to include the lines which are commented out (beginning with a hash mark #).

---

### Post by oldfred on 2020-01-31
Boot-Repair can only run from a gui.
You can use terminal commands to install it, but it needs a gui.

Part of Boot-Repair's report is bootinfoscript. You can run it from a terminal and manually post to a pastebin site.
Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by Gnigma on 2020-02-01
The url for the boot info is: [http://paste.ubuntu.com/p/tB79zJQgQq](http://paste.ubuntu.com/p/tB79zJQgQq)  I was getting a notice a few days before that said the package system was broken, and asking if I wanted to report it. I did, acouple of times, in fact, but that was all it said. Updates wouldn't run, though, and it kept telling me to check my internet connection.

---

### Post by oldfred on 2020-02-01
Grub does not use boot flag, Windows has to have boot flag on the primary NTFS partition with its boot files. Many Windows BIOS installs use a separate small boot partition, but boot files can be in the main  install. 
You can use gparted and move boot flag from sda4 to sda2. Then Windows should boot or you have to make Windows repairs.

Make sure Windows works as grub only boots working Windows.
Then you can use Boot-Repair to reinstall grub to MBR to boot Ubuntu.

You may also need to repair your ext4 partition(s).
o see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb2

---

### Post by Gnigma on 2020-02-03
I bit the bullet and reinstalled the kernel and basic system, then restored the /home folder from backup. It fixed the problem. Now the PITA is putting it all back like it was...

---

