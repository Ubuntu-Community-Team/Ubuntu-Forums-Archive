---
title: "tried upgrading to lubuntu 14.04 and now nothing works"
date: 2016-02-03
forum: General Help
---

### Post by iuval on 2016-02-03
Someone here suggested I upgrade to lubuntu 15.xx, but my package manager suggested I upgrade to 14.04. It took several hours, gave some error messages, and finally I get a blank screen after restarting the computer. It asks if I want to report the system error (I said yes). What to do? I was able to press ctl alt delete and see running processes, but that is about it.

---

### Post by ian-weisser on 2016-02-03
More information about 'some error messages' would really help. We are not psychic.
If you have any files in /var/crash, please attach the most recent to this thread.

In your previous thread you had perhaps out-of-memory issues while running a CPU-intensive job overnight. You upgraded from 12.04 to 14.04 before investigating. Perhaps you have bad RAM, perhaps you have a loose disk cable or a dying hard drive or many other possible hardware (or software) issues.

We can help you rule out many possible causes...if you are willing.

---

### Post by iuval on 2016-02-04
Thanks, ian. I can't access any files now. When I first turn on the computer, I get "error:file not found. Press any key to continue". I press a key, I get the login box, I login. Then a box appears saying "system program problem detected, do you want to report the problem now?" Then nothing-blank screen. Maybe I should download 14.04 on another computer then transfer through a memory stick. How to do that? Will it try booting off the memory stick by default?

I have a guess of what might have gone wrong. I had a usb wifi stick connected and didn't disconnect it till after it failed to boot. Maybe it was trying to boot from it?

---

### Post by iuval on 2016-02-04
To be more precise, the screen is not completely blank. It has the mouse cursor and some Lubuntu swirly ribbons on it and it's blue.

---

### Post by iuval on 2016-02-04
I don't think I have bad ram because I didn't see that when I ran the diagnostics prior to this OS "upgrade". Mathematica was crashing because I am doing some intensive General Relativity calculations in 5 dimensions that require more memory than I had in RAM, it tried using virtual memory (which means from the hard drive, right?) and it ran out of that as well, or was thrashing and another process caught it and killed it

---

### Post by iuval on 2016-02-04
Anyway, please advise on what I should do, to hopefully reinstall and not lose my data.

---

### Post by ian-weisser on 2016-02-04
See Post #2. More information on those errors, and the most recent .crash file, if any.

---

### Post by iuval on 2016-02-04
How do I access any information? I can't do anything. Is there a way to input something before it boots to get me a terminal screen?

---

### Post by iuval on 2016-02-04
There are no menus available. Is there some key combination that pops up a terminal?

---

### Post by ian-weisser on 2016-02-04
If you cannot login to a graphical desktop, you cannot copy-and-paste text into a web browser. That will slow you down a lot.

You have a couple options.

1) You can boot your LiveInstall media ('Try Ubuntu') to get to a graphical desktop. Mount your hard drive, and proceed from there.

2) You can reinstall again, and take detailed notes of the error messages (if any).

Let us know which way you want.

---

### Post by iuval on 2016-02-04
Can you give a bit more detail about each of these? For 2) do I download it on another computer and then transfer to a memory stick?
For 1) do I do the same thing as 2) but download a more primitive version of the OS? What is the link?

---

### Post by iuval on 2016-02-04
I don't know what Liveinstall media is. When I first got Ubuntu I had a memory stick with the OS on it. But I don't have it anymore. By option 2, do you mean I download 14.04 unto a memory stick from another computer and then transfer it to my computer? Would it boot from the memory stick? Or do I need to do something after I turn the computer on to help it along?

---

### Post by ian-weisser on 2016-02-04
Yes, you use a USB stick. Since you "don't have it anymore," you must make a new one exactly the same way you made the old one.

When you booted from that stick, you should have seen a choice 'Try Ubuntu' and 'Install Ubuntu'. Click 'Try Ubuntu' to enter a test environment. The test environment runs from the USB stick, not your hard drive.

For most users, it's much easier than moving your hard drive to a different computer merely to paste log enteires into a web browser.
Maybe it's not easier for you. You tell us what's easier for you.

---

### Post by iuval on 2016-02-11
Oh, I accidentally replied to the older thread, can someone please close that one (how do I prevent my computer from logging out) Here is what I found so far:
So I was able to get live debian linux onto a usb stick and then boot  from it. But just like lububtu 14.04, it can't boot. It gets stalled on  partitioning the hard drive. I am trying to find out what is wrong. The  hard drive was fine before that. This is what it said for memory:
user@debian:~$ sudo dmidecode -t memory
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x000F, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 1

