---
title: "Help me clean a Grub 22 Error,"
date: 2007-02-06
forum: General Help
---

### Post by Ewat on 2007-02-06
Hello,

After many tries of loading Ubuntu 6.06 unsuccessfully on my IBM T40 Laptop with WinXP, I finally did it. However, I had to delete Windows! 

During the process I got a Grub 17 error, now I get Grub 22 and an "Authentication" thingy. Additionally, When I try to access the BIOS. While holding the key to access it, the boot goes past the BIOS and gives me the Authentication and Grub 22 error messages.

Please help me get past these error messages. Or, should I wipe the hard drive and start over. I wonder if that will help?

Desperate for success with Ubuntu.

---

### Post by rsambuca on 2007-02-06
A few questions...  Do you still have XP on the machine?  If so, how is your drive partitioned?
The grub error should be easy enough to fix, but the "authentication thingy" needs clarification.
Were you installing from the liveCD or Alternate CD?

---

### Post by Ewat on 2007-02-06
Rsambuca,

Thank you for your response. 

I had to remove XP. I choose to let Ubuntu install the partitions from the Live CD.

I really appreciate your help.

---

### Post by rsambuca on 2007-02-06
So do you now have just one partition?  It might be easiest if you run the liveCD and run the program gParted just to see how everything is partitioned first.

---

### Post by Ewat on 2007-02-06
Hi,

Here are the partitions:

/dev/hda1     ext3     2.37 Gb
/dev/hda2     extended    1.55 Gb
/dev/hda5     linux-swap  1.55 Gb

Again, thank you for your help.

---

