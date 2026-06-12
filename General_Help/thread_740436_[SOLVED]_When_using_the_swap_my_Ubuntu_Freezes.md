---
title: "[SOLVED] When using the swap my Ubuntu Freezes"
date: 2008-03-30
forum: General Help
---

### Post by linuxd00 on 2008-03-30
I have a thinkpad X31 laptop with 1GB ram. A swap partition has 666MB

When using firefox (which oftens seem to leak memory and use tons of ram) i often quickly reach 1GB... as soon as this happens linux seems to start to swap. The HD Led is on all the time... but ubuntu freezes then. open windows will turn black and white one after another and nothing works anymore.

i cant do nothing more. I cant even log in to console and pkill Firefox.

sometimes im lucky and and can manage killing firefox quickly enough before it freezes which will reduce RAM usage and everything is ok.

but i'd expect ubuntu to run slower and not to freeze altogether.

Is my swap maybe corrupt? can i repair it?

is this maybe a known bug?

thanks for any help!

---

### Post by housam on 2008-03-30
we normally make swap partition 1-2 the size of RAM. Your swap partition is less than that ratio. try to resize it to a suitable size.

---

### Post by linuxd00 on 2008-04-01
hi,
thanks for the answer...

but again... i have to doubt.
Why does ubuntu freeze instantly... one would expect it to work at least until RAM usage hits 1,6GB then... but it freezes instantly o unusability.

---

### Post by anindya_m on 2008-04-01
The new linux kernels are happy when swap size = RAM (2 * RAM is no longer needed). The "freeze" that you experience is typical when heavy swapping happens as the hard disk is an order of magnitude slower than RAM. I have seen systems take 30 mins or more to recover under extremely heavy loads. Sometimes, if you can no longer move the mouse, a quick Ctrl+Alt+Backspace helps (sure it will kill your session, but at least you won't have to reboot).

In addition to setting swap size properly, you can also set up your system to automatically kill a program when its memory usage exceeds a certain amount. A very simple (and not entirely foolproof) way is to set up usage limits in your /etc/profile. For example, to restrict the resident size (actual RAM usage) of any process to say 800 MB, just append the following line at the end:
```
ulimit -S -m 819200
```
After you log in, run the command "ulimit -a" from a terminal to check if the setting is active. See the bash manpage for more details.

---

### Post by linuxd00 on 2008-04-03
Hi,
thanks for the tip with ulimit! thats great! is there a possibility to restrain it to only one program? i actually only want to kill firefox(hope not to have this issue with FF3!)
ill read the manual as soon as i get home

as for the swapping i still think something might be wrong because swapping on windows is more smoothly... the computer gets a lot slower of course... but it never freezes.

my ubuntu seems to freeze as soon as im one kilobyte over my physical ram.
It starts to swap and never stops. :(

---

### Post by anindya_m on 2008-04-07
Hi. One very simple way to restrict usage limits to firefox is to make a script like:
firefox.sh
```
ulimit -S -m ####    #Size in KB
exec /usr/bin/firefox
```
then edit your firefox launcher button to run the above script.

linux VM performance in my experience is quite a bit better than on windows (just copying a few GB sized files on a 512 MB machine makes this apparent); it seems worse with Vista, but that may be because it needs more RAM than XP on the same machine. So something is not right about the freeze you are experiencing. Normally you should almost never have to reboot, swapping or not. You can try the following:

1. Check if DMA is on for your disk (using hdparm -d)
2. Set swap = RAM.

It might help to look at your /var/log/messages file after a crash.

---

### Post by linuxd00 on 2008-05-11
turns out the device ID for the swap partition was wrong in fstab!
i found out because for the first time i tried to hibernate and it aborted saying that it didnt find the swap partition(i think it asked me to check the fstab file as well).

it seems that during the transition from 6.10 to 7.04 the names were renewed. I never noticed because Firefox2 was the first and only app to leak memory so bad that it would consume all my ram...

now i put the right deviceID in it.
I found out the right device ID by seeing in Gparted the partition name (in my case /dev/sda9) and loking the partitionID with 
```
vol_id /dev/sda9
```


i also right clicked on the swap partition in gparted and activated "swapon"

Now swapping occurs and its even smoother than in windows! in windows you hit the maximum amount of ram and the PC slows down as it swaps.
In Ubuntu the swapping process starts before you hit the RAM maximum.. so its actually seamless. No slow downs whatsoever. :)

hope his helps anybody...

---

### Post by RJARRRPCGP on 2008-05-11
> **linuxd00 said:**
> 
In Ubuntu the swapping process starts before you hit the RAM maximum.. so its actually seamless. No slow downs whatsoever. :)


I dunno, because Windows 98 and Windows ME (default with Windows 98 and Windows ME) swaps before the RAM maximum.

Windows 2000 and Windows XP is hard to tell.

Linux seemed to do it like Windows 95, wait until the RAM is full.

---

