---
title: "cursor freezes have to reboot"
date: 2015-06-23
forum: General Help
---

### Post by Rolandl on 2015-06-23
While working on-line everything suddenly slows down and the cursor freezes. keeps happening. I reboot and a message says Ubuntu 15.04 Gnome has experienced an internal error. Could someone tell me what software to use to find the problem and correct it? And If I may ask another question here, A software to keep track of the cpu usage like process explorer does in MS Windows? Thank you.

Is this meaningful?
total system RAM is 1431 MiB Free  34%
swap total RAM is 1471 MiB   Free  98%

---

### Post by Ty_Scheun on 2015-06-23
Probably due to the amount of RAM that you have. Which PC are you using? Are you using any intensive applications? 1GB is very low RAM. Installing RAM would help alot. And replacing your hard drive has found to help too.

---

### Post by Mike_Walsh on 2015-06-23
Hallo, Rolandl.

Can't quite remember what it's called off the top of my head, but I believe 'gnome system monitor' is what you want. It's available through the Software Centre; open the SC, and enter 'gnome system monitor' in the search box, top right corner. The system will search and find it for you. Either click for more information, or install straight away.

I agree with Ty_Scheun. I run Xubuntu on a 12-yr old Dell laptop with a Pentium 4 & I GB RAM; it's.....leisurely, would be a polite way of putting it! Xubuntu, however, doesn't need 3D acceleration for the graphics.....which Ubuntu does. I don't know about Ubuntu Gnome, so can't comment. 

I can't increase my RAM as the mobo is 'maxed out'; but installing additional memory is one of the easiest ways there is of increasing system performance.....an extra 1 GB would make a** lot** of difference, believe me.

My 10-yr old desktop has 4 GB of RAM, so the problem doesn't arise.


Regards,

Mike.

---

### Post by Rolandl on 2015-06-23
I have system monitor okay. I see opening it it shows everything 'normal' right now under PRIORITY and my comp is running efficient. will keep a check on it.

Thanks very much fellas. will take your suggestions.

freezing and crashing. How can I check the condition of the hard drive files?

---

### Post by Bashing-om on 2015-06-27
Rolandl; Hello;

> **Rolandl said:**
> freezing and crashing. How can I check the condition of the hard drive files?

Verification of the file system:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo fdisk -lu ##to identify your partitions
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```

Next perhaps might behoove you to check the health of the hard drive and run a SMART test from 'disk-utility'.

[INDENT][INDENT][INDENT]safety is no accident
[/INDENT][/INDENT][/INDENT]

---

### Post by Rolandl on 2015-06-30
I checked HD files with nemtest86 and report said no errors. (took an hour and a half so I guess it's a good check)
I installed another gig of RAM, now have 1.9 gigs. arrow hasn't froze again so far. 
but it is crashing sometimes and on restart says 'ubuntu has experienced an internal error'. 
What would likely be causing this?

What would a SMART test tell me that nemtest doesn't?

---

### Post by Bashing-om on 2015-06-30
Rolandl; Well ....

Like this:
memtest86 checks the ram (memory)  installed ;
e2fsck checks/repairs the file system (software);
smartctl  checks the physical condition of the hard drive.

If any one fails, the whole system fails.

[INDENT][INDENT]all together now
[/INDENT][/INDENT]

---

### Post by Rolandl on 2015-07-01
I went here: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools), and did everything it suggested but terminal said 
smartctl: command not found.

Do I need Synaptic?

---

### Post by Bashing-om on 2015-07-01
Rolandl; Well ;

Then !

```

sudo apt-get install smartmontools

```

will put is back on the right track.

---

### Post by Rolandl on 2015-07-04
I got smart ok then tried the commands -p -n and -c but it said 'command not found'.

---

### Post by llamabr on 2015-07-04
Looks like you must install it first:
brock@silver:~$ apt-cache search smartctl
smartmontools - control and monitor storage systems using S.M.A.R.T.
gsmartcontrol - graphical user interface for smartctl
idle3-tools - change the idle3 timer of recent Western Digital Hard Disk Drives
brock@silver:~$

---

### Post by Bashing-om on 2015-07-04
Rolandl; Well ..

Not looking over your shoulder at your terminal, I can not say what is not taking place.
Have you consulted the 'manual' to know what each argument to "smartctl" does ? And the proper syntax is invoked in the terminal commands ?
```

man smartctl

