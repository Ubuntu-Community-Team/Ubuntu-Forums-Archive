---
title: "&quot;file did not match its source copy&quot;"
date: 2021-06-02
forum: General Help
---

### Post by sytheii on 2021-06-02
***Forgive me if this is answered elsewhere in a newer thread, I found replies to the question but from a decade ago.***

Have been trying to ressurrect an old tower computer.

I received this message on ubuntu install from a bootable USB live made with rufus and ubuntu newest amd64 image 20.04.2.0, made the usb stick fresh a few days ago...have tried with different sticks same deal

**["file did not match its source copy"]("https://ubuntuforums.org/showthread.php?t=1243550")**


etc ect, abort, retry, cancel, i have tried a few times to install and have tried retry...i have had 1 successful install, but then upgraded to a SSD and install hangs at various points each time i try ...the files it has problems changes each time too. Certain image is clean....ran a hash check, looks good.

Is my SSD really garbage? whats going on?

Please help

---

### Post by Bashing-om on 2021-06-02
sytheii; Hello -

What results show ?
Boot the installer and in the boot menu is "check disk for defects"

Does the check return clean ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sytheii on 2021-06-02
Here's photos of process for install...let's see if it installs this time...in pdf

[https://www.dropbox.com/s/xwinn8c9z4f8mye/ubuntu.pdf?dl=0](https://www.dropbox.com/s/xwinn8c9z4f8mye/ubuntu.pdf?dl=0)

---

### Post by guiverc on 2021-06-02
Alas 20.04 doesn't have the "*check disk for defects*" option prior releases do

It's automatic; so you should see the check occur before it fully boots... Did it complete successfully?  

I'd recommend not skipping it with ^C as the check doesn't take long and saves hours-weeks of problem-solving so I think it as cheap insurance.

At the end it reports "**Check finished: no errors found.**" (then boots to the try/install option you selected)

FYI:  *It doesn't check your ssd/disk for issues, but the installation media, to ensure you had a successful write of the ISO to media.. in my experience about 5-8% of ISO writes fail as thumb-drive media is made mostly for price/cost.*

---

### Post by scorp123 on 2021-06-03
> **sytheii said:**
>  I received this message on ubuntu install from a bootable USB live ... 
There's your problem, very likely. Most USB sticks are cheaply made and not exactly "high quality". It's possible your USB stick is at fault. Try a different one?

> **sytheii said:**
>  Is my SSD really garbage? whats going on?

If you get the same (or similar) errors on the same PC while trying a different USB stick ... yes, it might be the SSD.
If you get no errors when trying the installation with a different stick / different media (e.g. DVD?) then it was the USB-stick.

My guess would be that it's the USB-stick. USB-sticks are rarely "high quality" and not meant to last long. Try a different one? Or try with a different media, e.g. DVD?

---

### Post by sytheii on 2021-06-03
> **scorp123 said:**
> There's your problem, very likely. Most USB sticks are cheaply made and not exactly "high quality". It's possible your USB stick is at fault. Try a different one?



If you get the same (or similar) errors on the same PC while trying a different USB stick ... yes, it might be the SSD.
If you get no errors when trying the installation with a different stick / different media (e.g. DVD?) then it was the USB-stick.

My guess would be that it's the USB-stick. USB-sticks are rarely "high quality" and not meant to last long. Try a different one? Or try with a different media, e.g. DVD?

I will try with a newly purchased one... honestly I have like a large coin purse with tons of them in there...like candy...most are old (some a decade old) so that's probably something to consider... although once I put in the SSD I have made fresh Ubuntu pen drives, (3) SanDisk, pntyand a generic...and each time I get the same messages from the Ubuntu install...dis y'all look at the images I made of the install process?

Looks like even with those messages the latest install went through and now I've got Ubuntu on the tower...

Although after some deliberation I decided to splurge on a new board and processor and a WD m.2 ssd...so I will be trying the same process over again once I get all the parts in. 

Can someone take a look at the images I put up and tell me what that represents? 

Is there maybe just an odd way that the read/write happens where when it checks what got copied from USB to HD that something gets corrupted?  Maybe it's USB to SSD? Maybe it's SSDs in particular?

I guess the real question is when you try "retry" and you subsequently don't get the same error message with the same file as reference, can you assume that it successfully copied and there's nothing to worry about?

I guess that's what I'm trying to figure out.

---

### Post by sytheii on 2021-06-03
Lol system reported multiple internal errors after it's first boot and now after updating some software components it won't reboot st all haha

---

### Post by scorp123 on 2021-06-04
> **sytheii said:**
> Lol system reported multiple internal errors after it's first boot ...

That would point to the SSD being faulty...  Can you run a live session and perform a check on the SSD?

---

### Post by sytheii on 2021-06-06
> **scorp123 said:**
> That would point to the SSD being faulty...  Can you run a live session and perform a check on the SSD?

Ive already returned the cheapo thing. Got a M.2 Western Digital for a new mboard as a replacement...hopefully it works better.

how would i run a check btw?
which util?

---

### Post by scorp123 on 2021-06-06
> **sytheii said:**
>  how would i run a check btw?
which util?

You could use **smartmontools **.... You'd maybe have to install it into the live session first, it might not be there per default. Or maybe it is? I honestly don't know. If it's not there:

```
sudo apt update && sudo apt install smartmontools
```

Once this is installed you can check if the tool and your new SSD can talk to each other. Assuming your new SSD is "/dev/sda" then the command would be:
```
sudo smartctl -i /dev/sda
```

You should get some output, something like this:

```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-74-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Marvell based SanDisk SSDs
Device Model:     SanDisk SD8SB8U-512G-1006
Serial Number:    163203424145
LU WWN Device Id: 5 001b44 4a42d7f6b
Firmware Version: X4120006
User Capacity:    512’110’190’592 bytes [512 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Jun  6 16:46:52 2021 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

With that out of the way, we can ask **smartctl** to tell us how long testing that disk would take ...
```
sudo smartctl -c /dev/sda
```

You should get some output saying something like ... (irrelevant stuff cut from output)
```
[...]
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  33) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
[...]
```

To trigger that "extended test" we can do:
```
sudo smartctl -t long /dev/sda
```

The system should respond with something like ...
```

smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-74-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 33 minutes for test to complete.
Test will complete after Sun Jun  6 17:35:13 2021 CEST
Use smartctl -X to abort test.

```

You can watch current test results with:
```
sudo smartctl -a /dev/sda
```

If you do that you should see some statistics about your SSD and how the test is progressing.

To abort the tests you can issue this command:
```
sudo smartctl -X /dev/sda
```

---

### Post by sytheii on 2021-06-11
It was bargain bin ssd that was giving me grief. New components fixed issues. Lightning fast install of Ubuntu.

[https://ibb.co/gRqcKpn](https://ibb.co/gRqcKpn)

---

### Post by Bashing-om on 2021-06-11
sytheii; Hey Hey :D

Good of you to return and provide the resolution.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]ain't nuthin but a thing
[/INDENT]

---

