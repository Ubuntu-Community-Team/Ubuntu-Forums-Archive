---
title: "Ubuntu8.04 Hibernate Help"
date: 2008-06-12
forum: General Help
---

### Post by wxf@bao.ac.cn on 2008-06-12
at first,it told me "swap is not enough for hibernate"
then I change swap from500MB to 7GB.
so hibernate can power off my PC
but after startup,
it stop at some step----
"the orange bar bump to left and right, then stop on the right"

I am really frustrated and tied. I have already spent more than 12 hours (around the clock) for "hibernate".
it is very important to me.it is very important to me (I write program to process data and image. Every day, I would like to continue my work before). I don't want to give up.
Who can help me, please. 

[email]wxf@bao.ac.cn[/email]

I have already tried all the following commands and setting: 
+++++++++++++++++++++++++++
1.swapoff swap
2.parted-> resize
fdisk or parted(rm swap)
3.mkfs -t ext3 
4.mkswap -c 
5.swapon 
6.cat /proc/swaps
# blkid 
swap UUID“&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;”
/etc/fstab: 
UUID=&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;
/etc/initramfs-tools/conf.d/resume:
RESUME=UUID=&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;&#65311;
update-initramfs -u

root@freedom:/home/wxf# free -m
             total       used       free     shared    buffers     cached
Mem:          3041        621       2419          0         22        352
-/+ buffers/cache:        246       2794
Swap:         6981          0       6981
root@freedom:/home/wxf# vol_id /dev/sda7
ID_FS_UUID=1692ad8d-6762-4d30-a445-09c3804d84bb
ID_FS_UUID_ENC=1692ad8d-6762-4d30-a445-09c3804d84bb

root@freedom:/home/wxf# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00088374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        9605    67151700    5  Extended
/dev/sda5            1246        3735    20000893+  83  Linux
/dev/sda6            3736        8715    40001818+  83  Linux
/dev/sda7            8716        9605     7148893+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ac30ac2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/sdb2            1531        8669    57344017+   f  W95 Ext'd (LBA)
/dev/sdb5            1531        4080    20482843+   7  HPFS/NTFS
/dev/sdb6            4081        7267    25599546   83  Linux
/dev/sdb7            7268        7331      514048+  82  Linux swap / Solaris
/dev/sdb8            7332        8669    10747453+  83  Linux

+++++++++++++++++++++++++++++++
Ubuntu 8.04 DVD.iso installed
My hardware:
PC Brand: Dell Optiplex GX280
intel P4 3.0GHz 32 bit cpu
interl 915 express chipset LgA775
Video card Nvidia Geforce 8600GT 512 DDR2
RAM 2G+1G=3G
so I set swap 3G*2RAM=~7G
sda 160GB
id3 80GB
DVD ROM rw
++++++++++++++++++++++++++++++++++++++++++

---

### Post by Pjotr123 on 2008-06-12
Bug:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 4 )

---

### Post by wxf@bao.ac.cn on 2008-06-12
Thank you. But I cant open the link.
maybe that's a out of date link.
Or, those web pages contain some news which make our(China) Government unhappy. They "blocked my eyes".
Could you paste them or mail to me. [email]wxf@bao.ac.cn[/email]

---

### Post by Pjotr123 on 2008-06-12
Probably a block. Here 's the entire page:

---

No operating system is flawless. Ubuntu is no exception. Here you'll find solutions for seven bugs in Ubuntu 8.04 (or in the applications that are part of a default installation of Ubuntu).

 

Content:

1. Firefox 3 eats occasionally during a few minutes, 100 % of the processor power and causes intense activity on the hard disk. (now largely resolved through the updates, but not entirely)

2. The screen resolution is not right, since I installed the restricted proprietary driver for my ATI or NVIDIA graphics card.

3. Booting takes a long time: in the beginning, the orange progress bar goes back and forth for a long time. Or the screen remains entirely dark during booting.

4. Hibernate and suspend don't work well: they make my computer malfunction or even enter a coma.

5. File manager (Nautilus) gets stuck after processing many music files.

6. Login Window change doesn't work: System - Administration - Login Window seemingly doesn't respond.

7. Laptop with Intel 945 graphics card: (945GM): can't install (no graphical screen), or the text size in the login window is immense.



1. Firefox 3 eats occasionally during a few minutes, 100 % of the processor power and causes intense activity on the hard disk. (now largely resolved through the updates, but not entirely)

This SQLite problem has been largely remedied through the updates (new xulrunner). But not entirely (yet). 

Furthermore, the underlying feature in Firefox 3, namely the recognition of attack sites and phishing sites, remains a "heavy" feature. Especially problematic for older and slower computers. Also on brand new computers this may occasionally be annoying or become so after Firefox has been used for some time. 

If your computer suffers from this (it probably does), then you can follow these steps to work around it. Temporarily, until Ubuntu provides a fix through the updates.

A. Open Firefox 3 and disable the identification of suspect websites:
Edit - Preferences - Security
Remove these ticks:

- Tell me if the site I'm visiting is a suspected attack site

- Tell me if the site I'm visiting is a suspected forgery

B. Close Firefox 3. If you haven't visited any web pages yet with Firefox 3, then this is enough and you are ready (repeat these steps in every user account). If not, then you will want to remove a large swollen unnecessary file. For this, do the following.

C. Places - Home Folder

