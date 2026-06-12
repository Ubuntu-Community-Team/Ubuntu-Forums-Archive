---
title: "Need a little help installling please."
date: 2008-05-07
forum: General Help
---

### Post by JakeG1 on 2008-05-07
Just today I started trying to convert over to Ubuntu from XP Pro, but have continually run into the same problem. After looking around I believe it is called the Bug #82314. I boot the Ubuntu CD and select Install, It then starts loading and when it gets to what looks like a loading bar, it stops at the third "block/segment" of the bar. A little later it gives me a screen with what looks like errors. This is what appears on the screen:

 *Preparing restricted drivers...       [ OK ]
 *Setting the system clock
 *Starting basic Networking...          [ OK ]
 *Starting kernel event manager...      [ OK ]
 *Loading hardware drivers...       
udeve-event [7020]: run_program: '/lib/udev/path_id' abnormal exit
ud/etc/rcS.d/S10udev:eve-event [7085]: run_program: '/sbin/modprobe' abnormal exit
udeve-event [7106]: run_program: '/lib/udev/usb_id' abnormal exit
Segmentation fault
/etc/rcS.d/S10udev: 105: /usr/bin/tput: not found
/etc/rcS.d/S10udev: 1: usplash_write: not found
Segmentation fault
Segmentation fault
init: rcs main process (5813) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (7170) terminated with status 255

This is my first attempt ever at installing anything having to do with linux, so do I need to download any files before I boot from the CD? I have tried installing Unbuntu while XP was on my Hard Drive, and also right after formating my Hard Drive so there would be nothing on it. I'm not concerned with dual booting or anything, I would just like to know how I would fix this problem. If anybody could supply an answer or point me to a thread I would greatly appreciate it, thanks.

As a side note I have also tried installing other Linux cd's like Mandriva and Knoppix, but both come up with some error about the /bin. After looking at this thread: [http://ubuntuforums.org/showthread.php?t=398487&highlight=Target+filesystem+doesn't+have+%2Fsbin%2Finit](http://ubuntuforums.org/showthread.php?t=398487&highlight=Target+filesystem+doesn't+have+%2Fsbin%2Finit)
 it seems I need to install the kernel fix, but I have no idea how. I tried the FixMBR, didn't work.
-Jake

---

### Post by anuban on 2008-05-07
Please check if the Live CD you burnt is good.  Before installing Ubuntu, you get an option 'Check Disk for errors'.  try that if it throws any error.
Worst case you might have to download again or install with alternate CD.
Hope this helps as you are doing a full clean without dual booting, so it should be quite straight forward.  No customization is require.

Thanks
Anurag

---

### Post by JakeG1 on 2008-05-07
Thanks for the quick reply. I have burned multiple Ubuntu disks and have checked them for errors, so far none have come up as being corrupted. Does anyone know if there is a way to reinstall /bin files? I think that is the problem, but then again I am completely new to this.

---

### Post by anuban on 2008-05-07
> **JakeG1 said:**
> Thanks for the quick reply. I have burned multiple Ubuntu disks and have checked them for errors, so far none have come up as being corrupted. Does anyone know if there is a way to reinstall /bin files? I think that is the problem, but then again I am completely new to this.

I think your best bet will be to use the Alternate CD.  BTW, which computer you are trying to install it.
Other thing you can try is run it through Live CD without trying to install it.  Just to check Ubuntu supports all your hardware.  Once satisfied, go for install option.  If Live CD doesn't work, try Alternate CD.
Hope that helps

Thanks

---

### Post by JakeG1 on 2008-05-07
I did what you suggested and clicked Install inside of Windows. So far it seems to be working, it's not done yet though.It says 19 hours remaining. Bah XD. Does this mean that I will still be running XP?

As for my computer, it is a Intel Pentium 4 Desktop, 3.00 GHz, 2.5 GB Ram.

---

### Post by anuban on 2008-05-07
By trying Ubuntu I mean, don't use Wubi to install it on your system within Windows.
Step to follow to try with Live CD:

[LIST=1]
[*] Insert LiveCD when booted with Windows.
[*] Restart your PC with Live CD in.
[*] Press F2/F12/F8 or whatever to go to BIOS booting options.
[*] Select boot from CD/DVD.
[*] Select 'Install or try Ubuntu wihout changing your system.'
[*] Let it load.
[/LIST]
 This is what is called booting from Live CD and trying Ubuntu without changing your existing OS.  You might wanna check this link:
[http://anuragbansal.wordpress.com/2008/04/08/how-to-try-ubuntu-without-messing-with-your-existing-os/](http://anuragbansal.wordpress.com/2008/04/08/how-to-try-ubuntu-without-messing-with-your-existing-os/)

let me know if it helps.  You can PM me for live chat at my AOL.

Thanks

---

### Post by JakeG1 on 2008-05-07
The same thing happens when I select the try option. It hangs at the loading bar and kicks me into the error page. Maybe my computer doesn't want to switch from XP :rolleyes:. I'll leave it for tonight and come back to it tomorrow. Thanks for all your help.

---

### Post by JakeG1 on 2008-05-08
Update:

Okay, so I now know that my CD is okay. I booted the live CD on my laptop and everything worked fine, It got passed the loading bar and into the live CD. This means that it has something to do with my PC, any ideas on what to do or try from here? Thanks.

---

### Post by JakeG1 on 2008-05-08
Still trying to find a solution, can anyone offer a suggestion? Thanks.

---

### Post by cerebellum on 2008-05-08
> **JakeG1 said:**
> Still trying to find a solution, can anyone offer a suggestion? Thanks.
Well since the CD is working fine on the laptop, good chance is the problem is in the hardware. What's the graphic adapter? Is it i386 or amd64?

---

### Post by JakeG1 on 2008-05-09
It is I386 I presume. When I burned a disk with the 64 version and inserted it, an error popped up saying I had a I586, not a 64 and needed to install the correct Kernel. So is I586 different from I386?

---

### Post by Madman6510 on 2008-05-09
Because you have a Pentium 4, which is not a 64 bit processor, you want the normal, 32 bit version. Did you try checking the box that says you want the alternate install CD on the Ubuntu download page? (It's a text installer, so it's a little harder to work with, but still workable.)

---

### Post by JakeG1 on 2008-05-09
Alright, I'll give that a try. Thanks.

---

### Post by JakeG1 on 2008-05-09
Alright, I am now using the alternate CD and things are going better then with the live CD. I am still running into a little trouble though. I go through the text installation normally and when it asks about the partition I select Guided - Use entire disk. Once the installer finishes and reboots, I keep getting some weird error. Like when I leave it alone and let it do it's thing at startup I get. ```
init: rc-default main process (5345) killed by SEGV signal
```

Is there a guide for installing from an alternate CD? This installation is driving me insane, but I really want to get it working seeing how I've already whipped my XP off the computer. Thanks.

---

