---
title: "Please some one Help Me Very Urgent.."
date: 2007-12-04
forum: General Help
---

### Post by KodigoLatino on 2007-12-04
Ok i installed ubuntu and everything was working fine and then i turned my computer of and then turned it back on i didnt realize the live cd was in . then the ubuntu live came up and i acidently installed it again ..so that created 2 ubuntu's logins thing on the boot so now i barly have any space ..i realy need help on how to unistall the second ubuntu i installed please someone. :confused:

---

### Post by chronographer on 2007-12-04
Do you have any other operating systems on there too? If not, you can just delete the partition of the second Ubuntu install, it would be easy to do this from the Ubuntu live CD.

Just boot up the live CD, ensure you know which partition the second install is on, then use the program GParted to delete the partition on which the second Ubuntu is on and make the partition the first Ubuntu is on bigger, to fill the space.

Once this has been done, restart the computer without the live cd ! then type this in a terminal "sudo cp /boot/grub/menu.lst" (to backup your old boot menu list) then
"sudo gedit /boot/grub/menu.lst" and remove the entry which refer to the second install.

If this sounds too hard, just boot form live CD and delete all partitions and reinstall!

Good Luck. 

Alex

---

### Post by KodigoLatino on 2007-12-04
Thank you Very much i apreiciate your answer u saved me from buying a new computer i thoght i had no hope..

one last question 
i got the ubuntu live cd on but i dont know were to find the program Gparted
do u know were to find it?

---

### Post by sethvath on 2007-12-04
Top left corner of your screen, System>Adminstration>Partition maker (or something of that sort)

---

### Post by ubukool on 2007-12-04
you need to use synaptic to install gparted.  If you go into system--->administration---->synaptic and search for gparted there.

*EDIT - I've just seen Sethvath's reply, maybe for the Live CD you can access it as he says, but if you are using your installed version of ubuntu you will need to install it with synaptic*

---

### Post by KodigoLatino on 2007-12-04
Ok i got Gparted on how do i delete ubuntu ? i got 2 ubuntus and it takes so much space or how do i delete the both of them?

---

### Post by chronographer on 2007-12-04
Do you have windows on there too? If you do then its a different matter.

---

### Post by KodigoLatino on 2007-12-04
nope i dont have windows =\
im running the GParted from ubuntu live cd but i dont know how to use it

---

### Post by kevinatkins on 2007-12-04
Hi,

It might be easier to just blow the whole lot away and install again from scratch using the Live CD. When you do this, at the partitioning stage, *make sure* that you select 'Use Entire Disk' - this will cause the installer to delete any existing partitions and format the entire disk, ready for reinstallation.

You could use a partition editor to delete one installation, but then you're also going to need to resize the other installation's partition, edit grub, etc, etc... You might find it a bit involved...

---

### Post by KodigoLatino on 2007-12-04
and i want to delete the 2 ubuntus i have so i can free up my space and then after i can reinstall it again when i have more space
do u know how to use Gparted?

---

### Post by chronographer on 2007-12-04
It is easy to get rid of Ubuntu. IF you want to use onlly 1 Ubuntu then refer to my first post, if you want none (and want windows only) then use gparted from your LIVE CD by going System - Administration - Partition Editor, delete all partitions EXCEPT the one which is formatted with NTFS and resize the NTFS partition to fill your hard drive.

OR to keep one Ubuntu, like I said earlier, note which partition the one you DONT want is on and use gparted from the LIVE CD to remove that partition and resize the remaining UBUNTU partition to fill the empty space.

If you want windows only, you will need to fix your MBR (or your master boot record) by inserting a windows CD and rebooting, then using repair an existing install or something like that.

---

### Post by KodigoLatino on 2007-12-04
ooo ok so i just need 2 put the ubuntu live cd and reinstall it and use all the space so the other ubuntus will delete and i will have only one?
but if i do dat wouldnt it make the computer slow ?

---

### Post by chronographer on 2007-12-04
Nope.  If you are in the ubuntu Live  CD now, start gparted by going "alt F2" and typing in the little box "gparted" then right click on all partitions and select "delete partition" you may have to right click and select "Unmount" first (using gparted still)

Once you have deleted all partitions, then click "apply"

Now install Ubuntu again using the icon on the desktop!

---

### Post by tlaloczint on 2007-12-04
sorry but it will not make you computer slow, just boot from cd and when you get in the step of partitioning you HHD just choose the one that says use the whole drive or something like that.

that way is going to erase both partitions and do a clean reinstall so you wont have to worry about having to many ubuntus in one pc.

---

### Post by sethvath on 2007-12-04
> **KodigoLatino said:**
> and i want to delete the 2 ubuntus i have so i can free up my space and then after i can reinstall it again when i have more space
do u know how to use Gparted?
Make sure you read up before doing anything to your partitions. First and foremost backup your important data. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by tlaloczint on 2007-12-04
> **sethvath said:**
> Make sure you read up before doing anything to your partitions. First and foremost backup your important data. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

in the first post he say that just installed twice ubuntu so he will be ok to do a clean reistal

---

### Post by sethvath on 2007-12-04
And fellas, I reckon KodigoLatino needs some hand holding so send him to the specific community docs where there's step by step guide with screenshots rather than explaining what to do in a wordy block of text. I myself am confused reading all the replies. 

KodigoLatino, please be specific with your system details so the rest of us here can help you to the best of our abilities. If there's nothing to lose on your system, go ahead and reinstall ubuntu by overwriting everything as suggested by tlaloczint.

---

### Post by KodigoLatino on 2007-12-04
yea i backedup my important data in a disk 
im about to do the instalation again and use the partition

---

### Post by KodigoLatino on 2007-12-04
the hole partition ***

---

### Post by markcaetano@gmail.com on 2007-12-04
open up GParted ...system>administration>partitioner or similar

now select those two partitions, right click then deactivate.

not sure if it'll work

worth a try

good luck



p.s - i'm in the same mess at the moment ;-)

---

### Post by KodigoLatino on 2007-12-04
I apriciate every ones respong thank you every one

:KS

---

### Post by erginemr on 2007-12-04
Hello,

You may also want to read the following graphical tutorials for GParted beforehand:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) (also suggested by sethvath before)

---

### Post by bigken on 2007-12-04
this what I would do boot from the live cd at the partition section select custom/manual delete all the partitions and create new ones a good example of this would be 

/ (system) 10 gig

swap twice your ram ie 512mb = 1gig

/home (whats left)

so if you ever need to reinstall ubuntu all you do is delete / (system) and home stays the same all your files ect stay safe

if you have 2 gig of ram no need for a swap partition :)

---

### Post by kevinatkins on 2007-12-04
Hi again,

You've backed up your data - good! I still think you're better off just reinstalling from scratch using the live CD - don't bother mucking about with GParted... just let the installer do its thing and make certain that at the partitioning stage, you elect to use the whole disk!

Your system won't run slower or anything like that - it will be a virgin installation. If all goes well, you should have a working desktop again within one hour - quick and easy.

---

