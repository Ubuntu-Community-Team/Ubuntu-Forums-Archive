---
title: "ubuntu-16.04 factory installed by dell boot error gave up waiting for root disk"
date: 2019-07-17
forum: General Help
---

### Post by cygnus-x12 on 2019-07-17
[COLOR=#242729][FONT=inherit]Hello and thanks for reading.

I have a dell XPS 5530 I bought late last year with Ubuntu 16.04 pre-installed. It was working fine but I have not opened the laptop for about 2 months and when I tried today I was greeted with a RAM disk prompt.  After doing some research I booted in recovery mode and saw that the kernel could not find the root device.  The message said : UUID=... was missing. I adjusted the delay to wait to 100 seconds but that did not do the trick. I also tried booting with older kernels with no luck.  My main Linux experience is primarily old school meaning I am used to ext2-ext4 file systems and older Slackware/centOS distros and I haven’t been able to keep up with the latest trends so the uuid message and possible encrypted file system stuff is new to me.

[/FONT][/COLOR]
[COLOR=#000000][FONT=inherit][COLOR=#242729][FONT=Arial][FONT=inherit]This laptop does not have a built in CD so I will need to get an external one or try and get a live Linux district on a USB stick which I don’t have at the moment. [/FONT]
[FONT=inherit]I ran the system tests and it looked good. Short of taking the ssd drive out and trying to mount it on another computer how can I tell if it’s still good ? [/FONT]
[FONT=inherit]Dmesg did not list a uuid value within. This is my first experience with Ubuntu.  I have been enjoying my experience so far.[/FONT]
[FONT=inherit]Any help is appreciated.[/FONT]
Thanks,
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by yancek on 2019-07-18
Is the UUID missing/incorrect?  Use a live system and run the command:  sudo blkid to find if the UUID mentioned in the error message shows.  You will need to compare the UUID's so that the one with the / root filesystem is the same as show in /etc/fstab and in your grub.cfg file.

Do you recall the original "RAM" disk error?

Simply not using the machine for a period of time is highly unlikely to give that error?

---

### Post by cygnus-x12 on 2019-07-19
Thanks again for the assistance.  I will have some time on Friday to get the RAM disk error message but won&#8217;t be able to try a live system until next week sometime.  

I agree that not using a machine should should not cause this but I might not have turned off the machine and simply closed it which I think should hav suspended it for the long period of time.  That should not matter either but it is not the same as shutting it down properly.

---

