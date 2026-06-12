---
title: "[SOLVED] /dev/sdb becomes /dev/sdc after Suspend. Why?"
date: 2008-07-10
forum: General Help
---

### Post by KenBW2 on 2008-07-10
My eeePC has an SD Card reader which is /dev/sdb, and mounted to /media/disk at boot, as per fstab. The card has 2 partitions on it: 6.5GB fat32 (/dev/sdb1) and 1GB linux-swap (/dev/sdb2).

If I Suspend, I wake it up to find that it remounts the SD Card to /media/disk-1. I just found out this is because the SD Card is now placed at /dev/sdc. 'sudo mount /dev/sdc1 /media/disk' works fine (although it lists "disk" twice in Nautilus' Places bar).

Why is it doing this? And is there a solution, since I think this could be why it's not waking from Hibernate.

---

### Post by danwood76 on 2008-07-10
This is probably caused by a hal or kernel bug.

Basically after the suspend it wakes up and tries to rediscover devices, as card readers are generally USB devices they are switched off on suspend and re initialised on resume.
I would bet that dmesg shows it re finding the SD card and re assigning it sdc.

I would bet the reason why it wont hibernate is that your swap will contain the RAM data and as that is on an SD card the initramfs wont locate it (probably due to lack of a driver in the initramfs) and so the kernel wont find a resume image.

---

### Post by KenBW2 on 2008-07-10
Thanks for your reply

You're right, dmesg does show it being assigned to sdd (this is after a second Suspend/Resume)

```

[    8.196192] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[    8.202299] ath_pci: switching per-packet transmit power control off
<snip wifi0 stuff>
[    8.464121] sd 4:0:0:0: [sdd] 15728640 512-byte hardware sectors (8053 MB)
[    8.465932] sd 4:0:0:0: [sdd] Write Protect is off
[    8.465947] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[    8.465954] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[    8.476102] sd 4:0:0:0: [sdd] 15728640 512-byte hardware sectors (8053 MB)
[    8.480096] sd 4:0:0:0: [sdd] Write Protect is off
[    8.480116] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[    8.480123] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[    8.480260]  sdd: sdd1 sdd2
[    8.486730] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[    8.486879] sd 4:0:0:0: Attached scsi generic sg1 type 0


```

I guessed it wasn't working from Hibernate because of the SD Card not being where it was beforehand.

The question is - is there anything I can do about it?

---

### Post by KenBW2 on 2008-07-10
*bump*

---

### Post by danwood76 on 2008-07-10
I think this may actually be caused by the system not unmounting the drives when it suspends see this I found:
[http://forum.eeeuser.com/viewtopic.php?id=16619](http://forum.eeeuser.com/viewtopic.php?id=16619)

It might help you.

---

### Post by KenBW2 on 2008-07-10
That link is for the default Xandros OS, not Xubuntu...

---

### Post by danwood76 on 2008-07-10
Ok, Xandros is based off debian so I thought it might be similar but after a full read I guess not.

What you might be able to do is add the module that loads the SD card to the ACPI whitelist which will keep it in the kernel during a suspend.
This should stop it from re loading but you will need to work out which module is doing it.

So first list all the modules with this command:
```

lsmod

```
I think the particular module is usb_storage (verify this is loaded on your system) we can then add this to the suspend whitelist to see if this fixes the issue.
It should stop it from unloading the drives but it might cause other issues, its worth a shot though it cant hurt.

First open the acpi config file for editing in gedit:
```

sudo gedit /etc/default/acpi-support

```
Scroll down and you will see
```

MODULES_WHITELIST=""

```
(yours might contain something between the speechmarks)
Add the usb_storage to it so it looks:
```

MODULES_WHITELIST="usb_storage"

```
Save the file and reboot and then test.
If it doesnt work check dmesg again to see if the output is different.

---

### Post by KenBW2 on 2008-07-10
Thanks for your continued help

I don't really know what I'm looking at with lsmod.

I've pasted the output to
[http://www.nomorepasting.com/getpaste.php?pasteid=17859](http://www.nomorepasting.com/getpaste.php?pasteid=17859)
instead of posting a huge list here.

Is that right?

---

### Post by danwood76 on 2008-07-10
It looks like the module 'usb_storage' is loaded as I thought, this is the module that controls USB external drives as your SD card will be recognised.

Have a go at adding it to the acpi suspend whitelist as I described and post your results.

---

### Post by KenBW2 on 2008-07-10
Problem is still there :(

::EDIT::
It did have a positive effect. See [Post 12]("http://ubuntuforums.org/showpost.php?p=5361014") for details

---

### Post by MasterXandrex on 2008-07-10
I don't really have a solution, but I would like to mention that I have two SATA hard drives that have this problem. Sometimes after reboot (not suspend) they simply swap.


Any ideas on that?


Thanks,

Xan

---

### Post by KenBW2 on 2008-07-10
After the aforementioned fix I find, unlike before, that if I 'umount /media/disk & sudo swapoff -a' before I suspend the SD Card is still /dev/sdb when I reawake. Hibernate still doesn't work

Now to figure out how to do it without needing this step...

Thanks for your help :)

---

### Post by danwood76 on 2008-07-11
Well you can make a script that runs during suspend and upon resume that does these steps for you.
Obviously this is more of a work around as opposed to a true fix but if it gets the job done then its obviously the way to go.

The suspend and resume scripts are in the following dirs:
/etc/acpi/suspend.d
/etc/acpi/resume.d

I will have a play and work out which is the best priority to have this script at, (I can mount an SD volume and test)
If you do it in the wrong place swapoff may not function.

---

### Post by danwood76 on 2008-07-11
> **UbuntuUser3859 said:**
> I don't really have a solution, but I would like to mention that I have two SATA hard drives that have this problem. Sometimes after reboot (not suspend) they simply swap.


Any ideas on that?


Thanks,

Xan

Using UUID's as opposed to the block device IDs will solve this issue.
The issue KenBW2 is having is to do with the SD card being re initialized after suspend and not properly turned off or kept in the loop, so is unrelated to your problem.

To get the UUIDs of devices do:
```

sudo blkid

```

---

### Post by KenBW2 on 2008-07-11
I tried adding the scripts to the directories you suggested. I just copied the aliases I had set up:

alias presuspend='umount /media/disk & sudo swapoff -a'
alias postsuspend='mount /media/disk & sudo swapon -a'

so the scripts were:

```

#!/bin/sh

# Unmount SD Card before Suspend.Otherwise /dev/sdb becomes /dev/sdc/d/e etc. Source: http://ubuntuforums.org/showthread.php?t=855289&page=2
umount /media/disk & sudo swapoff -a

```

```

#!/bin/sh

# Mount SD Card before Suspend.Otherwise /dev/sdb becomes /dev/sdc/d/e etc. Source: http://ubuntuforums.org/showthread.php?t=855289&page=2
mount /media/disk & sudo swapon -a

```

respectively.

This didn't work though. I tried with a few variations: /dev/sdb instead of /media/disk, and removing the sudo but neither worked.

Any idea why?

---

### Post by danwood76 on 2008-07-11
After doing a bit of reading it seems that hardy now uses pm-utils to do its suspend (cant seem to find any hardy docs about it???) which means you need to create a different type of script in a differnt place.

They are now in /etc/pm/sleep.d and have a slightly different file format as described below (in how-to format)

Ok so first create our new script:
```

sudo gedit /etc/pm/sleep.d/unmount.sh

```
The file needs to contain this style:
```

#!/bin/bash
case $1 in
    hibernate)
	;;
    suspend)
        umount /media/disk & sudo swapoff -a
        ;;
    thaw)
        ;;
    resume)
        mount /media/disk & sudo swapon -a
        ;;
esac

```
Then make the script executable:
```

sudo chmod a+x /etc/pm/sleep.d/unmount.sh

```
Then when suspending it should unmount /swap and your /media/disk and resume should do the opposite.
Hopefully this will solve your issues.

---

### Post by KenBW2 on 2008-07-11
> 
cant seem to find any hardy docs about it???

Well, documentation was never Linux's strong point...

Sorry - I'm still on Gutsy on my laptop.
I assume I can follow the instructions apart from which folder to put it in? Or does acpi use a different format for the scripts?

Thanks

---

### Post by danwood76 on 2008-07-11
I think gutsy uses pm-utils aswell so it should work the same.
That might be why I couldnt find any hardy docs on it.

Try it out, if the /etc/pm/sleep.d directory doesnt exist then maybe its not the same.

---

### Post by KenBW2 on 2008-07-11
Nope, no /etc/pm/ directory. Might be because it's Xubuntu, not Ubuntu (see signature). I'll try the format you suggested in the acpi dir's

EDIT:

I just looked at one of the existing scripts: 
```

#!/bin/sh

#prevent acpid from processing any following events
touch /var/lock/acpisleep


```

Looks like it doesn't use any fancy formats.

---

### Post by KenBW2 on 2008-07-11
Oh well unless you/anyone else has some bright ideas looks like aliases will be the solution. I din't mind, just would've been easier to have it automatic. Hmmm... I could add the suspend command to the alias... Do you know what it is?

---

### Post by danwood76 on 2008-07-11
Well if it still uses the older system then it should run those scripts.
To verify this you can add your lines to the bottom of one of the existing scripts and see if they get executed.
To make it easier to see you could just add a 'touch /home/username/foo' and it should create the foo file in our home.

When you add scripts to the /etc/acpi/suspend.d directory you need to give them a priority as the other scripts are setup with a number infront of the script name, it also needs to be executable.
To have it executed first (as I expect you should) you should name it something like '04-unmunt.sh' and then also 'chmod a+x' it.

The lower the number infront the sooner it gets executed and as you said it works if you unmount them and then suspend you should try and execute the script as soon as you can in the suspend cycle.

---

### Post by KenBW2 on 2008-07-19
I was a step ahead of you with the adding it to the bottom of another idea :), and it worked. I tried the chmodding but it hasn't had an effect.

OK, so the solution to the problem for anyone browsing this thread later:

*where I put /dev/sdb or /media/disk, change as appropriate*
**1) Testing unmount of your SD Card**
Manually unmount the SD Card:
```
umount /dev/sdb & sudo swapoff
```
When you reawake, remount it
```
mount /media/disk & sudo swapon -a
```

**2) Setting up an alias**
If that works fine, set up an alias to make it easier to do:
```
gedit .bash_aliases
```
Make two new lines containing the following:
```

alias presuspend='umount /media/disk & sudo swapoff -a & sudo /etc/acpi/sleep.sh'
alias postsuspend='mount /media/disk & sudo swapon -a'

```

