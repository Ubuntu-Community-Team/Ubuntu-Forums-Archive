---
title: "How Do you Dual Boot?"
date: 2007-11-26
forum: General Help
---

### Post by Xero117 on 2007-11-26
How do you dual boot like have Windows and Linux on the computer?

Cause I want to keep Windows XP on here and have Linux on here too

---

### Post by FuturePilot on 2007-11-26
You might want to have a look here
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
Very good info on how to do this.

---

### Post by qqzhenyi on 2007-11-26
Step 1: Install Windows
Step 2: Install Ubuntu
Step 3: Done!

Okay... maybe you should read this:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Xero117 on 2007-11-26
> **FuturePilot said:**
> You might want to have a look here
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
Very good info on how to do this.

dude this site is a good source thanks man!

---

### Post by dabl on 2007-11-26
1. Install *buntu.
2. Download and install VMWare Player on your *buntu system.
3. (the hard part) acquire a suitable virtual machine for Windows XP.
4. Install Win XP on the virtual machine.
5. Install whatever that indispensable Windows app is that you can't replace in Linux.

:guitar:

---

### Post by Xero117 on 2007-11-26
> **dabl said:**
> 1. Install *buntu.
2. Download and install VMWare Player on your *buntu system.
3. (the hard part) acquire a suitable virtual machine for Windows XP.
4. Install Win XP on the virtual machine.
5. Install whatever that indispensable Windows app is that you can't replace in Linux.

:guitar:

ok thanks but kinda confusing for me cause I'm new to this Linux stuff

---

### Post by nacho32 on 2007-11-26
yeah I like the first better install xp  then linux  for a true dual boot. I run a tripple boot on 2 HD's and I like it
 
install xp then vista then linux
fun when your board lol:popcorn:


must have tools G-parted and grub super boot loader CD's

---

### Post by -grubby on 2007-11-26
> **dabl said:**
> 1. Install *buntu.
2. Download and install VMWare Player on your *buntu system.
3. (the hard part) acquire a suitable virtual machine for Windows XP.
4. Install Win XP on the virtual machine.
5. Install whatever that indispensable Windows app is that you can't replace in Linux.

:guitar:

that's to set up a virtual machine (OS within OS) IF you really want a dual-boot then follow FuturePilots advice

---

### Post by erfahren on 2007-11-26
hermanzone has tons of information and resources as well: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

(gettin alot of these lately, Google must be down - lol )

---

### Post by teryowen on 2007-11-26
Install Windows,
Install Ubuntu,
and your done

---

### Post by Afkpuz on 2007-11-26
Here's one of the easiest ways I've found to dual boot.  First and formost, you'll need to install windows first.  It likes to sit on the first half of your hard drive and gets cranky when it's not.  So, install windows first.  In the windows install, partition your hard drive and leave at least 30 gb unpartitioned.  This is done at the step when windows asks you where to install.  Partitioning sizes will change depending on what you want to use windows and linux for.  Like if you only want to do internet and email in linux, you don't need very much space at all.  Ideally, just cut your hard drive in half and put windows on the first part.

Then, once windows is done, load up that ubuntu CD.  I've only used the alternate install disc, so please note that this will be different if you're using the live cd.  The alternate install disc is a text based installer that doesn't make you wait forever to live boot.  


Follow installer steps until you get to the partitioner.  Tell it to use guided-largest continuous freespace.  That will automatically set up your second partition.  Follow the steps until it asks to install the master bootloader to some place.  Say no.  Then it will ask you where to install the bootloader.  If windows is on your 1st half and linux is on the second, enter "(hd0,1)" .  That's your first hard drive and your second partition.  It starts counting at "0" instead of 1.  If you have more partitions, install it on the partition that linux is sitting on.  

Thats all really.  You partition, make sure windows is on 1st partition, and that the bootloader is installed on the partition that linux is on.  Then, everytime you boot up, it should ask if you want to load ubuntu or windows.  

Hope that helped

P.S. If you already have windows installed and need to just add ubuntu, thats different.  I can help you there too if that's the case.

---

### Post by erfahren on 2007-11-27
> **Afkpuz said:**
> Follow the steps until it asks to install the master bootloader to some place.  Say no.  Then it will ask you where to install the bootloader.  If windows is on your 1st half and linux is on the second, enter "(hd0,1)" .  That's your first hard drive and your second partition.  It starts counting at "0" instead of 1.  If you have more partitions, install it on the partition that linux is sitting on.  

Thats all really.  You partition, make sure windows is on 1st partition, and that the bootloader is installed on the partition that linux is on.  Then, everytime you boot up, it should ask if you want to load ubuntu or windows. 
I think your wrong about that part. See what it says about that at hermanzone 
[http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location](http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location)
> 
If you want GRUB's IPL installed to the first sector of your Ubuntu partition, type (hd0,1) or /dev/hda2 here (where hd0,1 or /dev/hda2 is the correct designation for your Ubuntu partition.
That means you will have to chainload GRUB from another bootloader or boot manager like GAG Boot Manager in MBR or from a floppy disk or a CD.

I've always installed GRUB to the MBR. The only downside(?) is that you just can't go and delete the Linux partition since that's where the rest of GRUB is. The MBR would need restored (he covers that as well on that site).

---

### Post by Afkpuz on 2007-11-27
If you have only 1 hard drive, installing the boot loader to where I said works fine.  I've done that on almost every install.  I tried installing to the MBR once and it killed my windows.  Haven't had windows ever killed when installing to the linux partition.  It's just a precaution, but that problem was also in dapper.  Either way, it will still work well if you install the boot loader to your linux partition.  Also, if you erase your linux partition, windows still lives without any tweaking.  Seems easier in my mind.  Don't have to mess with the MBR everytime you format the linux partition (like on fresh upgrades).

---

### Post by erfahren on 2007-11-27
I guess I'm a little confused about this, Afkpuz. When you install the bootloader to the Linux partition what kind of boot menu do you get when first booting your computer? You wouldn't get GRUB.
> 
That means you will have to chainload GRUB from another bootloader or boot manager like GAG Boot Manager in MBR or from a floppy disk or a CD.

take a look at this: [http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

If you do get the GRUB menu than I imagine that you have installed it to the MBR sometime in the past, but just haven't written over it.

In any event, when reinstalling Linux I've never had to mess with the MBR again (like restore it or whatever). I just format my Linux partition(s) while booted up into the CD, and install. The second part of GRUB gets reinstalled at the same time and all is well.

---

### Post by Afkpuz on 2007-11-27
I did a clean install of windows first, then installed ubuntu.  The boot loader went onto the second partition of my hdd, which is where linux was.  I've done that at least twice on fresh installs of both.  I once tried to install to the MBR and it broke both.  It should be noted that this was 3 distros back (dapper)  I do get the grub menu to come up when I boot.  I have yet to try any other way since dapper.  It just worked for me.  Doing this has allowed me to dual boot with dapper, edgy, fiesty, and gutsy+windows.  But I no longer use windows, so I don't have to mess with any of this.

---

