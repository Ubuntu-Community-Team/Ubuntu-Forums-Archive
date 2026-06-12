---
title: "I think Ubuntu is killing my hard drive"
date: 2016-09-25
forum: General Help
---

### Post by tonma on 2016-09-25
Hello,

I'm using laptop with dual boot with Windows 10 and Ubuntu 16.04. Whenever I use Ubuntu, the hard drive does not stop making the hard drive needle noise, as if it's always moving.. when I switch to Windows it's silent.

What can I do?

Thanks!

---

### Post by speartip on 2016-09-25
You really haven't given us much to work with here.
Your full laptop specification would be helpful. Particularly Graphics Card, & whether or not you're using the open source or proprietary Graphics Driver.
With more info, you're likely to get more replies.

---

### Post by 5hutd0wn on 2016-09-25
Yea also is it a new hdd?  Internal/External?  Also hard drives don't have a needle are you shure its not the fans?   Run some diagnostics and see if the Rpm is different on Ubuntu.  Im a noob here but with that data the best i think can be said is reinstall and see if its still a problem.
If u have date u need to save shrink the partition and make a new one about 30GiB to test.  If the problem persists then im clueless.

---

### Post by dragonfly41 on 2016-09-26
You could try launching Applications > System Tools >  System Monitor > 
go to Processes tab and start closing some processes .. [End Process] .. to see if you can find a process causing this noise.

---

### Post by tonma on 2016-09-26
HDD is 1.5 years old 5400 rpm.
The graphics are dual AMD  R5 M230 and Intel HD 4600, but I disabled the AMD in BIOS (I selected only "UMA Graphics" instead of "Switchable Graphics", because the AMD is really bad, and only causing problems, even with WIndows, where the support is 'better' for the graphics)

*I checked and the driver is i915 (does that make sense?) - is this the right driver for HD 4600?

About closing processes: there are too many I don't know whether it's safe to just end them without causing Ubuntu to crash?

*The needle just keeps moving, even while browsing right now. Could that also be related to the "swap" feature on Linux, that uses HDD in addition to RAM? Then maybe I should disable it?

---

### Post by ventrical on 2016-09-26
> **tonma said:**
> HDD is 1.5 years old 5400 rpm.
The graphics are dual AMD  R5 M230 and Intel HD 4600, but I disabled the AMD in BIOS (I selected only "UMA Graphics" instead of "Switchable Graphics", because the AMD is really bad, and only causing problems, even with WIndows, where the support is 'better' for the graphics)

*I checked and the driver is i915 (does that make sense?) - is this the right driver for HD 4600?

About closing processes: there are too many I don't know whether it's safe to just end them without causing Ubuntu to crash?

*The needle just keeps moving, even while browsing right now. Could that also be related to the "swap" feature on Linux, that uses HDD in addition to RAM? Then maybe I should disable it?

That's a real old drive, 5400rpm, and you can expect zeigiest and other programs to cause the heads to make some noise.

Regards..

---

### Post by tonma on 2016-09-27
Guys, I've found some articles, this for example: [http://www.computercorrect.com/2011/operating-systems/linux/ubuntu/fix-for-constant-hard-drive-clicking-in-ubuntu/](http://www.computercorrect.com/2011/operating-systems/linux/ubuntu/fix-for-constant-hard-drive-clicking-in-ubuntu/) that shows that more people are experiencing that.
Could you please help me by taking a look and tell me if it is safe to follow the instructions there? there are some commands I've never seen before

Thanks!

---

### Post by colin.p on 2016-09-27
I don't know how long you have had 16.04 on your system, but I know for awhile after updating from 14.04 (not a clean install), I noticed more HD activity. After having it now for over a month, the HD has settled down nicely and System Monitor doesn't show anything overtaxing the system. I did read that article you mentioned and I have bookmarked it and if I ever run into that issue, I'll try their advice.

---

### Post by dragonfly41 on 2016-09-27
It could be that your entire file system is being indexed by some application running in background.

---

### Post by tonma on 2016-09-28
So what are my possible fixes as an Ubuntu/Linux novice? It just won't stop

---

### Post by dragonfly41 on 2016-09-28
Does it stop if you create a new Ubuntu user account .. say "guest" .. and log out and log in to guest account?

---