**3) Suspending in future**
Just type to suspend your computer:
```
presuspend
```
And when you reawake:
```
postsuspend
```

**Notes**
- I've tried making a Panel launcher for this, but for some reason it won't work. Maybe someone else can help.
- Make sure you close all applications which are using the SD Card. In my experience Rhythmbox needs to be closed, but gedit/nautilus and some others don't



**Future advancements**

I tried the method described above by danwood76. This hasn't worked for me; the SD Card becomes /dev/sdc again, as if nothing has changed. But this is how far I got:


*where I put /dev/sdb or /media/disk, change as appropriate*
**1) Testing unmount of your SD Card**
Manually unmount the SD Card:
```
umount /dev/sdb & sudo swapoff
```
When you reawake, remount it
```
mount /media/disk & sudo swapon -a
```

**2) Preparing the next stage**
If this works, put your PC to sleep manually, allowing to see which scripts are being run:
```
umount /media/disk & sudo swapoff -a & sudo /etc/acpi/sleep.sh
```
Some output will be, er, output. Look for a script which is being run.

**3) Making the change permanent**
After you have found a script which is being run, add it to the bottom of that file. When this file is run, it should run the unmounting part, so System > Quit... > Suspend should work as normal.



Many thanks to danwood76 for all your help on this matter - at least I now have a way to Suspend at all without screwing things up :)

---

### Post by baustromverteiler on 2010-08-31
deleted cause solution stopped working ...

---

