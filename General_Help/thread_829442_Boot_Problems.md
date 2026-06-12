---
title: "Boot Problems"
date: 2008-06-14
forum: General Help
---

### Post by shewy on 2008-06-14
so i installed ubuntu 8.04 Hardy heron on my acer aspire 5610 laptop. it has vista home premium installed on the internal hard drive, so i went through the live cd and installed ubuntu on an external hard drive and all was good i could go through my boot menu and select which to boot from. the only problem i had was that i couldnt get into my boot options unless the external was connected which was fine temporaraly but i intended on solving that. 

the other night i plugged the drive in and was going to boot into ubuntu and "tick tick tick tick" the hard drive failed, now i cannot get past a GRUB error 21 "drive is not present" and i cannot even boot into windows, i have tried my vista discs and tried restoring my system, restore goes through and recovers windows but it still wont let me load past the error.

i have everything backed up onto another external but the one i had ubuntu on is toast and i cannot get anywhere past the error.

any ideas??

thanks in advance, Richard

---

### Post by meierfra. on 2008-06-14
Get SuperGrub (see my signature) and then follows these [instruction ]("http://www.supergrubdisk.org/wiki/UninstallGRUB")to fix the MBR of your internal drive.


If that did not get you back into Windows, click on FixMBR in my signature for other ways to restore the MBR.

---

### Post by shewy on 2008-06-15
well i did read those and if what i understand is correct i need to be able to ither boot into windows or ubuntu to use those options, i cannot even get the live cd to run, so i cant even get into my boot manager to change anything. so i was talking to a friend about what he thought that removing my internal hard drive, wipe it so it clears boot manager, and reinstalling vista, then reinstaling ubuntu and starting over from square one. 

any thoughts on this?

---

### Post by meierfra. on 2008-06-15
>  boot into windows or ubuntu

No, you have to boot from the SuperGrub disk and then follow the instruction:

[http://www.supergrubdisk.org/wiki/UninstallGRUB]("http://www.supergrubdisk.org/wiki/UninstallGRUB")

---

### Post by shewy on 2008-06-15
thank you very much it worked like a charm, this little glitch isnt going to stop me from using ubuntu ither, 

if i was going to set ubuntu onto an external drive what would be the best and simplets was to be able to boot ubuntu when i want to but boot vista when the hard drive disconnected or when i just want to use vista?

---

### Post by logos34 on 2008-06-15
> **shewy said:**
> if i was going to set ubuntu onto an external drive what would be the best and simplets was to be able to boot ubuntu when i want to but boot vista when the hard drive disconnected or when i just want to use vista?

The simplest, surefire method would be disconnect the internal laptop hard disk, then boot from the ubuntu cd and install to the external usb.  That way   grub ends up on the MBR of the external, and no editing of grub files needed.  Set the bios boot order to usb first, then the internal drive.  When the external is connected, you boot to grub on that, otherwise you boot windows.

But to access windows partition from linux you'll have to add it to fstab, either manually or using [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971")

You might also want to get fs-driver for windows (rw access to ext3)

---

### Post by meierfra. on 2008-06-15
Various options:

**1) **  Disconnect your internal drive while installing Ubuntu.  Set you bios to boot from the external drive. Add Vista to the grub menu:
```
gksudo gedit /boot/grub/menu.lst
```
and add this to the end of the file:

title  Vista
root (hd1,?)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

(the ? depends on the locations of Vista. If Vista is the first partition on the internal drive, then ? is 0, if  Vista is the second partition, then ? is 1, and so on

(Edit:  Adding Vista to the grub menu is not necessary, since you can also boot into Vista by either disconnecting the external  drive or switching to boot order in the bios) 

**2) **  Leave the internal drive connected. At step 7 of the installation click on "advanced". This lets you choose the location for the boot loader, choose the MBR of the external drive (usually /dev/sdb). Set your bios to boot from  external drive.

This is the easiest way, but sometimes the installer gets confused with the two hard drives. But that is easily fixed. Just come back to the forums and ask for help.


**3) **   Get EasyBCD (see my signature) and follows these instruction:
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")
Set your bios to boot from the internal drive.


