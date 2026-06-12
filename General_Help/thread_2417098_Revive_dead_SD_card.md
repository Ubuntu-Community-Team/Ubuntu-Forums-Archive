---
title: "Revive dead SD card?"
date: 2019-04-20
forum: General Help
---

### Post by francktheminer on 2019-04-20
Hey,
I'm not sure if this is the right forum to post this on, so feel free to move it around.
Now  to the problem. I have a 128 GB Sandisk Ultra MicroSD, and it seems to  be dead. I've tried formating it on Windows 10, macOS Mojave and Ubuntu  18.04.2 LTS, and the tools I've used were a regular File Explorer  format, diskmgmt.msc, diskpart on the command line and the SD Formatter  tool from the SD Association for Windows, Disk Utility and the same SD  Formatter on mac, both Disks and GParted for Ubuntu and as a long shot I  tried using a blank .img through Windows 32 Disk Imager on Windows and dd on Ubuntu. I tried NTFS, FAT, exFAT, ext4 and HFS+, but all of them returned an error of some sort.
Aditionally, as an act of despair I tried both my Android Phone (running Android 8) and a Zoom H1n Audio Recorder to format them. On Ubuntu on the disks app I made a full format (took around 12 hours, as it was writing at around 2 MB/s), so you can see I already tried most options.
Has anyone got any idea as to how I can bring it back to live, or whether or not it's even able to be used again?

---

### Post by TheFu on 2019-04-20
He's dead Jim.

---

### Post by Autodave on 2019-04-20
Moment of silence please..........

---

### Post by QIII on 2019-04-20
Dispose of it in an environmentally responsible manner.

---

### Post by francktheminer on 2019-04-20
Well I'm currently arranging the funeral, but I've got one last question... I had made a test using Blackmagic's Disk Speed test tool with that card and then compared it to a brand new one. The old one had 0.9 MB/s read 80 write, when the new one was getting 9 Read 80 write... Big difference, which lead me to think it was just the card that was full, kind of like when you had to defrag an old hard drive so that it ran faster. I then went to format it as exFAT on Windows, and that got me thinking... Because it was working """"perfectly"""" fine moments before, was it just a coincidence that it died while it was being formatted, or was it really because it touched on the file system aspect of the card that did the final blow? Post your conspiracy theories down below

---

### Post by TheFu on 2019-04-20
All flash media has a write count limit.  I've burned up well-regarded, USB flash storage in under a year which claimed to use load levelling and had support for 10,000+ write cycles.  I've seen SSDs fail in under 3 yrs.  I also have some USB flash storage that is 5+ yrs old, but not abused with lots of writes, so it keeps working.

One of the failed SSDs gave no warning.  It was working, then it never worked again. Not even read. 100% data loss, except I had automatic, daily, versioned, backups, so the failure was a minor inconvenience and cost of replacement storage. Nothing important lost.

