---
title: "Removing Extra Copies of Ubuntu"
date: 2007-08-27
forum: General Help
---

### Post by Rbro on 2007-08-27
Hey guys.

I have unnecessary, extra Ubuntu installations on my hard drive. I only need one of them. How can I remove the others and resize my wanted installation without messing up Grub. I need help ASAP. 

Thank you

---

### Post by SPr on 2007-08-27
Do you want to do what the user did in this thread: [www.dslreports.com/forum/r18944965-Wahhhhhhhh](www.dslreports.com/forum/r18944965-Wahhhhhhhh)

If so be very careful.

Or do you have several partitions each containing a different version of Ubuntu? If so just format them and remove the entries from /boot/grub/menu.lst. Then I assume gparted can resize the partitions.

---

### Post by Rbro on 2007-08-27
I made the same problem before. I removed the partitions, and grub error(could not mount selected partition, i think its number 17) popped up. Since I had no idea on how to restore the other partition, I installed a new copy of Ubuntu JUST so i could access the one I wanted. How do I get rid of the extra one without messing up grub, and getting that error?

---

### Post by Rbro on 2007-08-27
Also, they are not different version. They are all version 7.04.

---

### Post by Rbro on 2007-08-27
I'm guessing this is relatively hard to do...considering the 41 views.

---

### Post by Irony on 2007-08-27
The reason your not getting many answers is that you've provided little information, i.e. where do you have the installs and what do you want to get rid off and what do you want to keep.

Provide a;

[PHP]sudo fdisk -l [/PHP]

To redirect/install grub to the MBR (hda) and point it to a menu.lst in for example hda3 do;

[PHP]sudo grub[/PHP]

This opens up the grub program, with a prompt of grub>, now type;

[PHP]find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit[/PHP]

Here is a sample output;

[PHP]grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit[/PHP]

The reason for doing this is that if you eliminate a menu.lst that grub is pointing to you will get a grub error. Note though that this all depends on what you actually want to do.

---

### Post by jimbob on 2007-08-27
Open a root terminal and start grub.  At the grub prompt enter*[COLOR="Blue"] find /boot/grub/stage1[/COLOR]*

You will be presented with a list looking something like this:
  (hd0,0)
  (hd0,1)
  (hd0,3)


Decide which one of these you want to be your only choice, then enter (assuming it is the third entry):

  root (hd0,3)
  setup (hd0)
  quit

Now shutdown and reboot and the Ubuntu on partition #4, (hd0,3) since grub starts counting from zero, will be booted.  Now go in and save the /boot/grub/menu.lst file just in case and modify the original by deleting all the other entries and you should have what you want.

There will be some other partitions with Ubuntu on them but you can delete them using Gparted if you want.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Rbro on 2007-08-27
Sorry, jimbob. Didn't work. I had two options to pick from when i used grub. (hdo,2) and (hd0,6) I wanted the former, so I used your instructions as it applied to my situation. Unfortunately, I got a grub error 17 when I restarted, and am now using a livecd to talk through this forum. IN NEED OF HELP, I WOULD LIKE TO LOAD MY DESIRED PARTITION WITHOUT INSTALLING ANOTHER UBUNTU JUST SO I CAN ACCESS IT. 

Thank you... :)

---

### Post by jimbob on 2007-08-27
Sorry that didn't work out for you.  I guess we are going to have to see all of the output as shown in Irony's post above.  Do you have a stand alone  copy of the Gparted boot disk?  If not I would suggest you download and burn one. You can run grub from a terminal window from the Gparted disk.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Rbro on 2007-08-27
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         980     7871818+  82  Linux swap / Solaris
/dev/sda3             981       21511   164915257+  83  Linux ---------------------------------------------------------------<This is the ubuntu I want to keep.
/dev/sda4           21512       24321    22571325    5  Extended
/dev/sda5           24199       24321      987966   82  Linux swap / Solaris
/dev/sda6           21512       24198    21583264+  83  Linux


That's my hard drive's current state. I don't have a Gparted CD, and can't make one right now. However, I have a Linux System Rescue CD and the Ubuntu Live CD, I thought you could run grub on both of those, they both have terminals...

---

### Post by Rbro on 2007-08-27
Do I need to provide any more information?

---

### Post by Rbro on 2007-08-28
Um...guys? Figured it out myself. ^_^ If anyone cares, I used the Ubuntu Live CD, and edited Grub's list file. The root was set to (hd0,0). I had to change it to (hd0,2). That's it. Ok, problem solved.

---

