---
title: "Mouse/Ubuntu seems to freeze up every few minutes?"
date: 2015-05-27
forum: General Help
---

### Post by PsychedelicWonders on 2015-05-27
It's a new clean install of 14.04 on an SSD and every few minutes the mouse/Ubuntu seems to freeze up for a minute or so and then goes back to being ok for a few minutes then the mouse freezes again etc.  This is a wireless and wired mouse.

Any ideas on the issue so it can be fixed?

---

### Post by DuckHook on 2015-05-27
I take it that the wireless is USB dongle, but both tried on the same port? If so, try changing the USB port. Also, look at dmesg output for clues/conflicts.

---

### Post by PsychedelicWonders on 2015-07-16
Still having this issue and it happens every couple of minutes - beyond frustrating!

Yes it is hooked up via a dongle, I am new to Ubuntu, so where do I find this dmesg output info?

---

### Post by tgalati4 on 2015-07-17
Open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.

Paste any error messages, not the entire output.

---

### Post by PsychedelicWonders on 2015-07-17
Hmm, I ran that code and didn't seem to see any error messages.

Now that I've been using it a bit more, it seems that it's actually Ubuntu freezing up for 10+ seconds, then goes back to normal.  

It did this on the install just before this one too.  I installed a fresh 14.2 Ubuntu on a brand new SSD and forgot encryption password so had to secure erase and then reinstall.  This lag/freeze issue happened on both installs.

Any other idea on what it could be or how to fix it?  I can't use Ubuntu if this persists...

---

### Post by NoWayWin8 on 2015-07-17
I had freezes like that until in the Mouse & Touchpad settings I deselected al the Touchpad options (there are 4) but don't disable touchpad itself.

Haven't had a freeze since.

---

### Post by tgalati4 on 2015-07-18
If the Mouse and Touchpad settings don't fix the problem, I would look at encryption.  What is encrypted?  Your home folder?  The entire operating system?  It's possible that encryption is causing the delays.

Install *htop*.  Open a terminal:

```
sudo apt-get install htop
htop
```

Describe what you see during the frozen periods.

---

### Post by PsychedelicWonders on 2015-07-18
Yes I have the entire OS & home folder encrypted.  I figured if it gave me the options, I might as well utilize them.

I do plan on defaulting to the SSD hardware encryption that Samsung uses once I get an Asrock Mobo (they are the only mobo that will allow a bios setting to set a TRUE ATA password to enable the encryption of the key to the encryption.)  But for now I figured I'd use the software encryption Ubuntu comes with.

That is unless that is what is causing these delays/timeouts.

It's hard to say, but I think it's the entire OS freezing.  I will install and run that htop now and post my results.

---

### Post by PsychedelicWonders on 2015-07-18
Ok so what should I post back from the htop program? 

It is def the entire OS freezing up.  This is a brand new Samsung 850 Pro, shouldn't be any issues being able to handle Ubuntu's encryption.  I really hope that's now what is causing this lag, I think it's a great feature being offered on the OS and I would really like to use it, but not if it comes down to this constant lag/freezing.

---

### Post by tgalati4 on 2015-07-18
I'm sorry, you only need to run *top* (which should already be installed.)  Pay attention to CPU load, IO Waits (wa) and System load (sy).  I believe encryption should be captured by the System load cycles.

It might look something like:

> 
tgalati4@Mint17 ~/Desktop $ top

top - 20:17:30 up  2:53,  2 users,  load average: 0.81, 0.62, 0.48
Tasks: 184 total,   2 running, 182 sleeping,   0 stopped,   0 zombie
**%Cpu(s):  1.8 us,  1.5 sy,  0.0 ni, 94.9 id,  1.8 wa,  0.0 hi,  0.0 si,  0.0 st**
KiB Mem:   2040640 total,  1961564 used,    79076 free,     1760 buffers
KiB Swap:  2578428 total,    74284 used,  2504144 free.   387200 cached Mem