```

If :
a) the memory checks good
b) the file system checks good
c) the hardware checks good

Then
One would highly suspect a configuration issue at fault that the system misbehaves .

In that event one goes looking into the various system logs to look at what the system might report for error conditions.

[INDENT][INDENT]reading is good
[/INDENT][/INDENT]

---

### Post by Rolandl on 2015-08-26
I entered sudo fsckfsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

I wonder why it cannot check the disk?

memory is 1.9 GiB
page is still freezing. arrow won't move. light is on on the usb mouse.

---

### Post by Bashing-om on 2015-08-26
Rolandl; Yikes !

If you are running a file system check from within the installed operating system .. Ouch, bad things can happen !
I hope the operating system is protecting you.
To conduct the file system check the file system MUST be UN-mounted such as it is not pre-occupied and in use.
Insure that the swap function is turned off :
```

sudo swapoff -a

```
Then run the suggested file system utility.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Rolandl on 2015-08-26
> 
Thanks for that. I forgot about that. I loaded the original disk but couldn't find memtest86.
> 

---

### Post by kurt18947 on 2015-08-26
> **Rolandl said:**
> Thanks for that. I forgot about that. I loaded the original disk but couldn't find memtest86.

Bear in mind that memtest86 tests DRAM, it doesn't do anything at all for the file system on the hard drive. If you're running Ubunt-Gnome, I believe you have the application "Disks" installed by default. If you start that, you should see your drives along the left side. In the larger right panel you should see the active hard drive and its partitions. You may see a message that SMART is not enabled. If you click the little gear in the upper right corner, there should be an option for to enable SMART data and self tests. I have a button in the upper right corner of that windows that defaults to 'off'. If you click that button, you'll be prompted for an administrative password. After entering the SUDO password, you'll get several lines regarding disk status and an options for a self-test. 

This won't tell you if your file system has problems, just whether the disk seems to be healthy or not. You'll still need to run e2fsck to check file system integrity. There is a command or commands that once executed will cause e2fsck to run upon a reboot. I don't recall what those command(s) are. I think e2fsck is similar to DOS/Windows 'chkdsk' command.

---

### Post by Rolandl on 2015-10-08
Everything has been going okay for past month except for web page freezing at times. I was able to correct it until yesterday. now rebooting doesn't help. decided to re-install from Disk. Now the Ambience background opens but desktop doesn't. have tried 3 x. I re-installed without partitioning again. I wonder if something got corrupted or, a virus is possible? on the install disk doesn't show how to check the hard drive. I wonder too, there's only 1.9 Gigs of Ram. do I need more? What should I do?

---

### Post by Bashing-om on 2015-10-08
Rolandl; Hey !

If it were me I would check the physical health of the hard drive.
[https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T).
```

sudo smartctl -a /dev/sda

``` where 'sda' is the 1st hard drive .
Any possible issues indicated here I would then do more intensive tests:
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)
[https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results](https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results)
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

Make sure of the integrity of the .iso file :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Make sure of the burn:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
( there is a quick check in the live environment's boot options menu )

[INDENT][INDENT]then again
[INDENT][INDENT][INDENT]never hurts to run a file system check/repair
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Rolandl on 2015-10-08
> 
How does this look:

sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
      378819 inodes used (3.93%, out of 9641984)
         321 non-contiguous files (0.1%)
         311 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 330240/66
     3738902 blocks used (9.70%, out of 38564864)
           0 bad blocks
           1 large file

      260900 regular files
       52250 directories
          57 character device files
          25 block device files
           0 fifos
           0 links
       65575 symbolic links (48420 fast symbolic links)
           3 sockets
------------
      378810 files
> 

---

### Post by Bashing-om on 2015-10-08
Rolandl; Well ..

Good, that there are no reported problems by the file system check. But, that check will not relate directly to hard drive health.
To be confident, I would run the SMART utility.

[INDENT][INDENT]nothing like a confidence factor
[/INDENT][/INDENT]

---

### Post by Rolandl on 2015-10-09
I entered this: sudo smartctl -s on /dev/sda
response: " command not found"

---

### Post by Rolandl on 2015-10-09
> 
I re-installed a second time now. more problems than before with the installation.

Thank you all for trying to help. Think I will try Windows again see if I have as many issues.
> 

---

### Post by Bashing-om on 2015-10-09
Rolandl; Humm ..

OK, is the tool installed ? I can accept that it is not installed in each and every release .
```

dpkg -l smartmontools

```

smartctl is a part of that package, to install:
```

sudo apt-get install smartmontools

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

