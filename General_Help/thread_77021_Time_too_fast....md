---
title: "Time too fast..."
date: 2005-10-16
forum: General Help
---

### Post by cmo on 2005-10-16
Installed Ubuntu 5.10 yesterday.  Installation went perfectly.  The only problem I have is that the system clock runs too fast.  About three seconds for every actual one second.

I dual boot with WinXP and it's fine there.  I was previously using Mandriva 2006 rc2 and that was fine also.  I've updated the bios to the latest version.

Any ideas?

I'm using a Compaq Presario SR1440UK Athlon64, but running the 32bit version of Ubuntu.  (When I used Mandriva that was the 32 bit version as well.)

The kernal installed at installation was the i386 one.  I also installed the i686 one later, but with no change to the time.

Please help...

Many thanks

cmo

---

### Post by Rogmo on 2005-10-16
What happens if you do this:


download adjtimex via synaptic package manager 


And then at console:


```
 sudo adjtimex -a
```

---

### Post by cmo on 2005-10-17
The following happens:

[COLOR="Navy"]chris@ubuntu:~$ sudo adjtimex -a
Password:
 ..................................................--- current --- -- suggested --
cmos time     system-cmos  error_ppm   tick      freq    tick      freq
1129532314   686.526834
1129532319   691.524670   499783.7  10000         0
1129532324   696.523532   499886.1  10000         0    5001    910390
1129532329   701.522393   499886.2  10000         0    5001    905701
1129532334   706.519255   499686.2  10000         0    5003    904752
adjtimex: Invalid argument
chris@ubuntu:~$[/COLOR]

It's still running way too fast.

Any thoughts?

Cheers

cmo

---

### Post by objorkum on 2005-10-17
Just keep the clock synchronized with a NTP-server. That's what Windows XP do, by default, but only every 3 days or so. NTP in GNU/Linux is much better.

Go System > Administration > Time and date

Mark "Periodically......" and select some servers, or add your own servers.

You may have to install NTP (server daemon), if you don't have it. If "Time and date" tells you to do that, just follow the instructions, and then restart the Time and date app.

---

### Post by cmo on 2005-10-17
The clock is synchronized with a NTP-server.  The problem is that the time is moving too fast for it to be of much use.  After 15 minutes the system time has moved on by about an hour.  The only way to keep it in check would be to continuously synchronise, which doesn't seem practical or sensible.

---

### Post by fezzle on 2005-10-25
I have the same problem it seems.  The clock is way too fast.  The clock remains correct while the system is off and in Windows.

The clock also seems to go faster out of sync depending on system load.  At 100% cpu usage on a single processor for 20 minutes, it will get 10 minutes fast (registers 30 minutes having passed).

My system is a nForce4 based motherboard with an AMD X2 cpu running 2.6.12-9-amd64-k8-smp.  

I get these messages from 'dmesg' that seem to be relevant:

[   20.949811] ACPI: Looking for DSDT in initrd... not found!
[   20.983582]  not found!
[   20.996382] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   20.996398]  failed.
[   20.996400] timer doesn't work through the IO-APIC - disabling NMI Watchdog!
[   20.997130] Uhhuh. NMI received for unknown reason 2d.
[   20.997132] Dazed and confused, but trying to continue
[   20.997133] Do you have a strange power saving mode enabled?
[   21.115430] Using local APIC timer interrupts.
[   21.159572] Detected 12.866 MHz APIC timer.

I have tried disabling APIC with no success, although the above messages disappear.

Using 'ntp' to keep it in sync is out of the question since it is just too far off and this is a server which needs the correct time all the time.  Not to mention all the problems 'sudo' has with the time going back 1000 seconds every hour.

Any suggestions would be appreciated.

Thanks

---

### Post by cokhavim on 2005-10-25
does this help?

[http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed](http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed)

it helped me...
jo

---

### Post by rick.sorensen on 2005-10-29
The kernel/board match (mis-match) seems to be the key.  I had this problem with my Gateway 7510GX (AMD 64) running the 64-bit Hoary Hedgehog release.  I just tried (today) the 386 (32-bit) version of the Breezy Badger live CD and saw the same 2-times clock speed.  However, when I tried the 64-bit live CD the clock seemed to be running at normal speed during a 15minute or so trial.  I have yet to install the new release on my HD- hopefully soon.

Rick Sorensen

---

### Post by ctechols on 2005-10-31
I'm also having this problem on an AMD64 X2 processor.  (I'm using 2.6.12-9-amd64-k8-smp).  My system seems to run about 4x too fast, even at idle.  Also, mouse and keyboard behavior is so erratic as to make the system unusable.  Does the system clock drive the X-Windows event loop?

The only bit of new information that I have to add is that the problem goes away when I boot under a non-smp kernel (2.6.12-9-amd64-k8-generic).

---

### Post by crudh on 2005-11-03
[QUOTE=fezzle]My system is a nForce4 based motherboard with an AMD X2 cpu running 2.6.12-9-amd64-k8-smp.  

I get these messages from 'dmesg' that seem to be relevant:

[   20.949811] ACPI: Looking for DSDT in initrd... not found!
[   20.983582]  not found!
[   20.996382] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   20.996398]  failed.
[   20.996400] timer doesn't work through the IO-APIC - disabling NMI Watchdog!
[   20.997130] Uhhuh. NMI received for unknown reason 2d.
[   20.997132] Dazed and confused, but trying to continue
[   20.997133] Do you have a strange power saving mode enabled?
[   21.115430] Using local APIC timer interrupts.
[   21.159572] Detected 12.866 MHz APIC timer.
[/QUOTE]

I've got the same system (nfoce4, amd x2 and same kernel) and running 64. I have the same problem. When the system is idle the time runs fairly correct. When under heavy load or heavy network load the clock starts to speed up. It goes at least twice as fast.

And when it starts to go fast all the activity in the computer speeds up to. The indicators in gkrellm runs faster, the cursor blinks faster and the key repetition runs faster.

But I have this in dmesg:

[   35.670807] testing NMI watchdog ... OK.

But I noticed:

[ 5340.554296] warning: many lost ticks.

I think I have seen stuff about this in the Gentoo forums. I will check it out, if nobody has a suggested solution to this.

---

### Post by stimpie on 2005-11-28
There is a bug (5105) for this at kernel.org 

Booting with "notsc" should solve this.

There is also a patch.
[http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view](http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view)

---

