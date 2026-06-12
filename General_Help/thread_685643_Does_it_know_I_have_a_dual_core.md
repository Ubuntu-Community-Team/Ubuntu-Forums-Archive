---
title: "Does it know I have a dual core?"
date: 2008-02-02
forum: General Help
---

### Post by gm04030276 on 2008-02-02
Silly question, but one I would like an answer to. Does ubuntu know I have a dual core processor? I ask because at the moment i'm running folding@home and its taking more than twice as long to complete each percentage than it does when running in windows (granted I think this is a harder work unit but not 2x) and also a lack of heat coming out. When its running flat out in windows, processor sits about 58-60 degrees and you can feel a good warmth with the fans on full but the fans are down now and theres not much heat making me think its only using one core. Any way to check?

nb. Intel Core 2  Duo E6700@2.66GHz OC'd to 3.21GHz

---

### Post by earobinson on 2008-02-02
```
cat /proc/cpuinfo
``` will give you all the info u need

mine
> earobinson@MinusOne:~$ cat /proc/cpuinfo 
**processor       : 0**
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
stepping        : 6
cpu MHz         : 2666.647
cache size      : 4096 KB
physical id     : 0
siblings        : 2
**core id         : 0**
**cpu cores       : 2**
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5337.08
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

**processor       : 1**
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
stepping        : 6
cpu MHz         : 2666.647
cache size      : 4096 KB
physical id     : 0
siblings        : 2
**core id         : 1**
**cpu cores       : 2**
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5333.38
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


---

### Post by gm04030276 on 2008-02-02
My output:
> memu@TTS3:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
stepping        : 6
cpu MHz         : 2660.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6403.88
clflush size    : 64

so i'll take that as a no :(

What can I do to make it work properly?!

---

### Post by earobinson on 2008-02-02
looks like a no to me, you could also try ```
gnome-system-monitor
``` in the terminal

you could install the 64 bit version of ubuntu if you are currently using the 32 bit one.

---

### Post by gm04030276 on 2008-02-02
I am using the 32bit version. That was my first thought but i REALLY don't want to have to wipe and install 64bit. Anyway to upgrade to 64bit easily? like changing the repositories or something nice and simple?

---

### Post by Lord Illidan on 2008-02-02
folding@home only uses SMP (multi-cores) with their beta 64 bit client. [http://www.stanford.edu/group/pandegroup/folding/download.html](http://www.stanford.edu/group/pandegroup/folding/download.html)

In other words, either install 64 bit linux, which seems to be getting easier every release, or else use Windows to run folding@home.

---

### Post by Lord Illidan on 2008-02-02
But, while we're on the subject, and I am re-reading this thread, even if you're running 32 bit, Ubuntu should still recognise that you have a dual core processor. What does ```
uname -a
``` tell you?

---

### Post by ~LoKe on 2008-02-02
Try...
```
uname -r
```
Are you using the -generic kernel?

---

### Post by gm04030276 on 2008-02-02
uname -r 
> 2.6.22-14-386
uname -a
> Linux TTS3 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

Had a look about, seems upgrading from 32 to 64 is NOT a good idea (surprise!) so ill just reinstall and use dpkg --get-selections etc to get all my stuff back. Just need to save a few config files aswell!

---

### Post by ~LoKe on 2008-02-02
No need to reinstall.  Just do this:
```
sudo apt-get install linux-image-generic
```
Then reboot. =]

---

### Post by gm04030276 on 2008-02-02
and that will do what?!

---

### Post by ~LoKe on 2008-02-02
That will enable your second core.  The -386 kernel supports only one core.  -generic supports many more.

---

### Post by Lord Illidan on 2008-02-02
The 386 kernel which you were using does not support dual core, getting the generic kernel will help! You still won't get smp performance in folding@home though.

---

### Post by gm04030276 on 2008-02-02
says it already there, but now that i remember, i have a list of 9 (or 11) various kernels that come up in grub, and they're all the generic one except for the top 2 and i always just select the top one assuming its the  best because its at the top lol!
Well thats good to know but i think i will install 64 bit anyway because there are some other apps i want to run which say they work better in 64bit, shouldn't be that big a deal to upgrade (i hope!) not when i don't have to remember everything to install and if i back up config files it should be fine! :D

Thanks for all your help guys! Muchly appreciated! :D

---

### Post by ~LoKe on 2008-02-02
64bit is a complete re-install so you'll have to download everything all over again, but that's not too difficult.  As for 64bit offering better performance...yes!  If you run folding@home often (as you should) then you would **most certainly** benefit from 64bit.  Oh, and you can remove items from the list, to make things easier (there is **no reason** to boot the -386 kernel).

```
gksu gedit /boot/grub/menu.lst
```
And remove the unwanted ones.

---

### Post by Bif Powell on 2008-02-02
How can you insure that you're installing the 64-bit version?  When I first installed Ubuntu (7.04) it just recognized it as 64-bit automatically and I never did anything.

Now I just installed 7.1 and when I try the trouble-shooting steps in this thread, I'm on the generic kernel - I used the same procedure that I used with 7.04).  I don't recall seeing a selection for this during install.

Also, when I reinstalled will I end up with two grub entries or will it be smart enough to deal with that?

---

### Post by ~LoKe on 2008-02-02
> **Bif Powell said:**
> How can you insure that you're installing the 64-bit version?  When I first installed Ubuntu (7.04) it just recognized it as 64-bit automatically and I never did anything.

6.10 and later ship with the generic kernel, afaik, so despite your architecture (x86/x64) you'll have support for more than one core/processor.  As for knowing if you're installing 64bit or 32bit...well...it depends on which ISO you downloaded.  To check right now if you're on 64bit or not, type this into the terminal:
```
uname -m
```
If it outputs i686, it's 32bit.  If it outputs x86_64, it's 64bit.

---

### Post by Bif Powell on 2008-02-04
> **~LoKe said:**
> 6.10 and later ship with the generic kernel, afaik, so despite your architecture (x86/x64) you'll have support for more than one core/processor.  As for knowing if you're installing 64bit or 32bit...well...it depends on which ISO you downloaded.  To check right now if you're on 64bit or not, type this into the terminal:
```
uname -m
```
If it outputs i686, it's 32bit.  If it outputs x86_64, it's 64bit.

So essentially if I want to guarantee that I have 64-bit installed I need the proper ISO? (which makes sense, obviously but my assumption was that the ISO I downloaded would figure out what I had and use the right kernel and I missed/neglected some setting)

---

### Post by ~LoKe on 2008-02-04
Yep, it's all with the CD image you downloaded.  The reason for this is that all the libraries that are pre-installed have to match your architecture.  This is basically why it's difficult/impossible to upgrade from 32bit to 64bit without re-installing.

---

### Post by Bif Powell on 2008-03-03
> **~LoKe said:**
> Yep, it's all with the CD image you downloaded.  The reason for this is that all the libraries that are pre-installed have to match your architecture.  This is basically why it's difficult/impossible to upgrade from 32bit to 64bit without re-installing.

OK, I'm back at this now - downloaded and installed the proper kernel and my output from uname -m is finally:

x86_64

However, when I boot up and select my OS from the boot menu it still says 'generic' - do I have something mismatched or is the boot menu just borked?

Thanks!

---

### Post by gm04030276 on 2008-03-03
No, its all grand! It should say Generic.
From what I understand the Generic kernel works with all 32bit and 64bit x86 CPU's. It figures it out at boot time which system its running on, its the rest of the OS that makes the difference.
I'm not really clued into it all but I know it works!

---