Hit Control-C to quit, then you can cut and paste the results.  Try to do it before and during a freeze.

---

### Post by PsychedelicWonders on 2015-07-18
I don't think I did it right:

```
johnnyscience@SpaceStation:~$ sudo-apt top
sudo-apt: command not found
johnnyscience@SpaceStation:~$ sudo apt-get install top
[sudo] password for johnnyscience: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package top
johnnyscience@SpaceStation:~$ ^C
johnnyscience@SpaceStation:~$ 

```

---

### Post by PsychedelicWonders on 2015-07-18
It's for sure the OS freezing though.  Happens every few minutes still for a good 10 seconds.

---

### Post by NoWayWin8 on 2015-07-19
The command is 'top' all by itself.

---

### Post by PsychedelicWonders on 2015-07-19
```
top - 17:58:18 up 12 min,  2 users,  load average: 2.58, 1.87, 1.04
Tasks: 215 total,   2 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.1 us,  0.3 sy,  0.0 ni, 98.5 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8176068 total,  1713288 used,  6462780 free,    57780 buffers
KiB Swap:        0 total,        0 used,        0 free.   720544 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                  
 1373 root      20   0  565640 135896  54052 S  17.3  1.7   1:01.81 Xorg                                                                                                                                     
 2439 johnnys+  20   0 1287200 100428  62428 S   3.3  1.2   0:11.28 compiz                                                                                                                                   
 2908 johnnys+  20   0  660900  32016  23640 S   1.3  0.4   0:01.19 gnome-terminal                                                                                                                           
 1135 root      20   0    4376   1680   1500 S   0.3  0.0   0:00.71 acpid                                                                                                                                    
 2206 johnnys+  20   0  376612   8320   6904 S   0.3  0.1   0:00.56 ibus-daemon                                                                                                                              
 2228 johnnys+  20   0  558300  21872  17200 S   0.3  0.3   0:00.39 bamfdaemon                                                                                                                               
 2243 johnnys+  20   0  488196  24868  19840 S   0.3  0.3   0:00.40 ibus-ui-gtk3                                                                                                                             
 2616 johnnys+  20   0 1279536 384072  85096 S   0.3  4.7   2:54.65 firefox                                                                                                                                  
 2878 root      20   0       0      0      0 S   0.3  0.0   0:00.74 kworker/0:0        
```


Doe that help at all?

---

### Post by PaulW2U on 2015-07-19
Please use code tags for terminal output as they improve readability.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by PsychedelicWonders on 2015-08-02
Ok, thanks and sorry, I forgot.

So does that code read out help determine what is causing Ubuntu to freeze constantly?  Is there any way I can easily disable the encryption to see if if then runs smoothly?  It's on a new SSD, so unless it's my mobo or something that's locking it up, it really doesn't make sense why it's freezing the way it is?

---

### Post by tgalati4 on 2015-08-02
The package *htop* is not installed on default Ubuntu systems.  Type carefully:

```
sudo apt-get install htop
htop
```

Your *top* output looks normal.  You have no IO Waits (wa) so your disk drive is probably OK.  Your system load is also small (0.3%) so that is OK as well.  I could be a bug with the kernel and encryption or a problem with the SSD and encryption.  I would boot using a LiveUSB stick and see if your system runs OK.  If so, then back up your important data, wipe the disk and reinstall without any encryption.

---

### Post by PsychedelicWonders on 2015-08-07
Ok so I tried just running the liveCD and messing around a bit and seem to be running into the exact same issues.  The computer freezes every couple of minutes for a good 10-20 seconds.