(Edit:  Didn't see Logos34 post until after I posted this.  His method is the same as my method 1) )

---

### Post by shewy on 2008-06-15
i will use one of those methods im sure,

i must say iv been on forums before but since i joined this one like 2 days ago i installed my first ever ubuntu install and i then got my problem fixed in like an hours work and the response times you guys had was remarkable i would just like to say thanks for the help, and i will stick with ubuntu

---

### Post by logos34 on 2008-06-15
> **meierfra. said:**
> Various options:

Somehow I new there was another reply coming...

I have 3 questions/observations:

The whole point in disconnecting the internal drive is to keep things separate, in which it defaults to windows unless the usb drive is connected.  So why bother with a windows stanza in menu.lst?  

Second, if you do add windows entry, root would be (hd**1**,?), and you'd need mapping:
> 
title Vista
root (hd1,?)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

since in this case you're be booting to the external (hd0), and the internal would be seen as (hd1).


Third, there's no need to fiddle with step 7, grub location, etc. when installing with the internal drive disconnected.  There's only one MBR it can go on--the usb.  Again, that's the whole point.

---

### Post by logos34 on 2008-06-15
> **meierfra. said:**
> (Edit:  Didn't see Logos34 post until after I posted this.  His method is the same as my method 1) )

I posted 10 minutes before you.

---

### Post by jw5801 on 2008-06-15
> **logos34 said:**
> I posted 10 minutes before you.

Fairly thorough post though, perhaps took 10 minutes after encountering the thread?

---

### Post by meierfra. on 2008-06-16
> I posted 10 minutes before you.
Your post was not there then I started typing.
I type slowly,  had to look up the EasyBCD link ...


> The whole point in disconnecting the internal drive is to keep things separate, in which it defaults to windows unless the usb drive is connected. So why bother with a windows stanza in menu.lst?

I almost always have my external drive plugged in. Then it is just easier to  have Vista on the Grub menu.

> Second, if you do add windows entry, root would be (hd1,?), and you'd need mapping:


I  fixed that while you were typing this.

> Third, there's no need to fiddle with step 7, grub location, etc. when installing with the internal drive disconnected. There's only one MBR it can go on--the usb. Again, that's the whole point.

But you have to edit "fstab", and if you want Vista on the Grub Menu, you have to edit "menu.lst". And you have to disconnect the internal hard drive. There are lots of people who rather not do that.

(Edit: and again I hadn't seen jw5801 post, before I started this. I'm just slow.)

---

### Post by jw5801 on 2008-06-16
There's also the other option of creating a seperate /boot partition on the internal drive and installing grub to that. But that gets a bit more complicated, especially if you're just using a spare external drive to have a play with Ubuntu at this point. I currently have Ubuntu and Gentoo on my internal drive and I occaisionally have other things on an external, so using a seperate boot partition makes sense in my case.

---

### Post by meierfra. on 2008-06-16
> here's also the other option of creating a seperate /boot partition on the internal drive and installing grub to that. 

Now I have to take logos34 point of view: This really disturbs the independence of the hard drives  
I like to setup  my external drive setup so that I can plug it into any computer and boot from it.

But of course, if that isn't your goal, a separate boot or grub partition, can by useful.

---

### Post by jw5801 on 2008-06-16
> **meierfra. said:**
> Now I have to take logos34 point of view: This really disturbs the independence of the hard drives  
I like to setup  my external drive setup so that I can plug it into any computer and boot from it.

But of course, if that isn't your goal, a separate boot or grub partition, can by useful.

A fair point. In that case you could have the boot partition on the internal with a chainloader reference to the external so you can still use the external elsewhere. But that's getting a bit convoluted I think. It all depends on what your goal is, in my case my external is purely there for testing (other partitions on it are for storage/backup), so I don't need to be able to boot from it anywhere else.

---

### Post by meierfra. on 2008-06-16
> In that case you could have the boot partition on the internal with a chainloader reference to the external so you can still use the external elsewhere.

Indeed, and I actually do that. My grub menus on the  external and internal drives  chainload  each other. So  no matter from which drive I'm booting  I can reach each of my OS's and the drives are completely independent.

---

### Post by jw5801 on 2008-06-16
> **meierfra. said:**
> Indeed, and I actually do that. My grub menus on the  external and internal drives  chainload  each other. So  no matter from which drive I'm booting  I can reach each of my OS's and the drives are completely independent.

Nice, saves having to fuss with bios boot orders.

---

