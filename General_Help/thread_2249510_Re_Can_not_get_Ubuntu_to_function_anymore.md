---
title: "Re: Can not get Ubuntu to function anymore"
date: 2014-10-22
forum: General Help
---

### Post by SAltonS on 2014-10-22
So I have been using Ubuntu 10.10 for the last couple of years.  Yesterday, tried to start the computer and it would not start up.  Have tried checking the memory, safety startup and everything else.  Have also tried to use the original Ubuntu CD and nothing.  Anybody have any ideas?

Since Ubuntu 10.10 is not supported anymore, I have tried several time to update to 12.04 STD but did not have any success.  Have been meaning to get help, but now this problem.

---

### Post by grahammechanical on 2014-10-22
You need to give information about your computer hardware, your partition layout, any other operating systems on the machine and a more informative description of what is wrong than "it would not start up." For all we know it could be the computer that is broken.

It would be better if you installed either Ubuntu 12.04 with support until sometime in 2017 or Ubuntu 14.04 with support until sometime in 2019. It is possible to upgrade from Ubuntu 10.10 but first you need a working OS. And it will be difficult because you will need to go to 11.04, then to 11.10 before you get to 12.04 and with 11.04 and 11.10 also having reached End of Life upgrading will not be easy.

So, if you wish to install a newer version of Ubuntu you need to explain in more detail what you mean by "nothing."

Regards.

---

### Post by SAltonS on 2014-10-22
Right now, I am using that computer, just running from the original CD in the "try it" section of the CD.  So I think the computer is working.  I will try and get you the information you asked for.

Have no idea where to look to find the information you need.  I know that the terminal window will give me that information with the correct command, but I do not know it off hand.

---

### Post by DogMatix on 2014-10-22
You could use Disk Utility to check the status of your hard drive.

---

### Post by SAltonS on 2014-10-22
And how do I do that?

When I start the computer with out the original startup disk, There are four options to start the computer.  I ran the memory check option and found no errors.

---

### Post by DogMatix on 2014-10-22
Trying to remember back to 10.10.

You need to launch Disk Utility select the harddrive in question click the Gears Icon and run Smart Tests.

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> When I start the computer with out the original startup disk, There are four options to start the computer.  I ran the memory check option and found no errors.

What are the other options?

---

### Post by SAltonS on 2014-10-22
You are dealing with door here!  You will have to spell it out.  Sorry.

I would have to shut down the computer to remember that.  And that is not going to happen until I get this problem fixed I hope.

Disk utility says that the hard drive is healthy.  Everything that is applicable is good.

When I click on the "check filesystem" it says the the "file system is not clean"

The hard drive is 160GB.

Am running the Disk_bench test now.

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> When I click on the "check filesystem" it says the the "file system is not clean"

Is this a dual boot with Windows?

---

### Post by SAltonS on 2014-10-22
I am running from the start up CD, so I do not think the computer can tell if the hard drive is partitioned.  But no, I did not partition the hard drive.  I have no use for windows.

Can you reset the computer to an earlier date?  Know you can do that in Windows.  Is there a command line for that?  I have been playing with the terminal screen, but have only been able to figure out the "sudo apt-get" command line.

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> I am running from the start up CD, so I do not think the computer can tell if the hard drive is partitioned.  But no, I did not partition the hard drive.  I have no use for windows.

In a terminal try

```


sudo lsblk


```

and post the results

---

### Post by SAltonS on 2014-10-22
Results are "command not found"

The disk_bench test is still running.  I would imagine it is taking too long.

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> Results are "command not found"

How about

```
sudo fdisk -l
```

---

### Post by SAltonS on 2014-10-22
disk /dev/sda: 160.0 GB.
255 heads, 63 sectors/tracts, 19452 cylinders
Units = cylinders of 16065 * 512=8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimal/optimal) 512 bytes / 512 bytes
Disk identifier 0x000626d3

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> The disk_bench test is still running.  I would imagine it is taking too long.

