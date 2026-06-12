---
title: "Urgent Help Needed"
date: 2008-06-02
forum: General Help
---

### Post by 1waytikt2tickletown on 2008-06-02
I'm trying to install Ubuntu 6.06 (I tried numerous times to install 8.04 but time after time the installation gets stuck at 5%). Sometime the installation goes fine (but then I get another error, but thats a different story) but now it wont install at all. I get this error:

We're sorry; the installer crashed. Please file a bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code -11; see /var/log/installer/syslog and /var/log/syslog

This is the 4th time today I've tried to install 6.06. The first 2, the installation was susccessful but I came across another error and the last two I've been getting this error.

Can anyone tell me how to fix this problem or the 'stuck at 5% on 8.04 LTS' problem?

I'm pretty sure its not the disc, becuase I was able to successfuly install 
6.06 before on the same PC but I got an error when trying to Update the system and was forced to re-install.

Help, please.

---

### Post by 1waytikt2tickletown on 2008-06-02
I did a serach on the forums and some guy said that he head the same problem (quite a few people actually with 6.06) and he rebooted his Pc and lowered the reoloution and tried again. He said it worked. Would this work for me?

Should I try another burn? If so, can someone point me in the direction of a good burn that WILL work?

---

### Post by 1waytikt2tickletown on 2008-06-02
I just did a check to see if the CD was OK. It says there isn't a problem with it. Can someone PLEASE offer assistance? Right now I'm downloading another 8.04 .iso file.

---

### Post by jamewill on 2008-06-02
please can you tell us the specs for the computer (processor/memory etc)

---

### Post by 1waytikt2tickletown on 2008-06-02
description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop uuid=1297A232-FFFF-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: AK32
       vendor: Shuttle Inc
       physical id: 0
       slot: USB
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/07/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 1011MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1


I quickly just got this. Its a crappy PC, I know. But its ran ubuntu 6.06 before. By the way, I just tried installing again with the lowered res (not sure what that would do) -- it didn't work.

---

### Post by 1waytikt2tickletown on 2008-06-02
Heres an update: i'm downloading 7.10 as we speak and i'll brun that onto a disc to see if it works. can someone tell me if i'm waisting my time?

---

### Post by 1waytikt2tickletown on 2008-06-02
Okay, what the hell?! Sorry to bump, bt I just burnt the .iso file of Ubuntu 7.10 onto a disc and selected install. I ran the installation and same as 8.04, it gets stuck at 5%. Oh, but my mouse gets stuck. It doesn't move at all (this didn't happen in 8.04). Seriously, why?

Is this the end of my Linux adventure? Will I REALLY have to go back to Windows. Please help.

---

### Post by Lord Xeb on 2008-06-02
I have a computer that runs at about 800MHz and it works just fine. 7.10 is my favorite release. I do no think you will have any problems. I have reinstalled Ubuntu 4 times and have had no problems (this is on my main). Good luck. If Ubuntu doesn't work, go with Xubuntu. It is a lot light weight.

---

### Post by 1waytikt2tickletown on 2008-06-02
Xubuntu you say? Where can I find an .iso link?

Nevermind, found one. Anyone know the main problem yet?

---

### Post by Lord Xeb on 2008-06-02
what tpye of ubutnu are you using? Is it x86 (or also know as i386) or AMD64? If it is the later, that is your problem.

---

### Post by 1waytikt2tickletown on 2008-06-02
i'm using x36.

---

### Post by Lord Xeb on 2008-06-02
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

Are you trying to install and another version through a livecd?

this can also pose some problems.

Also, who makes your pc? the specs do not tell me.

---

### Post by 1waytikt2tickletown on 2008-06-02
> **Lord Xeb said:**
> [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

Are you trying to install and another version through a livecd?

this can also pose some problems.

Also, who makes your pc? the specs do not tell me.
What do you mean? I just burned the .iso onto a CD-R, put it in and selected install. It does take me into the Live CD part where I can select install and look at the desktop ect...

And I think its a company called Energy who makes my PC.

---

### Post by 1waytikt2tickletown on 2008-06-02
just about to start burning xubuntu 8.04. god, i'm using so much CD-Rs. :(

---

### Post by 1waytikt2tickletown on 2008-06-02
well that one didn't work either. thats wierd. i'm going to try to install xubuntu 6.06 seeing 6.06 is the only one that sometimes installs

---

### Post by jimbosheep101 on 2008-06-02
ok sorry mate but ur screwed 

baisicly the first about 5- 10% of the Ubuntu installation process is formating ur hard drive,

sound like to me its having formating ur HDD, so it sound like u have a problem with ur HDD, want my advice? if u really want ubuntu, try installing it in VM (virtual machine) in windows, use a program like virtual box or VMware.

sorry i cant be of more assistance!!!

---

### Post by cariboo on 2008-06-02
Did you boot into safe graphics mode and try it that way? I've had the same problems that you are running into and by booting into safe graphics mode everything installed as it should.

Jim

---

### Post by 1waytikt2tickletown on 2008-06-02
> **1waytikt2tickletown said:**
> What do you mean? I just burned the .iso onto a CD-R, put it in and selected install. It does take me into the Live CD part where I can select install and look at the desktop ect...

And I think its a company called Energy who makes my PC.

> **jimbosheep101 said:**
> ok sorry mate but ur screwed 

baisicly the first about 5- 10% of the Ubuntu installation process is formating ur hard drive,

sound like to me its having formating ur HDD, so it sound like u have a problem with ur HDD, want my advice? if u really want ubuntu, try installing it in VM (virtual machine) in windows, use a program like virtual box or VMware.

sorry i cant be of more assistance!!!Hm. Will I beable to install vista again?

And I'll have a try at the booting in safe graphics mode, thanks.

---

### Post by jamewill on 2008-06-02
have one last go at installing ubuntu but using the following

1) download the alternate cd (graphical installer but older style and no live cd) from the links on the download page

2) if you are setting up a dual boot then do the following....
      i) defrag your windows partitions multiple times before starting (trust me this can make the difference)
      ii) use vista to create the blank space that ubuntu will live on....   At a minimum 10GB+RAM size but better 20GB + RAM size if you have it.    Don't forget to choose the "manual" partition option when you reach it in the ubuntu install screens...

good luck and don't give up just yet

jw

---

### Post by Lord Xeb on 2008-06-02
The easiest way I have seen to dual-boot vista and ubuntu is to use two HDD.

---