### Post by rsambuca on 2007-02-06
Try running the live CD.  Then open a terminal and enter```
sudo grub
```
At the grub prompt, enter```
find /boot/grub/stage1
```
It should spit out a location for you such as (hd#,#)  presumably (hd0,0)
whatever is shown for the stage1 grub location, enter ```
root (hd#,#)
``` (where the numbers are what was indicated above)
then ```
setup (hd0)
```
type "quit" to get out of grub, and then try rebooting your PC without the liveCD.

Good luck

---

### Post by Ewat on 2007-02-06
rsambuca,

I am new and never entered commands before, but I think I can do this.

Thanks, again.

---

### Post by Ewat on 2007-02-06
rsambuca,

Success!!! 

Grub 22 is gone. I would be willing to guess that the "Grub Stagel.5" that I see while the machine is in process of booting is normal. 

I still can't access the BIOS, however. When I hit the key to open the BIOS, I get " Authetication of system services failed. Press <ESC> to resume."

If I don't try to access the BIOS, Ubuntu boots fine. Should I reinstall the BIOS, or is there a fix for this problem?

Thank you for hanging in there with this complete novice. Actually, I have overcome some of my fear and feel better about this OS.

---

### Post by rsambuca on 2007-02-07
Congrats on the Grub fix.  You have now become a true command line editing geek (a good thing!).

The grub stage 1.5 thing is normal, by the way.  As far as your BIOS problems, I have never heard of that before, so I can't help you out on that one.  Are you sure you are pressing the correct button at the correct time?  You will need to access your BIOS before the grub loading screen.

---

### Post by Ewat on 2007-02-07
Hi,

You might be right.  My laptop (T40) has a designated button, "IBM Access" that I used to get me to the bios. Since I have been loading Ubuntu though, the process may have changed. I will try another key tonight when I get home. If that doesn't work, I will seek help from the company.

Rsambuca, thank you for your time and dedication to helping me and others.

---

### Post by st0n3cutt3r on 2007-02-07
I have a similar situation, Grub(1.5) 22 Error.

I set up my primary drive to triple-boot.  The partitons are as follow
partition 1:  Windows XP
partition 2:  Windows Vista
partition 3:  (currently Kubuntu, but has been Ubuntu)
partition 4:  Linux Swap

I can get the system to boot only when I insert the Kubuntu Live CD prior to grub loading, and then choose to boot from the first disk once that has loaded.

If I let my system run w/o the Live CD, Grub 1.5 starts I get "Error 22", and nothing else happens.

After I tell the Live CD to boot from first disk, I have the option of running Ubuntu - default, Ubuntu recovery, Windows Vista/Longhorn (loader), and a few other options.

the two Ubuntu options do not work, but the Vista bootmanager does (from which I can choose XP or Vista).

I am using a full version of Vista, and am fairly certain that it has nothing to do with the errors.

----

I tried to get help on the #grub irc channel, but nobody responded.  Here is what I said there (slightly more detailed):

        <Brian_>	I'm having trouble with grub on my computer
	<Brian_>	I partitoned the drive for windows XP, windows Vista, and a version of linux, and swap space.
	<Brian_>	First I tried ubuntu, but that failed to install grub at all
	<Brian_>	then I installed ubuntu on a different disk entirely (the first install seemed to have corrupted somehow)
	<Brian_>	that failed to function as well.
	<Brian_>	then kubuntu on the second disk over the install of ubuntu (w/format)
	<Brian_>	then grub worked, but failed to recognize kubuntu (but would load the install of ubuntu on the primary drive)
	<Brian_>	so I reinstalled kubuntu in the exact same spot it was hoping to get grub to recognize it, but then it wouldn't boot any of the OSs
	<Brian_>	currently, I wiped the second disk completely, and replaced the original installation of ubuntu on partition3 of disk 1 with kubuntu
	<Brian_>	grub 1.5 boots with my computer, but says "error 22" immediately and fails to do anything else (preventing me from accessing any of the operating systems)
	<Brian_>	by booting the kubuntu live CD and telling it to boot from the first disk, grub 1.5 loads and will load windows fine, but says that no recognized files exist where kubuntu is

----

I don't care if I have ubuntu or kubuntu installed, just so long as I have some form of linux filling the space.  Any help is greatly appreciated!

---

### Post by rsambuca on 2007-02-07
If you follow the instructions in post #6 of this thread, I think that should work.  If not, obviously let us know as there are other things we can do.  Do you have two HDD's?

---

### Post by st0n3cutt3r on 2007-02-08
3, actually, but only 2 that I had been fighting with installing OSs on (the third is for my docs)

I haven't tried that set of instructions yet, I'll see if I can get to it tonight.

---

### Post by st0n3cutt3r on 2007-02-08
> **rsambuca said:**
> Try running the live CD.  Then open a terminal and enter```
sudo grub
```
At the grub prompt, enter```
find /boot/grub/stage1
```
It should spit out a location for you such as (hd#,#)  presumably (hd0,0)
whatever is shown for the stage1 grub location, enter ```
root (hd#,#)
``` (where the numbers are what was indicated above)
then ```
setup (hd0)
```
type "quit" to get out of grub, and then try rebooting your PC without the liveCD.


Alright, I tried these instructions, and this is what I got...
The location was (hd1,2).  (I'm not sure if that's important, but I didn't want to miss it if it was).

Everything ran fine, and it seemed to do what it was supposed to, but when I ran without the live cd, same as before "ERROR 22"

Again, I want to mention that I am working with kubuntu right now.  I don't know if that makes a difference at all, but if It does I am just as happy to install ubuntu.

---

### Post by rsambuca on 2007-02-08
The (hd1,2) indicates that the stage1 grub instructions are located in the 3rd partition of the SECOND hard drive (the numbering starts at zero).  I think the easiest thing to try is to change the order of the drives in your system BIOS.  Try changing the second drive to be the first boot up drive.

---

### Post by st0n3cutt3r on 2007-02-08
would swapping the SATA cables attached to the drives do the trick?

---

### Post by rsambuca on 2007-02-08
To be honest, I don't know.  I can't imagine that it would hurt anything.  I am not sure whether the motherboard reads the drive by the SATA port or not.  should be a quick test.

---

### Post by st0n3cutt3r on 2007-02-16
I just realized that while switching the sata cables might fix kubuntu so that *it* loads, it would screw everything else that *is* working up, because it would then be looking in the wrong location for them...  any other ideas?

---

### Post by rsambuca on 2007-02-16
OK, try this:

```
sudo grub
```
```
root (hd0,2)
```
type quit to exit the grub prompt
then try booting from the HDD

The problem is that grub has the drive order mixed up.  We will be able to fix this if this doesn't work.

---

### Post by st0n3cutt3r on 2007-02-19
alright, for some reason the forum isn't notifying me anymore of your responses, so I apologize for the delay.

I booted my computer from the live CD and thought I would give re-installing kubuntu another shot.  Unfortunately, since then Grub does not recognize any of my operating systems.  When I boot through the Live CD (and tell it to boot from the first hard disk) it pulls up the same list of operating systems it always has, but now it can not find any of them. -_-'

I ran the instructions that you told me to earlier (which was supposed to change grub to boot from (hd0), and despite the instructions I had given it earlier, it still instisted that the root was (hd1,2).   I gave it the instructions again, and then when it had given me the output and grub > again then I typed find /boot/grub/stage1 and it said (hd1,2) again.

I then pulled out my Ubuntu CD and decided that perhaps installing a linux OS to the drive that it thought it should be booting from (hd1,2) might fix the problem.

I adjusted the partitions so that they are currently:

sda1 - data
sdb1 - XP
sdb2 - Vista
   sdb3 - (formerly (k)Ubuntu, now unallocated)
sdb4 - SWAP
sdc1 - 8mb ntfs
sdc2 - 8mb ntfs
sdc3 - Ubuntu 6.10

...I'm not really sure what to do with it at this point, and I'm sorry I seem to have complicated the issue.

It now can not boot grub from the live CD or without the live CD (error 22 for both).

One more run of the Live CD and 'find /boot/grub/stage1' in the terminal gives me (hd2,2) this time instead.

I'm really not sure what do do with it from here, and unfortunately I can't get it to connect to the internet through either of my wireless adapters, so...   I think I've rendered it completely unusable. :/

Any further help would be greatly appreciated.

---

### Post by rsambuca on 2007-02-19
I'm trying to help you here, but you keep changing things!  What happened to your ide drive?  Why did you not try swapping the order of your drives in the bios like I suggested a week ago?

---

### Post by st0n3cutt3r on 2007-02-19
I don't know how to change my drive order in my bios, and I don't have an IDE drive, they're all SATA.

My desired end result puts Ubuntu in the unallocated space on sdb(3), and sdc entirely storage space.  I only changed the configuration to test if installing a form of linux in the location that originally set up (and simulatneously ruined) grub would fix anything, but I can easily change it back, and I will do so now if there's no reason not to.

waiting for your reply.

---

### Post by rsambuca on 2007-02-19
Ok, let's try and figure out what is going on here.  What has me confused, (and probably your grub too), is the fact that you have all SATA drives and yet the grub find command came back with hd#,#.

I think it would help us a lot if we could find out for sure what order your drives are designated to boot in the bios.  When you turn your computer on, before grub loads, there is a time when you can enter your system bios by pressing a button.  With many computers it is Esc, sometimes F12.  It depends on your system.  Try your best to get into your bios and there will be a section regarding boot options, or boot order.  In there, you will find another option to select to see the boot order of your hard drives.

Don't worry about wrecking anything in your bios.  You won't hurt anything as long as you exit without saving (you will see this as an option). 

See what you can find out for your boot order.  If you can't figure out how to enter your bios, you will have to look it up on your PC manufacturer's web page.  What are your system specs and I can help you out.

---

### Post by st0n3cutt3r on 2007-02-19
One of my friends built my computer for me in August of 05, so I don't have a 'store bought' computer.  I *do* know that I have an nVidia nForce4 Mobo and an AMD athlon 64 chip. 

Here's what I was able to find out (that I thought might be useful)
According to the bios, my two optical drives are channel 0 Master and slave.
Then the hard drives are as follow:
IDE channel 2 Master HDT722525DLH380
IDE channel 3 Master WDC WD2500KS-00MJB0
IDE channel 4 Master none
IDE channel 5 Master ST3300622AS

Boot Priority: 
ch 3 WDC WD2500KS-00MJB0
ch 2 HDT722525DLH380
ch 5 ST3300622AS

Also, playing around with the boot options, I have determined that grub will boot properly and will actually boot Ubuntu (a first ever for my computer), AND it will boot the Vista boot manager.

I went into the BIOS again and changed the boot priority to:
ch 5 ST3300622AS
ch 3 WDC WD2500KS-00MJB0
ch 2 HDT722525DLH380

Now it boots grub properly, and I CAN use my computer again! :D

I still have grub 22 errors on the other two channels if I try to boot from them, I have 2 useless partitions on my drive with Ubuntu on it, and ubuntu is not where I want it.

Also, for some reason Ubuntu only recognizes windows vista on the desktop and will not read the windows XP files.  I'm not sure why.

AND I am unable to connect to the internet. (never have been with (k)ubuntu on my computer).  I use a Belkin wireless adaptor, but I also have a linksys one if that would work instead (so far as I've seen, neither will connect).

At the very least, my computer *is* functional again, better than it was this morning (before I attempted to reinstall linux) in that I no longer need to use the Live CD to boot my computer, which is nice.

If you are willing to help me further, I would greatly appreciate it (and wait to make any further changes until you instruct me to).  If not, then THANK YOU very much for all your help and patience!

---

### Post by rsambuca on 2007-02-20
Obviously just leave the bios set up so that it loads grub properly.  The purpose of the grub loader is to give you the boot options without having the hassle of entering the bios every time.

So just so we are clear, does every OS show up in your grub and will each one boot up?

As far as recognizing only Vista files and not XP, do you mean the XP partition doesn't show up at all when you are in Kubuntu?  If that is the case, you can probably just add the XP partition to your fstab file.  Follow the instructions at this site:  [[COLOR="Red"]Link[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows")

I am afraid I can't help you with the wireless part as I am on a desktop hardwired cable modem.  There are a lot of threads that you will find if you do a search on the subject.

Good luck, and keep us all posted on your success so you can help others.

---

### Post by st0n3cutt3r on 2007-02-20
I installed Ubuntu (not kubuntu) and on it's desktop only the vista partition shows up.

from grub I can (or at least the 1 time I tried, was able to) boot the first (standard) Ubuntu 6.10 option.

Also, the Vista/Longhorn (loader) will boot properly, and from there I am sure that I can start XP (haven't tested Vista, but I'm sure it would work if I tried).

I still don't have Ubuntu in the drive location that I want it in, and I have to have (so far as I know) those two 8mb partitions before it if I want it to continue running (something I'd rather not have).

Can you instruct me on how to install ubuntu in the location that I had it in (on the drive with the other OSs)?

---

### Post by rsambuca on 2007-02-20
Yeah, but it will have to wait.  I am off to bed - too tired!

---

### Post by st0n3cutt3r on 2007-02-20
ok, well just let me know when you can, and thanks!

---

