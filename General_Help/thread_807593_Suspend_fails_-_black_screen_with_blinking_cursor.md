---
title: "Suspend fails - black screen with blinking cursor"
date: 2008-05-25
forum: General Help
---

### Post by jtreminio on 2008-05-25
Hello!

I am using Ubuntu 8.04 - everything on it works perfectly except for suspend/hibernate.

When I try to use either feature, the screen goes black and a cursor blinks in the top left corner. The HDD's spin down as if it was actually going into suspend, but my fans happily keep spinning. I've left it in this state for long periods of time, hoping it would go to suspend after X amount of minutes passed, but I've come back 4 hours later and it's still the black screen with a cursor. My monitor does not shut off during this time.

Any keyboard keys do nothing - ALT CTRL BACKSPACE does nothing - basically my PC is frozen except for that cursor blinking, mocking me. I am forced to hard reboot the machine to get anything done again.

I am using a desktop... here are the specs:

MB: Asus nForce 4m-a
cpu: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
gfx: GeForce 8600 GT

I am currently using the nVidia proprietary drivers - but I think I've tried it with them disabled and the same problem occurs.

Also, when I boot my machine, I get the following error:

MP-BIOS bug 8254 : Timer not connected to IO-APIC.

I do not know if this is related to the suspend problem, but it briefly shows this error before continuing to boot normally.

Any help with this buzz-killer would be greatly appreciated!

Thanks,

Juan

---

### Post by m i k e on 2008-05-26
I have the same suspend issue.  I've got an ATI Radeon 9800 Pro, ASUS P4P800 Deluxe, and a Pentium 4.

---

### Post by tmtan on 2008-07-29
hey, well im in the same boat, though im running on a Sony Vaio Fz laptop. ive been trying to figure this out for a while and havent got real far, However, i did notice that my swap partition was not being used or recognized by ubuntu. The partition editor sees it as swap, but the fstab entry did not correspond. well of course, there was my failing issue. so i fixed the swap. now the computer will sometimes suspend correctly, and sometimes not, confusing. hibernate hasnt ever and still isnt working. so do both of yall have swap fully recognized and running?

---

### Post by rudy.elgato on 2008-07-29
Having a similar problem with suspend on my desktop.  By all appearances, it looks like the system will correctly suspend, that is, the disk will spin down, monitor will darken, and the light on  the reset-start button will slowly flash.  But after that, I can never get it to resume.  The only way I can get the system back is a complete power reset.  

I've been very pleased with my decision 2 months ago to completely switch from windows to Ubuntu 8.04, except for this suspend/hibernate/resume not working.  I've been searching these forums on a very regular basis and have tried a few recommended "fixes", but still have not found anything that works...

Sure wish I could get suspend to work properly on my desktop...

---

### Post by ndest964 on 2008-08-07
I have the same problem, computer suspends fine, however I just get a blinking cursor when trying to restart.  Only way to get my computer back is power it down.  Anybody with a solution?  I didn't have this problem running Ubuntu 7.10.

Heres my pc
Abit IP35-Pro
Core 2 Duo 2.33
2 Gigs Crucial Ballistix
Seagate 7200.11 500gig hdd
Nvidia 8800gts (512)
Dual SATA DVD Burners

Thanks,
Nick

---

### Post by tuxxy on 2008-08-07
I had suspend issues, solved it by opening system > prefs > screen saver > power management and disablong any power saving that was active.

---

### Post by cdtech on 2008-08-07
I had the same issues with "suspend/hibernate" my fix for suspend was editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" around line 74. This will cause suspend when the lid is closed.

Then I made a couple of alias's to hibernate or suspend from the command line using:
```
alias sleep='sudo /etc/acpi/sleep.sh force'
alias hibernate='sudo /etc/acpi/hibernate.sh force'
```

I'm happy now.

Hope this helps...........

---

### Post by rudy.elgato on 2008-08-20
I went through the 6 steps listed in:

[]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/")

and suspend/hibernate (and Switch User) is working perfectly on my system (dell optiplex gx270, nVidia GeForce FX 5200, ubuntu 8.04)...

---

### Post by rudy.elgato on 2008-08-20
whoops...  here's the link:

