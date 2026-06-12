---
title: "performance issues - processor 100%"
date: 2007-05-24
forum: General Help
---

### Post by craig.brisbane on 2007-05-24
HI I need some help in understanding what is happening and how I can improve the performance of my computer :(. 

Background - I upgraded form 6.10 to 7.04 Ubuntu (in case that makes any difference from a new install) the computer is 2.4 celeron with 1gb ram. I am only running ubuntu 7.04 on the computer. 

Situation - when I have for example openoffice open editing a file and also fireworks (edit should be Firefox) open, if I open another link in a new tab the processor shoots to 100% and the computer freezes for a moment, then the web page loads.  I  have tried to modify the fstab file to see if the performance of the swap can be improved - someone in the past on this forum said that that the performance issue related to that. The fstab is below, you can see the change I made to the swap I have commented it out (#) and reverted back to the system default.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=bf774c43-eaa3-4951-b1ad-92fbc50b811b / ext3 defaults,errors=remount-ro,data=writeback,noatime 0
# Entry for /dev/hda3 :
UUID=6a73ee33-b008-486f-8426-e8d1bea8be42 /home ext3 defaults 0 2
# Entry for /dev/hda5 :
UUID=efc02c8d-0c68-4395-991f-8db1e9fd58c8 none swap sw 0 0
#/dev/hda5	swap	swap	pri=0	0	0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0


Any idea?  Tks
Craig

---

### Post by gustavoberman on 2007-05-24
don't know what fireworks is, but you have to first identify what is the process thats pushing up that processor use.
try with 'top' at the console
or 'system monitor' at the desktop

---

### Post by craig.brisbane on 2007-05-25
Can anyone offer me any other ideas or suggest a different forum to post - ta

---

### Post by snakedr on 2007-05-25
Ran across this url: [*http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml*]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml") on some settings that you can optimize. Check out the section on swappiness. That might help solve your problem.

How big is your swap file?

Also check the System Monitor to make sure the swap file is being recognized.

---

### Post by jfdill_2 on 2007-05-25
I suspect Firefox because my system is having similar lockups with 0 bytes of swap in use (1.5 GB of RAM) and CPU is not 100% used when it happens even though this is a basic Sempron box.  I'm watching "top" when it happens and md0_raid1 is using 5% CPU followed by Firefox then Xorg--it's interesting that even though the system seems "locked up" the text refreshes in gnome-terminal and I can sometimes click between windows, but I can't click on any menus or start up other applications or kill windows.  

To me, the "symptoms" such as they are feel a lot like when Internet Explorer hangs in Windows and I bring up Task Manager and I'm like, "Ugh, here we go again..."  In fact I can do the same fun thing that I do in Windows where that happens where I drag around the window that is in front of Firefox and "paint" with it leaving a psychedelic trail of window frames.  I'm just saying that because it's descriptive, and it was fun to say it, but it might not be technically relevant.

I'm going to play with Konqueror and Opera to confirm.  I didn't have this problem in Dapper or Edgy or Edgy with backports or Fiesty Fawn when it first came out, this started within the past few weeks.

I did have a past problem with Firefox (in Dapper I think) where animations in Firefox would play the frames as fast as possible at a very high frame rate with no delay between frames (how's that for redundant?) and that would max out the CPU, don't know if that could be at all relevant.

Update:  One thing that I am seeing now is various evolution processes (evolution-alarm-notify, evolution-exchange-storage, evolution-data-server) sucking up lots of CPU cycles even though I don't use evolution, maybe saved in my session somewhere, or something new.

Update:  Ahah!  I just got an e-mail from mdadm raid1 went into degraded mode, and the system has perked up now.  So, maybe there was indeed something wrong with the disk drive, didn't think of that because there was none of the usual DMA errors and chipset resets and whatnot.

---

### Post by craig.brisbane on 2007-05-26
Thanks for the advice - Could someone explain the following difference to me, as I am still getting use to linux - with regard to my swap file.

Through the system monitor I can see all the directories (like /home; /; /media/cdrom) but no swap. However with 'top' through the terminal I can see a reference to swap which says  
swap 1413680k total 0k used 1413680k free, 453516k cached (what does this mean?)

I the swap able to be used by my computer?

Thanks
Craig

---

### Post by owise1 on 2007-05-26
Hi Craig,

I have attached a snapshot of my processor load / swap etc from system monitor.  Sawp get very little use on this machine as I have a reasonable amount of memory (I think).  Not the spikes in processor load when I stated a new window in firefox and started other application.

Provides a bit better view of what is happening than top.

cheers

---

### Post by pmg on 2007-05-26
> Through the system monitor I can see all the directories (like /home; /; /media/cdrom) but no swap. However with 'top' through the terminal I can see a reference to swap which says
swap 1413680k total 0k used 1413680k free, 453516k cached (what does this mean?)

Technically you're not seeing "directories" in System Monitor, but rather filesystems.  The directories listed are the dirs where the filesystems are mounted.  Swap isn't a filesystem.  Linux can swap either to a file in a filesystem, or to a partition set up for swap (or to a logical volume if LVM is running.)  Using a partition is the more common than a file as it's more efficient, and also that way the space is reserved for swap and can't be used by anything else.  Linux only starts to use it when memory (i.e. RAM) gets overcommited, so if you have enough memory that everything fits swap isn't used at all.  The "swap .... 0k used" tells us that's the case on your system, at least at the time you looked at it.

Getting back to your initial problem: is the CPU really pegged at 100% when you look at top and System Monitor (or were you just assuming it was because of the slow performance.)  It might help if you copy the top three lines from top when you see the problem.

---

### Post by juantovarm on 2007-05-26
Try this, it sounds very familiar to me:

High CPU usage
[https://launchpad.net/bugs/54684](https://launchpad.net/bugs/54684)

you should add this line to your /apt/get/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

and download these packages:

libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnomevfs2-bin

---

