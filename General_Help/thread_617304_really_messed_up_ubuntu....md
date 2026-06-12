---
title: "really messed up ubuntu..."
date: 2007-11-19
forum: General Help
---

### Post by zivxx on 2007-11-19
ok guys i really messed up my ubuntu trying to fix some laggs in there..so now i have to delete it and re-install it...but i have no idea how to do it tbh..i got the CD if needed but i want to compeletly delete my ubuntu and start it all over again like in the first time with the trial version and the full installation...is it possible?if it is..how i do it?

---

### Post by kshane on 2007-11-19
> **zivxx said:**
> ok guys i really messed up my ubuntu trying to fix some laggs in there..so now i have to delete it and re-install it...but i have no idea how to do it tbh..i got the CD if needed but i want to compeletly delete my ubuntu and start it all over again like in the first time with the trial version and the full installation...is it possible?if it is..how i do it?

Boot up with the Live CD and then install again.  When it gets to the partitioning part, format the partition again and it'll be a clean install...

Kevin

---

### Post by zivxx on 2007-11-19
how exactly do i boot the CD on ubuntu?

---

### Post by Zipster90 on 2007-11-19
You should be able to just pop in the CD and restart your computer to boot from the CD. If it doesn't, you'll need to adjust the BIOS so it will boot from the CD.

---

### Post by zivxx on 2007-11-19
ok,
i set all 3 "boot from" at the bios menu to the CDROM
i entered a disc to both of my cdroms but it still load the ubuntu i already installed :/
any idea?

---

### Post by kshane on 2007-11-19
> **zivxx said:**
> ok,
i set all 3 "boot from" at the bios menu to the CDROM
i entered a disc to both of my cdroms but it still load the ubuntu i already installed :/
any idea?

How did you install Ubuntu to begin with?  

Is your system dual boot with Windows?  If you can't get the CD to boot, you may be able to format the Linux partition using Windows.

Kevin

---

### Post by henkasdf on 2007-11-19
Hi,

See if your pc boots up with a request to boot from cd (make sure the cd is inserted) if you see the request - press "enter" or "space bar".

That should do the trick.

When your 1st boot device is set to CD-Rom in the BIOS it should work.

On older machines with 2 CD-Roms you sometimes need to put the disc in the 2nd CD-Rom.

Hope you get right.

henkasdf

---

### Post by zivxx on 2007-11-19
when i installed it in first time i used all partition for linux, no more windows but i installed it that way:
i enter the CD
restrated few times..no booting so i did,
right click on cd->explore
double click on install
then it ran some weird installation, restart computer
it loaded linux trial version, and on that version there was an installation for linux..installed that ubuntu,restarted and thats it....i never booted form the CD also in the first time

---

### Post by zivxx on 2007-11-19
henkasdf,
my computer has 2 cdroms and its from 2005,you think i should enter 2 CDS to both cdroms at the same time?

---

### Post by teryowen on 2007-11-19
i dont see how the live CD doesnt work, maybe you should fix that problem before you format because how are you going to install it later if you cdrom is busted.

Make sure your cd drive is working, and that your cd is clean, next i dont understand what you mean by: > i set all 3 "boot from" at the bios menu to the CDROM

Try to go to the BIOS and in the boot options make sure that the CD drive is higher in priority than the hard drive.

If your CD doesnt boot then your BIOS is not working properly or your CD is not working.

---

### Post by henkasdf on 2007-11-19
I am not sure why that is not working.  Strange that you had a "trial" version of Linux - Ubuntu is 100% free!  What version of Ubuntu do you have?

henkasdf

---

### Post by zivxx on 2007-11-19
> **teryowen said:**
> 
If your CD doesnt boot then your BIOS is not working properly or your CD is not working.

both cdroms working great, i had cds in them just a few hours ago and both worked...and for the BIOS menu it look something like that,

First boot from:CDROM
Second boot from:CDROM
Third boot from:CDROM
you think i should change any of those?

---

### Post by zivxx on 2007-11-19
> **henkasdf said:**
> I am not sure why that is not working.  Strange that you had a "trial" version of Linux - Ubuntu is 100% free!  What version of Ubuntu do you have?

henkasdf

1st, i didn't meant exactly a trial version..it was more like an example
and i use Ubuntu 7.10 Gutsy Gibson

---

### Post by teryowen on 2007-11-19
Not sure why it shows 3 CDROMs, when you have 2, but as long as the hard drive is below them it should boot from the cdrom.

When you put the CD into your drive and restart the computer, make sure when it asks boot from CD you press enter, this is required on some computers.

---

### Post by henkasdf on 2007-11-19
You can check by switching the cd from one CD-Rom to another.  If that still does not work then pehaps your cd is damaged or a little scratched.

When last did your CD-Roms work.  Could the fault be possibly with them?

---