[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

---

### Post by luckytwitch on 2008-08-27
So, I'm a new Ubuntu user, but after cruising through these forums and following lots of links, I found something that works for my system (Kubuntu 8.04 and KDE on my Sony Vaio VGN-CR123E). I'm not quite sure what it actually does, but my suspend works now.
Here's the link that I found, [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/226279](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/226279), and the following is the code that I used to make suspend work:
Code:

echo "SUSPEND_MODULES=ehci-hcd" > /tmp/unload_modules
chmod +x /tmp/unload_modules
sudo mv /tmp/unload_modules /etc/pm/config.d

If anyone can explain what this actually does, it'd be cool, thanks

*edit*
actually, this may break something else,once I restarted again, I got an error, but that could be do to my other tinkerings in the past few days.

---

### Post by Jaxco on 2008-08-31
I will keep an eye on new releases but after a year and a half on ubuntu this new suspend problem with my ATI 9800 is forcing me back to windows for the time being... I really like ubuntu but it drives me batty to leave the computer awhile and have to power down.  I have been through this thread and a dozen others trying to get this glitch out... Gutsy with older drivers was far more stable.... cannot believe this is actually an LTS!

---

### Post by blackpaw on 2008-12-02
> **rudy.elgato said:**
> whoops...  here's the link:

[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

That did not work for me. 
Only think I achieved was tearing of my display. :(

Can anyone tell me how I approach this? Troubleshooting steps?

I followed the debug suspend wiki entry (making a trace by changing the real-time clock) but I could not find any offending modules and it seems my system went to sleep and immediately woke up again with blinking cursor and running fans.


This is the only reason I can not give Intrepid a "10" - please help ;)


[SIZE="1"]System: Ubuntu 8.10 x86_64 on ASUS P5Q-E board (Intel P45 chipset), Intel core2quad processor, NVIDIA 9600GT (tested with proprietary drivers and without), system basically works without any problems...[/SIZE]

---

### Post by itsbenderingtime on 2009-03-13
I don't have a solution for anyone, but I do have a thought. Most all of us on this thread are seeing essentially the same problem, but we're not seeing the EXACT same problem (some of us having problems on wakeup, some on the suspend), so no solution is solving everybody's problem.

Here's what I'm starting to think - I think some of us (including the original poster) are not having problems with our graphics cards screwing up suspend, but are rather having problems with our MOTHERBOARDS screwing up suspend. I have a similar setup to many people on this thread - An nVIDIA GeForce card (8800 GTS) and an ASUS motherboard (P5N-SLI), and I'm having the same problem as they are. Black screen, blinking cursor, fan on, but the power button is NOT blinking (so I can't say that the suspend has suspended without incident).

Can someone who knows something about power management help me out here? All of the stuff I read on the internet puts the blame on the graphics card, has anyone heard of a motherboard fouling up the suspend process?

---

### Post by blackpaw on 2009-03-14
> **itsbenderingtime said:**
> ... has anyone heard of a motherboard fouling up the suspend process?

I also suspect the motherboard... but most often it is related to modules that cannot be stopped in order for the system to come to a halt. Most of the time it turns out to be the graphics card, that's why everybody is pointing in this direction.
 
What you can do is the usual:
- check BIOS settings for power/suspend-related things
- remove/replace hardware and try again with different combinations
I did all this, for example changing suspend type to S3 only, disabling Speedstepping, disabling legacy USB support, replacing/removing hardware till I was at the bare motherboard with only the VGA card. Then I removed memory modules, changed my SATA hdd to a ATA hdd, etc.. nothing helped.

Then I discovered the "resume-trace" procedure which allows for better debugging:
[https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") 

Here I found out that my system goes to sleep but immediately wakes up again the same second it comes to a sleep state.

Now. I tried to find out what causes my system to wake up immediately but I got stuck there / gave up there. I would have continued but I have a job, a family... just not enough time to troubleshoot extensively. 

I decided to wait for an update / a patch that fixes this. Kinda "How to debug / interpret resume-trace" thread...

This one got pretty far:
[http://ubuntuforums.org/showthread.php?t=967697]("http://ubuntuforums.org/showthread.php?t=967697")

And this thread even shows how to troubleshoot extensively:
[http://ubuntuforums.org/showthread.php?t=505890]("http://ubuntuforums.org/showthread.php?t=505890") 

So.. shall we start a new suspend/resume thread with traces and debug kernels?

Let me know if I can help.



Andreas

---

### Post by kimifrega on 2011-03-13
this worked for me on my Asrock ION 3D 152d with Ubuntu 10.10 Server 64 bit:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

I found it after hours and hours...

---