Toolbar: View - tick: Show Hidden files

D. Go to:
/home/user_name/.mozilla/firefox/v5173hgzm.default/

(the name of the last folder is just an example, in any case the name ends on .default)

and remove the file urlclassifier3.sqlite and (if present) urlclassifier3.sqlite-journal

E. Open Firefox 3. The problem is now over in this user account. A new urlclassifier3.sqlite file is being created, but the size is limited to 9216 bytes (9 KB).

F. Repeat these steps in each user account.
 


2. The screen resolution is not right, since I installed the restricted proprietary driver for my ATI or NVIDIA graphics card.

A. Try to set the right screen resolution like this:

Applications - Accessories - Terminal

Type (or copy/paste): 

gksudo displayconfig-gtk

Press Enter. Now a configuration tool for your screen(s) appears.


B. Step A doesn't help enough and you have an Nvidia graphics card?

Note: The following applies only to Nvidia graphics cards running on the restricted driver.

System - Administration - Synaptic Package Manager

Search word:  

nvidia-settings

tick it and press Apply button

Then:

Applications - Accessories - Terminal

type:  

gksudo nvidia-settings

press Enter

Now you can configure your screens properly, with this handy tool from Nvidia.


3. Booting takes a long time: in the beginning, the orange progress bar goes back and forth for a long time. Or the screen remains entirely dark during booting.

That's an annoying phenomenon, which may have a number of causes.

I. In the first place, this might help:

A. Applications - Accessories - Terminal

type (or copy/paste): 

gksudo gedit /boot/grub/menu.lst

press Enter

B. Now search in the text file for the paragraph with the following content:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash 

Change the last line of this paragraph as follows: 

# defoptions=quiet splash clocksource=hpet

Save and close the text file.

C. Now type in the terminal:  

sudo update-grub

Press Enter. Please note that your password will remain invisible, not even asterisks, which is normal.

D. Reboot your computer.

 

II. In the second place it may be so, that the resolution of your screen is wrongly described in the file usplash.conf.

Please note: applying this solution only makes sense if the resolution in usplash.conf is wrong. Is it right or is there no resolution at all in there, don't apply the solution.

This is how you do it:

A. Applications - Accessories - Terminal

Type:

sudo gedit /etc/usplash.conf

press Enter

Your password will remain invisible, that's normal (not even asterisks)
 

B. Change the values of the xres and yres as follows:
xres=1024
yres=768 

Save and close the text file.
 

C. Then type in the terminal: 

sudo update-initramfs -u

press Enter

Note: This is a drastic operation, for the completion of which your computer needs some time and a lot of effort. Please wait patiently until it's completely finished and DO NOT close the terminal prematurely! Otherwise your entire system will be spoiled an you'll have to reinstall Ubuntu.

D. Reboot your computer.


4. Hibernate and suspend don't work well: they make my computer malfunction or even enter a coma.

This still happens with some hardware, and unfortunately .... there is no solution yet. Therefore it's better to turn off these two modes, if they don't work on your computer:

Applications - Accessories - Terminal

type:  

gconf-editor

go to: apps - gnome power manager - general and remove the ticks at: can_hibernate and can_suspend

Note: this is a user preference: repeat this in each user account. 

 

5. File manager (Nautilus) gets stuck after processing many music files

This bug may be repaired in version 8.04. But to be on the safe side, you may want to switch off the fairly useless feature that causes it.

For this, disable the sound preview in the file manager (Nautilus). As follows:

Places - Home Folder

Nautilus toolbar: Edit - Preferences - Preview

Sound Files: Preview sound files: Never


6. Login Window change doesn't work: System - Administration - Login Window seemingly doesn't respond.

A flaw in gdmsetup (System - Administration - Login Window): the first time you want to change the login window, this sends the processor to 100 % and it takes a long time before the login window changer appears. The change screen will appear eventually, but it takes very long. Just wait.

This happens only the first time. The next time you want to change the login window, the change screen will appear quickly, as it should.


7. Laptop with Intel 945 graphics card: (945GM): can't install (no graphic screen), or the text in the login window is immense.

There is an error in xorg (git, to be precise), making the standard Intel driver xserver-xorg-video-intel not work properly with the Intel 945 chipset. This Intel 945GM is in many laptops. Installing Ubuntu with the normal Desktop CD is usually impossible on these laptops. 

Upstream developers from Intel have released a fix, but it's not in Ubuntu yet. Hopefully it will be in 8.04.1 (which is 8.04 with an integrated Service Pack 1, to be released on July 10).

What you can try in the meantime is installing Ubuntu with the use of the Alternate Desktop CD (which does not feature a LiveCD function). You can download it here.

You have to tick a box for this, right under the green lettered "Start Download".

Then take the following steps.

A. Immediately after the installation you do not just boot normally, but you boot in the Recovery Mode (second option in the Grub menu). If necessary, make the Grub menu visible by pressing the Esc key several times when the BIOS screen appears.

B. You end up with a limited screen which gives you a few options to choose from. Choose the terminal window.

C. Remove the intel driver as follows.

Type: 

apt-get remove xserver-xorg-video-intel

press Enter.

This will cause Ubuntu to fall back automatically on the other Intel driver that's installed by default: xserver-xorg-video-i810. The i810 does not suffer from the git bug.

D. Type: 

reboot

press Enter.

E. Now reboot normally. The problem should be over.

---