### Post by zivxx on 2007-11-19
henkasdf, they worked few hours ago when i was ripping music off backup CDS i made when i had XP...so i don't think
teryowen,
the BIOS menu looks like this:
i enter the menu,advanced BIOS features, in there i see:
Hard Disk Boot Priority [Press Enter]
First Boot Device [CDROM]
Second Boot Device [CDROM]
Third Boot Device [CDROM]
Password Check [Setup]
CPU Hyper-Threading [Enabled]
Limit CPUID Max. to 3 [Disabled]
No-Execute memory portect [Disabled]
CPU enhanced Halt (C1E) [Enabled]

tell me if you see anything wrong with those, im gona try to set 1st and 2nd boots for cdrom and 3rd to hard drive

---

### Post by teryowen on 2007-11-19
try hight lighting the hard disk and then pressing the minus key - to bring it down in priority what this seems like to me is that your hard disk right now has priority so bring it down.

---

### Post by teryowen on 2007-11-19
Also what happens when you press ENTER over hard disk boot priority?

EDIT: if you think you have everything set up correctly in the BIOS try unplugging the HD but once the CD begins booting plug it back in. be careful with this step its what i would do dont do it if you don't feel comfortable with it.

---

### Post by zivxx on 2007-11-19
ok tey, i entered the Hard Disk Boot Priority and there were 2 options there, my Hard Disk was on 1st, so i changed the other to the first and,
at the boot devices its now that way,
1st CDROM
2nd disabled
3rd disabled

---

### Post by zivxx on 2007-11-19
ok..i saved changes and restarted computer and here it what it says:
( right before op system should load)
Disk Boot Failure, Insert System Disk and Press Enter.
i press enter..and it tell this again...and again and still nothing happen
any idea?

---

### Post by teryowen on 2007-11-19
So you have a faulty CD, burn an ISO image of ubuntu on a new CD at 4x maybe even 2x for safety.

---

### Post by zivxx on 2007-11-19
About unplugging my HD..i think we might have to save that step for the last one..the last tiem i unplugged my HD i ruined it and had to buy a new one

Edit:ok i will burn new one right now, luckily i accidentaly downloaded ubuntu desktop instead of kubuntu when i was installed kubuntu :)
BTW, when i open the ISO file with cd/dvd creator the lowest speed is about 5.6x or something like that

---

### Post by teryowen on 2007-11-19
good idea.

 you dont have to unplug it anymore anyways, because now it tries to boot from the CD.

---

### Post by henkasdf on 2007-11-19
I worked in a technical dept of a harware company and I have seen that a faulty BIOS can be the cause for bootable CD's not to boot.  Both CD-Roms cant be faulty.

---

### Post by teryowen on 2007-11-19
Henkasfd 
Not the CD ROM butthe CD it self, it may be scratched or just be corrupt due to a bad burn.

zivxx: go ahead and burn it hopefully it works.

---

### Post by zivxx on 2007-11-19
ok the lowest speed on CD/DVD Creator is 4.7x
im burning 1 right, im gona burn 2 in case that i will ned to insert for both of the CDROMS


Edit:btw henkasdf,
my CDROMs are just fine, for example when i enter the ubuntu installation CD on ubuntu the CD picture show up saying"Ubuntu 7.10 i386"
so the problem is probably no with the CDROMs

---

### Post by teryowen on 2007-11-19
Is everything working for you?

---

### Post by zivxx on 2007-11-19
ok i was away and..i still get the same massage after burning another 2 copies...and when i switch between the options in the hard disk priority it goes normally to ubuntu again...any ideas?

---

### Post by zivxx on 2007-11-19
anyone?

---

### Post by teryowen on 2007-11-19
do you have a floppy frive inserted or a usb connected like an external hard drive try removing those and starting up again.

Im almost completely certian that the fix will be found in the BIOS, im not there to see how the BIOS looks but it seems that the BIOS is the problem.

---

### Post by zivxx on 2007-11-19
what connected to my comp is:
optical mouse-USB
keyboard
screen
bluetooth device
internet router
and thats all i think..what should i disconnect?

---

### Post by teryowen on 2007-11-19
No those shouldnt be problematic. Just play around with your BIOS, whats happening right now is that your computer is trying to boot from either the hard drive (ubuntu whihc u dont want) or some other device (which doesnt work which is why you get the error messege) I think its the bios that problematic rite now.

---

### Post by zivxx on 2007-11-19
you think i should unplug the HD?

---

### Post by teryowen on 2007-11-19
Ok if your gonna do that make sure your computer is completely off power out everything off power supply off.

Unplug.

Everything ON, try booting up see how things go.

DO NOT plug in the hard drive while the computer is running as this may cause problems to the hard drive.

If the CD boots im not really sure how to go about connecting the hard drive as there is no guarentte as to what would happen to the hard drive.

EDIT: i still think this wont do much because the problem your having is with the BIOS trying to boot of a device which isnt bootable.

---

### Post by zivxx on 2007-11-19
ok well i guess i won't unplug the HD, do you go an msn,yahoo aim or icq so i could go on the other computer and instnat talk with you while im on the BIOS menu to see whats wrong

---