When trying to open firefox or Wordpad, it takes 30-60 seconds for the program to open (I feel like I'm on XP! lol) and then I started typing a paragraph to test this freezing issue out and sure enough, even typing in wordpad froze up for a good 20 seconds before allowing me to type again.  It's not just the mouse, but the entire OS.

This is the liveCD that I used to install onto my SSD, so do I just have a bad download?  Should I try a new download/liveCD creation?  I downloaded 14.04.2

Any suggestions?

---

### Post by tgalati4 on 2015-08-07
The LiveDVD does not use encryption when booting into a Live Session, so we can rule that out.  Although it is possible that a bad DVD can cause a bad install, there should be a "Check Media" option when you first boot the Live disk.  Run that and it will check the entire media for errors.

I think we can rule out the SSD as well, since the Live Session is run completely in RAM.  What is the output of:

```
cat /proc/cpuinfo
```

What is the make and model of this computer?  How old is it?

---

### Post by PsychedelicWonders on 2015-08-10
I do not see any option to "Check Media" It just boots up into Ubuntu and only gives me options to install or run Live CD - can I check media once I run LiveCD any where?   I looked around and didn't see anything.  Is this perhaps an indicator this is a bad kernal?

This is a home build, Intel quad core, 8g ram, dual nvidia 9800 GT video cards etc.  I've had this computer for about 7 years now.  But the SSDs are only a couple weeks old, I have two Samsung Pro 850's, 128g for Ubuntu & 250g for Windows.

I don't have any more DVDs to try and burn another kernal with, I'll have to stop at the store over the next day or two.  I guess I'll try downloading 14.04 again & if still having issues I'll try the 12.04

Here is the output for the code you gave me:

```
johnnyscience@SpaceStation:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 4810.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 4810.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 4810.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
microcode    : 0xb6
cpu MHz        : 1596.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 4810.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


```

---

### Post by tgalati4 on 2015-08-11
It's possible that your motherboard is having timing issues with the SSD.  I would put in a fast WD drive (raptor or equivalent) since that is what the motherboard expected 7 years ago.

Pull both SSD's out of the machine and then boot the LiveDVD.  If you still have freezing issues, then there is an issue with the kernel and your motherboard.   It's possible you have a failing motherboard.  Any bulging or leaking capacitors on the motherboard?

---

### Post by mörgæs on 2015-08-11
Before disassembling the hardware I would suggest a fresh install of 15.04. It solved the problem for me using a slightly older Nvidia card.

---

### Post by PsychedelicWonders on 2015-08-11
I am running Windows 7 on the 256g Samsung 850 Pro SSD and it runs flawlessly, I've also had a Samsung 840 Evo running Windows 7 for almost a year before upgrading to the 850 and it also ran flawlessly.  Nothing is broken or leaking on the mobo & while it's is dated (I plan on building a new watercooled computer over the next several months) it has ran perfect it's entire life.  

I will try disconnecting both SSDs & running the liveCD.  I really wanted to run 14.04 since it is LTS, but I could try the 15.04 version, perhaps it is an issue with the older Nvidia cards I'm running?  Would I better going with the 15.04 version vs the 12.04?

For the record I have an Asus P5k-E mobo

---

### Post by PsychedelicWonders on 2015-08-15
So I re-downloaded 14.04.3 again and put it on a USB and this time and I got the menu to check disk for errors, it runs it's test and came back with 2 files having errors. 

Can I check which two files have errors? What should I do, re-download it again and give it a 3rd try?  I'm downloading right from the main link on Ubuntu... I don't understand why this has been so difficult and frustrating.

---

### Post by mörgæs on 2015-08-15
Would be better to try 15.04. 
After download you can verify that the ISO is correct using [MD5 hashes]("https://help.ubuntu.com/community/HowToMD5SUM"). It's an easy test.
Here is the [mirror list]("https://launchpad.net/ubuntu/+cdmirrors") so you can get a fast download.

---

### Post by PsychedelicWonders on 2015-08-18
Ok, just out of curiosity I tried re-downloading 14.04 again and ran the Ubuntu disk check test and it's still coming up 2 filles with errors.

Any way to check & verify what 2 files are having errors?  Is this a known issue with 14.04?  

I just downloaded 15.04 and going to try to to the Ubuntu disk check on that and if all goes well with no errors I will try installing it on the SSD.

---

### Post by tgalati4 on 2015-08-18
The media check runs through all of the installation files and compares the MD5 sums to a text file stored on the disk.  If there is a mismatch, then the files are flagged.  It's possible that when packaging the distro that the MD5 sums in the comparison file are incorrect.  It's possible that there are errors in the mirror that stores the distro.  I imagine that there is a log file that shows the bad files, but I don't know where it is kept since it is running a mini Live Session when performing the check.

You could try 15.04 and perform a media check.  If you have a clean disk that passes inspection and you still have problems, then that really doesn't narrow down the causes does it?

---

### Post by PsychedelicWonders on 2015-09-05
15.04 finally was able to be installed and already giving me these same issues.

How can Windows 7 64 run FLAWLESSLY for years on my system, even when migrating it to an SSD, but Ubuntu is constantly having problems from the get go?

---

### Post by PsychedelicWonders on 2015-09-06
Anyone have an idea?

---

### Post by tgalati4 on 2015-09-06
Did you pull out the SSD and boot into a Live Session?  Is your system stable without the SSD?

---

### Post by PsychedelicWonders on 2015-10-25
I finally got around to pulling all SSDs & running just the live CD, pretty sure it was version 15.04 that time too.

Still having these freezing issues, even tried adding a wired mouse to the system and still same issues.

I realize my system is a bit old and will be getting upgraded hopefully over the next 6 months or so, but how is Win7 64 able to run flawlessly and yet Ubuntu 14/15.04 is having such issues to the point it's not even usable?

---

### Post by tgalati4 on 2015-10-25
You have a 7-year old motherboard.  It could be worn out.  Pull the RAM and boot a LiveUSB with minimal RAM (One stick).  Check the voltage of the power supply in BIOS or use a voltmeter.  Declock the computer.  Slow down the front side bus and the CPU clock multiplier.  

Is this machine dual-boot?  I'm going to guess that you wiped Windows7.  If so, try reinstalling and see if your computer still works the way you expect.

---

### Post by PsychedelicWonders on 2015-11-03
> **tgalati4 said:**
> You have a 7-year old motherboard.  It could be worn out.  Pull the RAM and boot a LiveUSB with minimal RAM (One stick).  Check the voltage of the power supply in BIOS or use a voltmeter.  Declock the computer.  Slow down the front side bus and the CPU clock multiplier.  

Is this machine dual-boot?  I'm going to guess that you wiped Windows7.  If so, try reinstalling and see if your computer still works the way you expect.

I realize it's an older system & am in the midst of putting together a new build, but it's going to take at least a few months to get everything together & setup.  It's going to be a big desk case project.

In the mean time I'd love to use Ubuntu on my current system.  Windows 7 64 is and has been running on this system just fine for 7 years.  

So if win7 64 can run fine as bloated as it is, why is Ubuntu struggling when it's so much more stripped down, especially with an SSD?

---

### Post by tgalati4 on 2015-11-03
Try 12.04.

---

### Post by PsychedelicWonders on 2015-11-03
Ok will do.  Am I still able to download older version from Ubuntu.com or do I need to go to sourceforge or something?

---

### Post by tgalati4 on 2015-11-03
I would choose an earlier kernel, in case there is a kernel issue with your motherboard.  [http://cdimage.ubuntu.com/netboot/12.04/](http://cdimage.ubuntu.com/netboot/12.04/)

---

### Post by PsychedelicWonders on 2015-11-06
So I assume I want the regular Netboot download, not the HWE backport kernels?  (Since I don't know what backport kernels are?)

But at the amd64 link, it pulls up a parent directory & i don't see any .iso to download?  I assume the mini.iso listed in the parent directory is not what I want?  I went through most of the folders & don't see any .iso?

Thanks.

---

### Post by PsychedelicWonders on 2015-11-17
bump

---

### Post by tgalati4 on 2015-11-17
Make a bootable USB  stick with *unetbootin*.  You can select the distro from there. 12.04 Live shows up as an Ubuntu pick.

```
sudo apt-get install unetbootin
sudo unetbootin
```

Insert a clean USB stick before hand.

---

### Post by PsychedelicWonders on 2015-11-17
I'm downloading ubuntu on windows to start, I don't have a usable ubuntu distro at the moment, so I'll probably use universal usb installer.

Do I still just download regular unetbootin and install the iso on the usb?

---

### Post by tgalati4 on 2015-11-17
*Unetbootin* is used on linux machines to create bootable USB sticks.  I don't know how it is done on Windows.  Haven't used it in years.  I sure there is a tutorial out there on how to make a bootable USB stick from Windows.

---

### Post by PsychedelicWonders on 2015-11-20
> **tgalati4 said:**
> I would choose an earlier kernel, in case there is a kernel issue with your motherboard.  [http://cdimage.ubuntu.com/netboot/12.04/](http://cdimage.ubuntu.com/netboot/12.04/)

> **tgalati4 said:**
> *Unetbootin* is used on linux machines to create bootable USB sticks.  I don't know how it is done on Windows.  Haven't used it in years.  I sure there is a tutorial out there on how to make a bootable USB stick from Windows.


Should I just go back to the orginal idea of downloading 12.04?

And if so, I [COLOR=#000000]assume I want the regular Netboot download, not the HWE backport kernels? (Since I don't know what backport kernels are?)[/COLOR]

[COLOR=#000000]But at the amd64 link, it pulls up a parent directory & i don't see any .iso to download? I assume the mini.iso listed in the parent directory is not what I want? I went through most of the folders & don't see any .iso?[/COLOR]

[COLOR=#000000]Thanks.[/COLOR]

---

### Post by tgalati4 on 2015-11-20
[[Backport kernels are older kernels than when 12.04 came out so you can run it on really, really old hardware.  You don't need that.]]  Wrong information, corrected below.

I believe mini.iso is the netboot image.  Put that on a USB stick and boot with it.  Make sure you have a working, wired, internet connection.

---

### Post by deadflowr on 2015-11-21
I'll concur that the mini.iso is indeed the netboot image, and that the top entry will give you the version with the original hardware stack for precise.

If you where to want to try any of the others, use the version with the trusty hardware stack (the version with the 3.13 kernel)

The other 3 versions listed contain unsupported hardware stacks.
(Ubuntu dropped support for those in, or around, August 2014; as users of those hardware stacks moved (or should have moved) to the trusty hardware stack.)
fwiw

> [COLOR=#000000]Backport kernels are older kernels than when 12.04 came out so you can run it on really, really old hardware[/COLOR]
It's the opposite.
They're newer kernel and hardware stacks that were built for the releases after 12.04.
They then build them (backported them) for 12.04.
They do this so newer hardware can run long term releases,
which they couldn't do if the old kernel doesn't have the support for the newer hardware.
if that make sense.

---

### Post by kurt18947 on 2015-11-21
I've seen what PsychedelicWonders is seeing when using a Logitech **wireless** keyboard and mouse.  A wired keyboard seems to work as advertised. In my case the pause problem does not seem to occur with fresh boots, rather after suspend/resume. I've found that powering the offending device off momentarily seems to eliminate the issue for some time. This is on a 2007-2008 vintage Gigabyte AMD board. I wonder if there is/was something to do with BIOSs or chipsets from that time frame that is causing this issue. My wife's machine is an ASROCK AMD MoBo current production. She sees no issue and is using a wireless Logitech keyboard and mouse.  I've seen no similar issues on a couple 2010-2011Thinkpads running the same O.S. 

I wonder if for trouble shooting purposes it'd be worth creating a live USB of a non-Ubuntu/non-Debian O.S. like Fedora or Open SUSE. Run that and see if the pausing issue persists.

---