Bench tests can take a 'long' time.

---

### Post by SAltonS on 2014-10-22
Device          boot                     Start                   End                    Blocks          Id                 System
/dev/sda1         *                           1                  18658                  149864448     83                Linux
/dev/sda2                                 18658                19453                 6382593          5                 Extended
/dev/sda5                                 18658                19453                 6382592         82               Linux Swap/Solaris

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> disk /dev/sda: 160.0 GB.
255 heads, 63 sectors/tracts, 19452 cylinders
Units = cylinders of 16065 * 512=8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimal/optimal) 512 bytes / 512 bytes
Disk identifier 0x000626d3

I was expecting a partition table underneath this output.

---

### Post by DogMatix on 2014-10-22
> **SAltonS said:**
> Device          boot                     Start                   End                    Blocks          Id                 System
/dev/sda1         *                           1                  18658                  149864448     83                Linux
/dev/sda2                                 18658                19453                 6382593          5                 Extended
/dev/sda5                                 18658                19453                 6382592         82               Linux Swap/Solaris

Ah! there it is.

---

### Post by SAltonS on 2014-10-22
Sorry.  It took some time to type it all in.  Wanted you to have something to look at while I finished.

Just got an error message, but I messed up and cleared it before I could copy it.  Sorry.

---

### Post by Iowan on 2014-10-22
Please use the "Edit Post" to consolidate information. It makes the thread flow more smoothly.

---

### Post by SAltonS on 2014-10-22
Okay.  Thank you for the help.

---

### Post by DogMatix on 2014-10-22
Assuming you are booted from a live CD you could try in a terminal

```
fsck.ext4 -p /dev/sda1
```

If you get a warning about **SEVERE file system damage ** press 'n'. Don't do it.

---

### Post by SAltonS on 2014-10-22
Permission denied while trying to open /dev/sdal.  You must have r/w access to the file system or be root.

---

### Post by DogMatix on 2014-10-22
Maybe 

```
sudo fsck /dev/sda1
```

thats sda1 not sdal

---

### Post by SAltonS on 2014-10-22
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Devise or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

---

### Post by DogMatix on 2014-10-22
Try

```
sudo fsck -M /dev/sda1
```

This ignores mounted drives. Although I'm not sure we are going off in an irrelevant tangent now.


It's getting on for 2am in the UK now. I'll check this thread after work tomorrow but I need to get my head down now. Maybe someone else can pick it up. All the best SAltonS && goodnight.

---

### Post by SAltonS on 2014-10-22
Same response as the previous command line.

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Devise or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?


Thank you very much for all you help and efforts.  Have a great day when you wake up.  Thanks.

---

### Post by SAltonS on 2014-10-22
Could it be a virus?  Did I hear something about a Linux virus on the new a couple day ago?

---

### Post by SAltonS on 2014-10-30
So here is where I am at.  I am still using Ubuntu 10.10.  Computer has crashed.  When I start the the computer normally, the last line that show on the screen is "(3.465927) usb 2-2.3 new full speed USB device using uhci_hcd and address 3".

When I start it with my Ubuntu 10.10 CD I can get it to start and run but not shut down.  When I shut it down using Control+alt+print, the last line that is shown before the computer gets stuck is "Checking for running unattended - upgrades:init : rc main process (3341) killed by TERM signal.

When I start it using the CD there is an error that shows, "Glib Warning getpwuid_r () failed due to unkonwn user id".

Anybody have any ideas?

---

### Post by mörgæs on 2014-10-30
Threads merged. 

A 10.10 installation is not worth repairing. Back up your stuff and do a fresh install of 14.04.1 or 14.10. 

If a live boot of 10.10 does not work then try one of the versions mentioned above.

---

### Post by SAltonS on 2014-11-01
Understood.  But at the same time, I am learning a bunch.  Thank you.

---

