---
title: "GParted LiveCD stops at 'grub&gt;'...what am I missing?"
date: 2008-03-25
forum: General Help
---

### Post by PhilCash on 2008-03-25
G'day All,

Help! 
I'm stuck at         grub>

Every GParted LiveCD I try boots to        grub>     and nothing more. 

I'm not yet familliar with Grub, so do not know how to proceed although from reading the threads relating to GParted LiveCD, it seems it should just start GParted without intervention

I've downloaded both the GParted LiveCD iso file and the GParted-LiveCD - Clonzilla iso file and have burned several image cds of each using Nero in WinXP, and CD/DVD Creator, and GnomeBaker in Ubuntu, but all display the same behaviour.

Am I not burning the CD from the iso file correctly? Is there a hidden switch I've missed?

Any suggestions would be appreciated.

Cheers,
Phil

---

### Post by LaRoza on 2008-03-25
Are you sure the CD is booting? (In other words, does the system boot to an OS when you start it normally)

It is likely a faulty ISO, did you check the MD5?

---

### Post by PhilCash on 2008-03-25
G'day LaRoza,

With no CD in the CD drive, the system boots fine, providing me with several boot choices for Ubuntu or WinXP from the HDD.

I've only recently installed Ubuntu, and the system booted from the installation LiveCD just fine for that.

The system 'seems' to be booting from the GParted LiveCD as the GNU GRUB information header and the 'grub>' prompt is comming from somewhere. If it were from the boot sector of the HDD I'd expect it to boot as it normaly does without a bootable CD in the drive.

A faulty iso was my first thought too, but I've checked the MD5 of the iso's with md5sum and both are fine.

Is there a question I'm not aware of that I should be asking about burning an image to CD for correct booting as a LiveCD?

---

### Post by louieb on 2008-03-25
The GParted live CD has always been hit or miss working for me. Its not being supported any more either. Don't know why the Clonezilla CD is giving problems. But anyway  when I need to use GParted I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") Might give that a try. 

When I burn an ISO to CD it just right click on the ISO in Nautilus and choose **write to disk **and burn at 2X**. **Doesn't seem like your doing anything wrong - don't know why your having problems. Just letting you know what works for me. Good Luck.

---

### Post by LaRoza on 2008-03-25
> **louieb said:**
> The GParted live CD has always been hit or miss working for me. Its not being supported any more either. Don't know why the Clonezilla CD is giving problems. But anyway  when I need to use GParted I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") Might give that a try. 

When I burn an ISO to CD it just right click on the ISO in Nautilus and choose **write to disk **and burn at 2X**. **Doesn't seem like your doing anything wrong - don't know why your having problems. Just letting you know what works for me. Good Luck.

The GParted Cd has always worked for me. And the project is active and has new owners and they just released a new version and fixed a bunch of bugs in it, so your information is a little out of date.

When I have a faulty burn (usualy because it was interupted in my case), I get the grub> thing as well.

Check the ISO, and then burn it at a slow speed (I also use 2x).

---

### Post by smoker on 2008-03-25
try disabling the hard drive boot option in the bios, so it has no option but to boot from the cd. you can always change it back after using gparted

best of luck

---

### Post by louieb on 2008-03-25
> **LaRoza said:**
> .. And the project is active and has new owners and they just released a new version and fixed a bunch of bugs in it, so your information is a little out of date.

Just checked GParted itself has new maintainers. And put out a new release in Feb 2008. 
However the GParted live cd project is not being maintained and hasn't put out a new version since November 2007.  The latest systemrescue CD does have the new version of Gparted.

---

### Post by PhilCash on 2008-03-26
Sorted!
Thanks for all the suggestions and assistance everyone.
Never did get GParted LiveCD or the GParted-LiveCD/Clonzilla CD to get past grub>, but the SystemRescueCD works fine.

Thanks again,
Phil

---

