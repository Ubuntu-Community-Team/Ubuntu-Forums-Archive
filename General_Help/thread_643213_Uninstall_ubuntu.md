---
title: "Uninstall ubuntu"
date: 2007-12-17
forum: General Help
---

### Post by Christian Christiansen on 2007-12-17
My dad somehow magically installed ubuntu onto my laptop but it doesn't work :(.
Now my laptop is running really slowly so I really need the RAM back for my Windows 2000.
Using a Windows 2000 disk is not an option as Windows 2000 was pre-installed on my laptop.

Any step by step guides would be really helpful as I'm still quite new to all this.

---

### Post by cmnorton on 2007-12-17
> **Christian Christiansen said:**
> My dad somehow magically installed ubuntu onto my laptop but it doesn't work :(.
Now my laptop is running really slowly so I really need the RAM back for my Windows 2000.
Using a Windows 2000 disk is not an option as Windows 2000 was pre-installed on my laptop.

Any step by step guides would be really helpful as I'm still quite new to all this.

What exactly does not work? What is not running fast enough? Can you still boot into your Windows 2000 partition?

---

### Post by Christian Christiansen on 2007-12-17
Ubuntu 7.10 Gutsy Gibbon doesn't work. When I boot it up the screen just goes black and then it shows the login window but it flashes and goes up and down and basically makes it impossible to login.
When I boot up in Windows 2000 it works perfectly apart from it takes much longer to boot up and the applications I use take a lot longer than usual to start.
By the way my laptop is a SONY NOTEBOOK COMPUTER PCG-161M.

I've searched and read quite a bit about this but I can hardly understand half of what is being said.
Are there any step by step guides?

---

### Post by eggdeng on 2007-12-17
> I really need the RAM back
You mean disk space. Having a Ubuntu install on your disk will only slow your system down if the W*nd*ws partition is very nearly full and there is no space left for virtual memory (less than 1 or 2 gigs.) Unless this is the case, getting rid of Ubuntu will not help. Even so, an easier solution would be to simply make room on the W*nd*ws  partition.

---

### Post by erfahren on 2007-12-17
hold off ... (see my next post)

---

### Post by staticvoid on 2007-12-17
did he use wubi?

that sounds magical.

just double click the uninstall option in the folder ubuntu is in.

attempt to boot into recovery mode for your ubuntu OS.

---

### Post by staticvoid on 2007-12-17
gparted live disk is your best bet, you will see all that is going on.

simply delete the ext3 partition and expand the XP. 

**FIRST BACK UP YOUR DATA**

sv

---

### Post by erfahren on 2007-12-17
actually, I agree it could be Wubi

anyway if it isn't and Ubuntu was actually installed to a partition on the harddrive you want to download and run this before you go and delete the Ubuntu partition.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Edit: let the OP fix the MBR before the linux partition is deleted!

---

### Post by Christian Christiansen on 2007-12-18
I've tried recovery mode but nothing happens. By the way I know nothing about hardware and don't know what Wubi is. Anyway I'm going to try out GParted and see what it does.

---

### Post by erfahren on 2007-12-18
> **Christian Christiansen said:**
> I've tried recovery mode but nothing happens. By the way I know nothing about hardware and don't know what Wubi is. Anyway I'm going to try out GParted and see what it does.
I'll expand on my answer a little here.

I'm not totally familiar with [Wubi](http://wubi-installer.org/), but it's a way to install Ubuntu within Windows. In that event it sounds like you just can uninstall it like any other program.

The other way we talked about here is installing Ubuntu in a dual-boot environment. When you first boot the PC you'd get a menu to select which operating system to boot (Windows or Ubuntu). That menu would be the GRUB menu.

GRUB (by default) overwrites a portion of the MBR (Master Boot Record) of the harddrive and instructs the boot process to access GRUB itself (which, by default, resides on the Linux partition) - to finish the boot process. So basically, if you just go and delete the Linux partition, GRUB is deleted along with it and you can no longer boot Windows.

You would then have to use a boot disk of some kind to fix the MBR in order to boot Windows.

It's far easier to repair the MBR ahead of time using MbrFix.exe while you are still able to boot Windows. (Boot into Windows > fix the MBR > *then* delete the Linux partition.)  

**It would be good for those answering these questions to not just come out and tell someone to *"just delete the Ubuntu partition"*, and then have them go download another utility to repair the MBR afterwards (which they will *inevitably* have to do).**

---

### Post by Christian Christiansen on 2007-12-18
I'm sorry that I need explaining like a five year old but how do you fix the MBR?
By the way, thanks for making me finally understanding a tiny bit about how GRUB works.

---

### Post by eriqjaffe on 2007-12-18
> **erfahren said:**
> IWhen you first boot the PC you'd get a menu to select which operating system to boot (Windows or Ubuntu). That menu would be the GRUB menu.Well, you get a menu with WUBI, too.

Christian:  If you see an entry for "WUBI" in the Add/Remove Programs control panel in Windows, just uninstall it, and Ubuntu will be gone, just as magically as it got there in the first place.  If it's **not** there, you'll have to follow the more in-depth procedures elsewhere in this thread.

---

### Post by erfahren on 2007-12-18
> **Christian Christiansen said:**
> I'm sorry that I need explaining like a five year old but how do you fix the MBR?
By the way, thanks for making me finally understanding a tiny bit about how GRUB works.
no problem, it isn't a dumb question

first thing I need to ask is: when you first boot the pc do you get a menu that looks something like what's shown here? (scroll down a bit): [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by forestpixie on 2007-12-18
> **erfahren said:**
> [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

that is a useful piece of information to pick up - having never read through the whole of the hermanzone site I'd never seen that bit - added to my little pile of notes :D

---

### Post by eggdeng on 2007-12-18
My bad. erfahren is right. (Er muss erfahren sein).

---

### Post by smartboyathome on 2007-12-18
Well, since your laptop runs windows 2000, no wonder it doesn't run Ubuntu! I would probably recommend SAM Linux/Linux Mint XFCE edition at MAX for that computer.

---

### Post by Christian Christiansen on 2007-12-19
> **erfahren said:**
> 
first thing I need to ask is: when you first boot the pc do you get a menu that looks something like what's shown here? (scroll down a bit): [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Yes. My laptop uses GRUB (and not Wubi). When I boot up my computer it looks like the picture you showed me.

---

### Post by erfahren on 2007-12-19
ok, go and download & run the little utility by the instructions given here: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

once yo fix the MBR it should boot into Windows immediately again.

you can then go to Windows Disk Management (part of the Administrative Tools or through the Control Panel) 

in there you can click on (or right-click on) the partitions created for Ubuntu and delete them (there should be two a larger one and a small one that is only about 512MB to 1GB). You can then reformat the space as FAT32 or NTFS and use it for storage.

Someone mentioned growing the C:\ partition to retake the space. In that event you probably would need something like [GParted](http://gparted.sourceforge.net/) - you'd have to download it, burn it to a CD and boot into it in order to resize the C:\ partition to retake the space. (I'm not going to go into that.) 

if you want you can post a screenshot of the partition table if you have questions at that point.

---