My LUG had a discussion last week about ways to ensure data on spinning disks was truly wiped.  A few of the answers:
* Shoot it with whatever firearm is handy, provided your laws allow it. I do live in Squidbilly-Land where almost everyone has lots-o-guns.
* Drill 5 holes into it with 3/5" drill bit
* Use dban - Darik's Boot and Nuke
* Use dd if=/dev/urandom of=/dev/sdZ  bs=1M
* oxygen acetylene torch to raise the temperature passed the point where HDD data can be retained. [https://www.youtube.com/watch?v=gc9mSZO45vE](https://www.youtube.com/watch?v=gc9mSZO45vE)
* Thermite - always a crowd pleaser. [https://www.youtube.com/watch?v=toYk1yJKYTc](https://www.youtube.com/watch?v=toYk1yJKYTc)

Then they started getting silly. ;)

We have a few spooks in the LUG. They suggested that dd and dban weren't sufficient because there are layers of data and the longer data sits with any specific value, the more it becomes memorized by the physical media.  Not good enough for super-secret govt needs, but certainly good enough for my needs at home or work ... er ... these days.  
They also suggested that drilling holes and firearms would leave huge amounts of data still on the platters, from which information could still be gathered. Sure, the drive wouldn't work, but for a determined organization, lots of data still exists.

Plus, you might want to consider using strong encryption for the data on all new, portable, devices.  Then the solution becomes securely wiping the just the header where the keys are stored and not the entire storage media.

Anyway, destroying data storage devices is something the entire family should enjoy together, sorta like marshmallows around a campfire.

---

### Post by Autodave on 2019-04-20
I had my share of failures.  But, I have an 8 year old USB that has had tons of data written to it and erased from it.  It was machine washed and then dried in an electric drier.  Still works great.  Ya just never know.

---

### Post by rbmorse on 2019-04-20
So, this is a micro-SD card.  How are you interfacing it with the machine?

---

### Post by HermanAB on 2019-04-20
Jim, he's dead.

---

### Post by VMC on 2019-04-20
*Jed is dead*. Pulp Fiction. I loved how that that line was setup. My best and fastest USB flash died recently, and I foolishly thought I could revive it. A lesson in futility.

---

### Post by rbmorse on 2019-04-21
IF....you have a USB flash memory device (especially one made by Sandisk) that you have been interfacing through a USB 3.X port. and it appears to have died, try it in a USB2.X  port.  Sometimes the USB 3 controller on the device will die, but the 2.X port will still work. I've been able to recover data from a couple of Sandisk flash devices in the last year or so in this way. .  

Of course, the device gets recycled after I get the data off.

---

### Post by francktheminer on 2019-04-21
> **rbmorse said:**
> So, this is a micro-SD card.  How are you interfacing it with the machine?

I'm using the microSD > SD adapter that came with the new microSD... They're the same brand, if that may raise some red flags

---

### Post by TheFu on 2019-04-21
> **francktheminer said:**
> I'm using the microSD > SD adapter that came with the new microSD... They're the same brand, if that may raise some red flags

Definitely try some different versions of those and I'd try a microSD to USB converter too.  These things are extremely cheap.  They really should be $0.25/ea, but expect to pay $3+/ea.

I've had some loose stuff with the micro-to-SD converters, but you did try it in a phone without the convert, correct? Yep. I see that in the OP.

Dead, dead, dead.

---

### Post by Kris_M on 2019-04-21
The only trick I have is to boot a stand-alone gparted on a usb stick, and remove/redo its MBR, and re-format it. If that doesn't work, I throw it. It's a shame. How did you kill it?

---

### Post by cmcanulty on 2019-04-22
Here they are 3 for .74

[https://www.ebay.com/itm/3PCS-Lot-Memory-Card-Reader-to-USB-2-0-Adapter-for-Micro-SD-TF/233087733730?hash=item36451c8fe2:g:OKMAAOSwkSlbBSpN]("https://www.ebay.com/itm/3PCS-Lot-Memory-Card-Reader-to-USB-2-0-Adapter-for-Micro-SD-TF/233087733730?hash=item36451c8fe2:g:OKMAAOSwkSlbBSpN")

---

### Post by TheFu on 2019-04-23
> **cmcanulty said:**
> Here they are 3 for .74

[https://www.ebay.com/itm/3PCS-Lot-Memory-Card-Reader-to-USB-2-0-Adapter-for-Micro-SD-TF/233087733730?hash=item36451c8fe2:g:OKMAAOSwkSlbBSpN]("https://www.ebay.com/itm/3PCS-Lot-Memory-Card-Reader-to-USB-2-0-Adapter-for-Micro-SD-TF/233087733730?hash=item36451c8fe2:g:OKMAAOSwkSlbBSpN")

Someone in my LUG bought a 50-pak of these and handed them out.  The ones I got were a little too small to insert microSD cards.  I had one of these from a Sandisk microSD purchase a few years earlier that fit perfectly. Appeared to be identical. The transfers are really slow for these cheaper versions.  For me, it was worth getting a USB3 device for a little more cash. Unfortunately, the size of the USB3 device was much larger since they insisted on adding 5 other slots on it too.  

At least that was my experience with them.

---

