---
title: "Ubuntu 17.10 grub rescue unknown filesystem"
date: 2018-04-04
forum: General Help
---

### Post by gullprint on 2018-04-04
[ATTACH=CONFIG]279166[/ATTACH]

Hi, 
Ubuntu 17.10 crashed and all I have left is **grub rescue**.
Spent a few days reading all can find online. Was able to understand how to check from Grub 2. But as you can see from screenshot only "**filesystem is unknown**" found everywhere.
Created ISO USB but not able to install/fix from it.
Please direct me to the right place where can I find an answer. 
I need to save/restore my docs on this comp.
Thanks in advance.

---

### Post by yancek on 2018-04-04
Have you tried the commands suggested at the link below, scroll about half way down the page.  Your output only shows 2 partitions so try them both.  Was your Ubuntu the only system installed?  You may need to do a filesystem check from a Live CD/usb with Ubuntu or some other Linux on it.

[https://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash](https://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash)

---

### Post by oldfred on 2018-04-04
Did you have an abnormal shutdown, power failure or forced shutdown before something internal was done. 
That can corrupt file system, and then fsck is required.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by gullprint on 2018-04-04
Is there is a way you know how to sudo parted -l from **grub rescue?**

---

### Post by oldfred on 2018-04-04
Grub has only a very limited number of commands.
You can see partitions with the ls command, but listed as BIOS/grub type as partitions are not yet mounted by Ubuntu.
So you see hd0,1 or hd0,msdos1 type drive partitions.

You need the Ubuntu live installer to run repairs. Best is same version as some software changes.
I just tried running fsck on a partition I formatted with 18.04 and it does not work as version has been updated. I had to use my 18.04 install on one drive to run fsck on flash drive install.

---

### Post by gullprint on 2018-04-04
Yes I did before I posted on this forum. In my post on attached screenshot you can see it. Ubuntu 17.10 is only system installed. Filesystem check is what might needed - but not able to perform.

---

### Post by yancek on 2018-04-04
You should be able to run a filesystem check on your partitions from any Linux on a usb or DVD.  Are you saying you cannot boot a usb or DVD either?

---

### Post by gullprint on 2018-04-04
Yes, Created ISO USB but not able to install/fix from it.

---

### Post by oldfred on 2018-04-04
Can you boot USB?
You may have to use "cold" boot not "warm" reboot.
Or turn off all power, unplug, removed battery if laptop, hold power switch for 10 sec to drain all power.
Then see if you can boot and press correct key to get into UEFI/BIOS boot menu.

---

