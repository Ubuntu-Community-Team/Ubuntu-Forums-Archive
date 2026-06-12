---
title: "Fix grub on ubuntu live help"
date: 2007-06-29
forum: General Help
---

### Post by pspfreak101 on 2007-06-29
Well I kinda deleted a part of my hard drive that i thought was not ubuntu because thier was one by it that was 4gb and thought that was ubuntu hardrive went like this 
"[  Vista  ][   70gb  ][ubuntu 4gb][ recovory for vista ]" anyways the next time i restarted my computer it said loading...error 17 on the grub . I had the ubuntu cd so i booted that and tried a guide on the live like this ```
 sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> exit
```
Please help thanks and kinda new to ubuntu so please expain good

---

### Post by bodhi.zazen on 2007-06-29
Well, if you deleted or formatted you Ubuntu partition you are looking to re-install more then grub :)

You either need to re-install Ubuntu (grub will come with that as a bonus).

Or if you are trying to remove ubuntu you need to re-install the windows boot loader. You will need to do that from your restore partition ...

But as your partitions are now (hd0,0) = vista and so you can not simply use grub + vista.  Well I suppose you could make a small /boot partition and install grub using that as root.

So the it would be <vista> </boot>

/boot could be small ...

Then
grub> root (hd0,1)
grub> setup (hd0)

HTH

---

### Post by pspfreak101 on 2007-06-29
well I tried that and i get an error ```
grub> root (hd0,1)

grub> setup (hd0)

Error 17: Cannot mount selected partition


```
This is when I do tab
```
Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```
all of them are unknow I don't have the vista disks but just the recovory ones but they won't boot so I can't reinstall the boot loader  but if I could just boot into vista and delete the 4gb then repartition it and then reinstall ubuntu it should be fixed right?/
////////////////////////////////////////UPDATE\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
WOOT!!! well I downloaded super grub disk and put it on my psp then used thier boot tools and just booted to vista and ubuntu was still thier so i guess i didn't delete it

---

### Post by Puppy Fan on 2007-06-29
[COLOR="Blue"][/COLOR]

Hey Guys,


I am in a similar jam  I have a laptop HP dv8339us with dual 100GB hard drives which has suited me well for the purposes of dual booting.  

Previously, UBUNTU 7.04 Desktop 386 installed itself to (hd1), claiming space after a storage partition I used for Vista.    Maybe I should have shrunk the storage partition in my (hd1), leaving some unallocated space.  I have done this once before with Vista RC1 last year.  This was when I was more fearless, and less careful.  (When I boot UBUNTU 7.04 Desktop on the Intel Core Duo HP Pavilion dv8339us, I *always[I] get memory allocation errors...but that's an HP story for another day, but I think I need a better BIOS w/ out acpi bugs) *[/I]Vista's Virtual Disk Management seems dual-boot friendly.  I recall wanting to see how UBUNTU 7.04 desktop would handle the situation.

Eventually I screwed things up and Vista wanted to run checkdisk on the 2nd hardrive (hda1) each time I selected it from the grub boot menu.  I wouldn't let it since my instincts told me that it was viewing the ext3 fs as a potential threat.  A colleague mentioned something about the cardinal sin of dipping into a partition created by Vista for file storage using Nautilus.  He mentioned corruption, I changed the subject.

So Vista entered the "boot cycle that never ends."   There was a flash of blue screen and reboot before the boot cycle completed.  The Vista Boot Disc's Repair Console, presented itself as efficient, purposeful, and meticulous, but to no end.  The most info. I got was that A. A patch was preventing the Vista OS from starting and B. I was told to see my System Administrator about having "connected a foreign device like a camera, to the machine recently"  ????  I am my administrator, but tend not to trust my judgement in situations like these.  (Please won't you be my administrator?...Ah, but, things were so much simpler for us in the days of Mr. Roger's Neighborhood.) 

So Ubuntu continued to boot using Grub, unaffected by Vista's demise.   So what did I do?
I reinstalled Vista.

In the virtual disk manager it says I need to format the (hda1)...2nd HDD within which Ubuntu has 2 partitions and Vista 1 big storage partition (I know it is still there, because I can see it with the UBUNTU 7.04 live disk)  But I refuse to reformat it, as Vista suggests.

How do I find Grub?   The live CD tells me that its backup copy is usable but that its original copy is corrupt.  Should I reinstall Grub?  If so, how and where?  hd0 is Vista only, new fresh, I suppose I could just reinstall Ubuntu on that 1st disk, but I don't want to risk loosing storage data on the 2nd.

Maybe it is time for Steve Gibson's Spinrite.  I am getting desperate.  Maybe I should just post on craigslist to distract myself and complicate my life in more exciting ways. lol

Your help is much appreciated.  Thanks in advance.

:D

---

### Post by Pheodax on 2007-06-29
I have used Super GRUB Disk to fix some GRUB problems several times. I have had the error 17 message as well. GRUB uses your BIOS settings to order the order of your HDDs. In my case this order was a littlebit odd and caused the GRUB to be installed on the wrong HDD. When I copied it to another HDD, GRUB did load, but it gave me the error 17 message. I then modified the loading command a few times by pressing E in the GRUB menu.

find /boot/grub/stage1
Gave me: (hd1,0)

In the GRUB loader I editted (press E to edit, B to boot) the root to (hd2,0) instead of the suggested (hd1,0) and it worked. I logged into Ubuntu, changed the menu.lst file (/boot/grub/menu.lst) and modified the file to fix the issue (changed hd1 to hd2).

Kernel, GRUB en BIOS all have a different order of HDDs... Really odd. Anyway, I hope this helps. Forgive me for my bad English.

---

### Post by Puppy Fan on 2007-07-02
Vista is objecting to my second HDD which has Ubuntu in it as well as a partition of storage for Windows.   I cannot get into anything on that disk.   Vista is booting and running fine, but I would like to straighten this all out...I downloaded the GParted Live CD.  I really don't know what I should do at this point...more research.
:D

---