### Post by tonma on 2016-09-30
Nope :( It's just so annoying, I have to keep using Windows? Or I should try the things mentions in the link I gave?

---

### Post by dragonfly41 on 2016-10-01
Referring to the link you gave, start by running the commands: 
```
man hdparm
``` 
and next ...
```
hdparm -help
```
which together will explain more what that hdparm command does (or can do).

Take note of the "dangerous" advice in the help output and so do not depart from the advice.
i.e. only use the argument -B as explained in the article.
 
Provided that you follow closely to the instructions in the above article you should be safe.

Start by running the basic test command to see if the noise stops.

If it does stop it will probably resume next time you reboot. 
So only then need you progress to second stage of editing internal files which configure hdparm.

Caveat: I write this as someone who has not experienced this disk noise although my disks are old.
Personally, I would follow the advice in the article.

---

### Post by tonma on 2016-10-01
*But the manual doesn't say what does 254 or 255 mean, and how I can revert back to the first state?

I tried both sudo hdparm -B 254 /dev/sda and sudo hdparm -B 255 /dev/sda.. The noise did not stop, now how can I tell what is 255 or 254, and what was m first state?

And how to stop that noise? :confused:

Edit: The sound is like in this video:

[https://www.youtube.com/watch?v=n9obzgmWrlM](https://www.youtube.com/watch?v=n9obzgmWrlM)

---

### Post by dragonfly41 on 2016-10-01
This is the output of man hdparm .. -B option
```

       -B     Get/set Advanced Power Management feature, if the drive supports
              it.  A  low  value  means aggressive power management and a high
              value means better performance.  Possible  settings  range  from
              values  1  through  127 (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).  The highest degree
              of  power  management  is  attained with a setting of 1, and the
              highest I/O performance with a setting of 254.  A value  of  255
              tells  hdparm to disable Advanced Power Management altogether on
              the drive (not all drives support disabling it, but most do).

```

This suggests that not every drive supports the option..

For further diagnostics of your drive ...
Test is you have smartctl installed by running ```
man smartctl
```

More information found here .. [www.smartmontools.org]("http://www.smartmontools.org")

```

       smartctl controls the Self-Monitoring, Analysis and Reporting  Technol&#8208;
       ogy  (SMART)  system  built into most ATA/SATA and SCSI/SAS hard drives
       and solid-state drives.  The purpose of SMART is to monitor the  relia&#8208;
       bility  of  the hard drive and predict drive failures, and to carry out
       different types of drive self-tests.  smartctl also supports some  fea&#8208;
       tures  not  related  to  SMART.  This version of smartctl is compatible
       with ACS-2, ATA8-ACS, ATA/ATAPI-7 and earlier standards (see REFERENCES
       below).

```


If not go to Ubuntu Software Centre (or Synaptic Package Manager if you have that installed) to install

smartmontools   ... control and monitor storage systems using S.M.A.R.T.

optionally ...
gsmartcontrol     ... graphical user interface for smartctl


You can then further inspect your drive by launching the GUI from command

```
gsmartcontrol
```

or running smartctl directly from command line.

Note that it is possible that your drive may not be S.M.A.R.T. enabled, but if it is only 1.5 years old then it should be.


Or just run the command ```
sudo smartctl -i /dev/sda
```

and you could post the result here for us to view (we might glean more information).

---

### Post by buzzingrobot on 2016-10-01
I'm not sure what the OP means by "hard drive needle".  But, the Linux kernel uses a memory allocation algorithm that sees it attempt to retain code in RAM once it is read from a drive. (So does the Windows kernel, using its own techniques.)  Reason:  It's orders of magnitude faster to read from RAM than a physical drive. So, seeing a busy GUI tool that claims to visually represent that IO activity isn't a bad thing. That doesn't necessarily mean the physical drive is in constant use.

If a drive is *audibly* in constant use for routine non-disk intensive activities, it might be the OS has been installed in a partition that's too small. Even routine activity generates files and data that need to be written to a drive. (Browsing can create a large amount of this.)  This can prompt increased disk activity as data on a drive are reshuffled to accommodate the new files.

Use of the swap partition in Linux is reasonably sophisticated. Disabling it altogether, especially in systems with low RAM, isn't smart.  You can play with settings to attempt to adjust how and when it is used but results can vary from user to user depending on their mix of applications.

---

### Post by tonma on 2016-10-04
> **buzzingrobot said:**
> I'm not sure what the OP means by "hard drive needle".  But, the Linux kernel uses a memory allocation algorithm that sees it attempt to retain code in RAM once it is read from a drive. (So does the Windows kernel, using its own techniques.)  Reason:  It's orders of magnitude faster to read from RAM than a physical drive. So, seeing a busy GUI tool that claims to visually represent that IO activity isn't a bad thing. That doesn't necessarily mean the physical drive is in constant use.

If a drive is *audibly* in constant use for routine non-disk intensive activities, it might be the OS has been installed in a partition that's too small. Even routine activity generates files and data that need to be written to a drive. (Browsing can create a large amount of this.)  This can prompt increased disk activity as data on a drive are reshuffled to accommodate the new files.

Use of the swap partition in Linux is reasonably sophisticated. Disabling it altogether, especially in systems with low RAM, isn't smart.  You can play with settings to attempt to adjust how and when it is used but results can vary from user to user depending on their mix of applications.

Thanks,

but I don't think I disabled SWAP , I only did hdparm 255 and 254 - which didn't help.. So it might happen because, as you said my Ubuntu partition is too small:o

---

### Post by oldfred on 2016-10-04
While noatime or relatime are often suggested for SSD to reduce writes you can also try that.
Linux tries to load apps into RAM, so do you have enough RAM that swap would not be used much. Then it may be writing update times and noatime can reduce that.
       
Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,errors=remount-ro 0       1 

           
 
Info on trim and ext4 without journal, ext2 does not support TRIM, with newer SSDs relatime a reasonable alternative to noatime and works with some apps that need timestamps like mutt
[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)

---

### Post by Pitero on 2016-10-05
Perhaps it's something related with that how swap file is configured in Ubuntu? Newer version usually has higher memory requirements. How much RAM do you have?

Please have a look on the following link [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 

You can do:
 
sudo gedit /etc/sysctl.conf 

and find/add

vm.swappiness=10  #from 0 to 100

the lower value the less frequent system should use swap file, at the beginning you can even try with zero value

---

### Post by megamania on 2016-10-05
Check if the "tracker" process is running (run "top" from the terminal). If it is running, it's likely that your hard disk is being indexed and so is constantly used.

[https://wiki.ubuntu.com/Tracker]("https://wiki.ubuntu.com/Tracker")

---