Handle 0x0010, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000F
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: 1
    Locator: M1
    Bank Locator: Bank 0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer:                 
    Serial Number:         
    Asset Tag:       
    Part Number:                   

It also shows the hard drive as partitioned into a 4Gb and a 246Gb  partitions, with the 4Gb partition behaving nicely. But the 246Gb  partition gives the following error when I try to open it in the file  manager:
Error mounting /dev/sda1 at  /media/user/36f962f5-e6cf-4302-b71e-8eb44f83093f: Command-line `mount -t  "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1"  "/media/user/36f962f5-e6cf-4302-b71e-8eb44f83093f"' exited with non-zero  exit status 32: mount: wrong fs type, bad option, bad superblock on  /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

Any ideas on what to do next? I would like to avoid buying another hard  drive. I actually have an extra one but in another state.

---

### Post by furtom on 2016-02-11
The thing about bad RAM is, it's hard to diagnose, is not duplicable, and each situation fails in unique and pretty much random ways.

I would certainly suspect bad RAM. You say you did the memory check before installation? I hate to ask a "jerky" question, but are you 100 percent sure it passed?

---

### Post by iuval on 2016-02-12
I didn't do a memory check before either lubuntu 14.04 installation, or the debian installation, but doesn't the software do that automatically? Anyway I have live debian now from the USB stick, so I can check anything. Please let me know how to check. Isn't the dmidecode -t memory a way to check?

---

### Post by furtom on 2016-02-12
It does not do it automatically. It takes a bit of time.

You don't need any command in the terminal. When you boot from the usb, it's an option under the *try without installing* and *install *options. Just select it and wait for the result.

memtester is the test for RAM, BTW, but it's better to do it from the live media instead of when already booted up.

EDIT: I forgot you said you had a Debian image. That's OK, the memtest option is still there, but it may look a little different than I've described.

---

### Post by iuval on 2016-02-12
Thanks, Tom. It failed the memory test. There is no reason to suspect bad hard drive, since I was able to retrieve everything from it with live debian, except that after it tried to partition it, I couldn't open one of the partitions in the file manager and got the error. The bad memory hypothesis would also explain why Mathematica was thrashing and finally crashing. I opened up this little laptop and I can't find what I remember RAM looks like, but it's been a while since I last looked at RAM chips. Could the RAM be built into the CPU chips (looks like it has two CPUs, one larger than the other)? As far as I remember, RAM can be easily taken in and out of slots on the motherboard.

---

### Post by iuval on 2016-02-12
I actually found the RAM on the back of the motherboard. It is indeed 2Gb. Will try replacing.

---

### Post by iuval on 2016-02-13
Replaced RAM, still failing the installation to hard drive. It's saying can't install the "grub boot" package. Does this mean it's the hard drive?

---

### Post by ian-weisser on 2016-02-14
Have you run the memory test on the new RAM?

---

### Post by iuval on 2016-02-14
Yes. It doesn't say the same thing as before about a bad pointer. It says something about signal 11 (segmentation fault). Unfortunately it keeps looping the screen output (there is more than one screen page of it) so I can't read it carefully.

---

### Post by ian-weisser on 2016-02-14
A segmentation fault is a program failure, not a memory test failure, and can have many possible causes.
Are you really using Memtest from the GRUB menu, or are you using some other method of memory testing?

---

### Post by iuval on 2016-02-14
Once I tell the bios that I want to boot from the USB device, it gives me a menu of things to do, including default, live install, and memtest. Is that the "GRUB menu"?

---

### Post by ian-weisser on 2016-02-14
The GRUB menu look something like [this]("http://i46.tinypic.com/35mi1vs.jpg").

Yours may differ a bit.
See how it says GRUB at the top?
See the memtest option?

---

### Post by iuval on 2016-02-14
It is not that. It says UNetbootin at the top and the options underneath are
Default
Live (686-pae failsafe)
Graphical install
Memory Diagnostic Tool (memtest86+)

---

### Post by iuval on 2016-02-14
The hard drive looks good right now from the file manager. I look in  /media/usr/boot on it and I find all sorts of programs including  memtest86+.bin, but I cant type that in a terminal (I guess it is not in  /bin on the usb or the hard drive). Should I make it an executable in  the boot directory and try to run it?

---

### Post by ian-weisser on 2016-02-14
Ah, you are booting the installer media. Of course. Yes, run memtest86+.
If memtest86+ segfaults, then there are several possible causes - including a failing USB stick. Create a new installer on a different USB stick and try memtest86+ again.

It is a waste of your time to guess about faulty hardware. Be methodical, and prove your USB stick, RAM, and hard drive work before trying to install.

---

### Post by iuval on 2016-02-14
I tried chmod +x memtest86+.bin but it says file not found when I tried to run it on the hard drive. On the USB it has no .bin file by that name (at least in /usr/lib) just an .iso and a .elf file.

---

### Post by ian-weisser on 2016-02-14
If you cannot run memtest86 from the USB stick's boot menu, then create a new USB stick.

Do not bother trying to chmod memtest, nor run it from the 'Try Ubuntu' environment. It's not meant to work that way.

Think about it - how can memtest test the RAM that the Ubuntu environment is loaded into? It cannot. No OS can be running when memtest is running.

---

### Post by iuval on 2016-02-14
I didn't know the OS environment (debian in this case, not Ubuntu--that was what I started with, but then someone told me to try debian) is loaded into the RAM. In any case, I can run memtest86+ from the USB stick boot menu, but it loops and gives a seg fault. I will try another memory stick.

---

### Post by iuval on 2016-02-15
With the new 16Gb memory stick, the same thing happens with memtest (seg fault). The attempted installation from live debian onto the hard drive fails at the grub boot install, as before, and also (I didn't mention this before) fails to initialize the network--even when I plug in the wireless usb stick. If I prepare the usb stick with a non-live debian installation, it is able to complete so the computer is bootable from hard drive, but since it can't find the network, all I have is a terminal. I can't check my hard drive without internet access, can I?

So so far I have put in a new RAM card and booted from a new USB. Why is it still failing memory test? What should I do next?

---

### Post by iuval on 2016-02-15
I meant to say that I can't download those packages to check the hard drive without internet

---

### Post by iuval on 2016-02-15
Or maybe I can get them from another computer with internet, and transfer them through a usb memory stick?

---

### Post by iuval on 2016-02-16
And remember, all this started with attempting to install lubuntu 14.04.

---

### Post by ian-weisser on 2016-02-16
...on faulty hardware.

---

### Post by iuval on 2016-02-16
OK, but why was it working before? And what specifically is not working anymore?

---

### Post by Geoffrey_Arndt on 2016-02-16
Thinking a bit out of the box, but, if you have dvd/cd driive on your PC . . . _it can be a more stable way on older equipment to install any Linux distro_.    I would suggest to use another PC to download a new iso for xubuntu 15.10 or lubuntu 15.10.   Either should run on your box.

IF that iso still won't load up and initiate and complete a new install . . . then do the following to test your hardware:

Best Solution (in my humble opinion):

>   Goto [http://partedmagic.com/](http://partedmagic.com/)

The above is an excellent tool to use for system testing, rescue, etc.   Very polished, very fast (loads and runs from ram).   Note - - it does cost a small amount to get the iso file from the website . . about $10.00 the last I checked.   **_But worth it_** in my view as it is the best of the Linux rescue media that I've seen (has all the essential tools & is not buggy as some are).  Burn the iso to a CD or DVD (preferably), and only use usb-stick if needed.    Don't worry about the wireless dongle to run the live system - - be sure to accept the defaults for loading to ram.

>   Scan the menus for "memtester" & run it if needed.   It's just not certain at this point that you actually have a hardware issue.

Then, let us know results.

---

### Post by iuval on 2016-02-16
Thanks! Unfortunately I do not have a CD/dvd drive. I may buy the rescue media you suggest.

---

### Post by iuval on 2016-02-16
OK, some progress. First, the failed memtest happened the same way (seg fault and endless looping) when I tried loading the super GRUB2 boot software from a usb stick. I loaded the software onto the stick on a mac, and though I told it not to erase the live debian, I think it did anyway.  A friend told me the GRUB software often fails and I should try this other one... This leads me to believe that the "failure" might not have anything to do with the state of my (now new) memory.

Next I decided to try Lubuntu live (recall the first time I tried to upgrade to 14.04 it was not live and it crashed my computer), so I loaded the usb stick on the mac with 14.04, and booted from it on my inspiron mini10. It is nice in two ways:
1. It detects my wi fi network usb stick so I can connect to internet via that computer.
2. It has disk diagnostics (SMART data and self tests) as a GUI so I don't have to waste time reading man pages on how to use it.  I did the short self-test (two other options are "extended" and "conveyance", whatever that means) on my hard drive. The self assessment is "threshold not exceeded". The overall assessment is "disk is OK, one bad sector".
More details
Attribute                 Value
Read error rate        0
Spinup time             1 sec
Start/Stop Count      5473
Reallocated sectors   0
seek error rate         0
power-on hours        7 months 18 days
spinup retry count    0
calibration retry count 0
power cycle count      5271
G-sense error rate     2914
Power-off retract count 577
Load/unload cycle count 606677
temperature              41C
reallocation count      0
current pending sector count 1 
uncorrectable sector count 0
UDMA crc error rate   2
white error rate         0

---

### Post by iuval on 2016-02-16
So based on this diagnostic, what should I do? Do I need to replace hard drive, or is the bad sector repairable?

---

### Post by iuval on 2016-02-16
to clarify: I did not ask for a memtest, I just told the menu to boot from USB, then the only option on the next menu was "default". When I selected that it gave me the same output as previously when I was asking for a memtest. Is it trying to do a memtest but the memory is loaded with something else (first it was the live debian, now the super GRUB 2) so it crashes? In which case it should not allow you to do a memtest when you are booting from usb?

---

### Post by furtom on 2016-02-17
Is it possible it's trying to install grub to the USB?

---

### Post by iuval on 2016-02-17
Hell if I know, Tom. I can't really see the output because of the looping, but I do see the seffault. I don't know how I was supposed to use the super GRUB2. Perhaps once I have the hard drive loaded with everything else and the regular GRUB fails, then I should load the super GRUB2 iso file from another usb? But maybe all this is moot now that I found a bad sector on my hard drive? Maybe I just need to deal with that? How?

---

### Post by furtom on 2016-02-17
You can mark bad sectors as unusable and continue to use the disk, but I've found once you have bad sectors, you have a bad disk and it's only a matter of time.

You can try to mark the sectors as bad and continue on. Try [this page]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/"). but if it's messing up grub, I don't know if it will work. no harm in trying, however.

Or you can bite the bullet and get a new hd. You'll probably be in good shape if you do. New RAM and new hard disk. :)

---

### Post by iuval on 2016-02-17
I am having my friend from CA mail me my extra hard drive that I left there. I already bought and installed new RAM. Can you look at that SMART report I posted and tell whether there is anything else to worry about on the hard drive? For example the Gsense measure was 2914. What does it mean? Is it something that could be bad on the motherboard?

I am also wondering what happened to the hard drive. Could it have been damaged by a thrashing Mathematica session that ran out of RAM? But then why did everything (including other less intensive Mathematica computations) still work until I tried installing lubuntu 14.04? And if the hard drive die as a result of Mathematica thrashing, as a result of not enough RAM, maybe I need to get a computer with more RAM, or can I just put in a RAM card with more Gb into the present slot?

---

### Post by furtom on 2016-02-17
Mostly, I have no idea. :)

I'd doubt Mathmatica killed your hard drive. I'm sure Ubuntu didn't. Rather, the intensive workload and then installation process uncovered problems that were lying dormant. How old is the hard drive?

I don't know too much about G-sense. Maybe someone can chime in with what is a normal rate. According to this [Web page]("https://kb.acronis.com/content/9126"):

> This parameter is considered informational by the most hardware vendors. Although degradation of this parameter can be an indicator of drive aging and/or potential electromechanical problems, it does not directly indicate imminent drive failure. Regular backup is recommended. Pay closer attention to other parameters and overall drive health.

I suspect the actual rate is not as important as the rate's degradation over time, but this is just an inference. 

Google is your friend. :)

---

### Post by matt_symes on 2016-02-19
Hi

> **furtom said:**
> You can mark bad sectors as unusable and continue to use the disk, but I've found once you have bad sectors, you have a bad disk and it's only a matter of time.

You can try to mark the sectors as bad and continue on. Try [this page]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/"). but if it's messing up grub, I don't know if it will work. no harm in trying, however.

Or you can bite the bullet and get a new hd. You'll probably be in good shape if you do. New RAM and new hard disk. :)

This is good advice.

Kind regards.

---

### Post by iuval on 2016-02-29
It was not a hardware problem. It was something about the BIOS that was confusing all the installers. I'm not sure what it was but I changed a few things and was able to install lubuntu 15.02. What a waste of my time.

---

### Post by mörgæs on 2016-03-01
Congratulations. I hope you mean 15.10 and not 15.04, which is out of support.

---

