---
title: "k3B/brasero choke on DVD-R Capacity?"
date: 2013-12-28
forum: General Help
---

### Post by r_avital on 2013-12-28
Hello all,

To minimize confusion, I'm starting a new thread on this problem.  This is where things stand right now:

1. 50-count blank DVD-R "cakebox" purchased "some years ago" -- I don't burn often, but in the past few years since the purchase I've burned dozens of DVD-R disk, including with some of my purchased DVD movies for backup.  All blank media used and referred to below is from the same package.  I don't honestly remember the advertized capacity, I'm pretty sure it's 4.5GB and I **know** they are Double Layer, (and maybe irrelevant, they are LightScribe).

2. Under Lucid (10.04) 64Bit, k3b was happily burning ISO images or copying my movies, some 2 or 3 hours in length, with no issues.

3. Made clean install of Saucy (13.10) 64Bit, on same laptop, as well as Raring (13.04) 64Bit on separate desktop PC.

4. Let's concentrate on the laptop first, since that's the exact same hardware:  I was getting the "unable to mount DVD-R location already mounted" error, and following suggestions here, I used dconf-editor to set all automount settings to False.  The error does not happen anymore.

However, both k3b and brasero, while they correctly identify the blank media as "DVD-R" complain that the media's capacity is not enough:  They report the capacity of the blank DVD-R as 4.4GB, and the ISO image I'm trying to burn is about 7.2GB.

**The "Burn" button in brasero, and the "Start" button in k3b, are grayed-out, disabled, can't use them to start the burning process.**

[LIST]
[*]libdvdread4 and libdvdcss are installed. 
[*]Used the regionset program to make sure that the DVD drive was set to any region (retion 1 in this case). 
[*]Replaced the DVD drive with a new one (again, this is a laptop running Saucy 13.10 64Bit). 
[*]Ran regionset on it as well, and set the region to 1. 
[/LIST]

Still, to no avail.  Same behavior.

On the desktop, which has 2 DVD drives and should allow me to use the "copy medium" option in k3b -- same behavior.

On both computers, if I select a smaller ISO for a source (say, an Ubuntu distro ISO), as long as it's 4.4GB or smaller, the Start/Burn buttons are available.

**However, if I run a Win-7 Ultimate VM guest OS on this desktop (Raring is the Host, Win7 is the Guest), and use a paid program (DVDNextCopy NexTech), it happily copies the approximately 130-minute movie and burns the 7.2GB ISO, on the same media, with the same hardware.**

My questions:

[LIST=1]
[*]Has anybody ever known either brasero or k3b to fail to recognize that the media is Double-Layer, and therefore can be used to burn such sources? 
[*]Do we all agree that this could not possibly be a hardware problem, or a blank-media capacity problem? 
[*]Do we all agree that this should be resolved for the next LTS? 
[/LIST]

---

### Post by coldraven on 2013-12-29
> 
[LIST=1]
[*]Has  anybody ever known either brasero or k3b to fail to recognize that the  media is Double-Layer, and therefore can be used to burn such sources?
[*]Do we all agree that this could not possibly be a hardware problem, or a blank-media capacity problem?
[*]Do we all agree that this should be resolved for the next LTS?
[/LIST]

1. You still don't know for certain if the media is dual-layer.
2. No, DVDNext has probably compressed the movie to 4.5GB 
3. Yes :)

For info you could try this
```
sudo apt-get install libcdio-utils
```
```
cd-info
```

---

### Post by Impavidus on 2013-12-29
Single layer DVDs have 4.5GB capacity, double (or dual) layer DVDs 8GB. So are your DVDs single or dual layer? (Assuming they are single-sided 12cm DVDs)

---

### Post by r_avital on 2013-12-29
Thank you both for the very useful info.  I did not realize DVDNext actually compressed the content to fit the media size.

Here is the output of cd-info with a blank DVD-R inserted, and the --dvd option:

```
[B][SIZE=2][FONT=courier new]~$ cd-info --dvd /dev/sr0
cd-info version 0.83 x86_64-pc-linux-gnu
Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
CD location   : /dev/sr0
CD driver name: GNU/Linux
   access mode: IOCTL

Vendor                      : ATAPI   
Model                       : iHAS424   B     
Revision                    : GL1A
Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : Yes

Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : Yes
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : Yes

Writing....
  Can write CD-RW                         : Yes
  Can write DVD-R                         : Yes
  Can write DVD-RAM                       : Yes
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No
__________________________________

Disc mode is listed as: DVD-R
++ WARN: error in ioctl CDROMREADTOCHDR: Input/output error

cd-info: Can't get first track number. I give up.[/FONT][/SIZE][/B]
```
I can't find any indication on this as to whether the media is single or double-layer (silly label fell off the spindle-box years ago).  I guess I have to accept that the media is single-layer, unless anyone can tell me how else to find out?

[Incidentally, I tried the same with an actual movie DVD, and got more interesting output instead of the error at the bottom]

EDIT:  Ok, my apologies, I've been "lying" - took a closer look at the markings on my blank media, they are in fact DVD+R and not DVD-R as I stated earlier.  My bad.  How is that reflected in the output of cd-info above, if at all?

I'm finding out that only DVD+R media has the 8.5GB capacity, which means my DVD drives should be able to handle them, correct?

Alternately, instead of me pestering you all with these dumb questions, you could point me to some info page on the web, that would be fine and dandy.

Thanks again :)

---

### Post by mc4man on 2013-12-29
1st -  don't the disks themselves say anything, ie. a label?

Otherwise - install dvd+rw-tools if not already
With blank disc in drive run (assumes device is /dev/sr0
```
dvd+rw-mediainfo /dev/sr0
```

Ex. on Verbatim dvd+r dl
> $ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [HL-DT-ST][BD-RE BT20N     ][KV01]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         2Bh, DVD+R Double Layer
 Media ID:              MKM/001
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.4x1385=3324KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     2.4x1385=3324KB/s@[0 -> 219903]
                        4.0x1385=5540KB/s@[219904 -> 3953919]
                        2.4x1385=3324KB/s@[3953920 -> 4173823]
 Speed Descriptor#0:    02/4173823 R@8.0x1385=11079KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    02/4173823 R@8.0x1385=11079KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2086912*2KB=4273995776
DVD+R DOUBLE LAYER BOUNDARY INFORMATION:
 L0 Data Zone Capacity: 2086912*2KB, can still be set
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           4173824*2KB
 Track Size:            4173824*2KB
 ROM Compatibility LBA: 266240
READ CAPACITY:          0*2048=0


---

### Post by r_avital on 2013-12-29
> **mc4man said:**
> 1st -  don't the disks themselves say anything, ie. a label?

Thanks, mc4man, the label fell off years ago, so instead of guessing I used your suggestion, and here's the output of dvd+rw-mediainfo /dev/sr0 with two different disks, one blank, one used.  I won't bore you with the whole thing, just the relevant portions, that led to a "discovery" I stumbled upon that puts a new twist on it:

```

THE BLANK DISK:
~$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [ATAPI   ][iHAS424   B     ][GL1A]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Media ID:              MCC 03RG20  

[etc]

THE RECORDED DISK
~$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [ATAPI   ][iHAS424   B     ][GL1A]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              MCC/004

[etc]

```

Yep.  One is DVD-R and the other is DVD+R.  And just so I'm not taken for a madman, see the scans of the hubs of these two disks: [IMG]https://dl.dropboxusercontent.com/u/88563407/hubs1.png[/IMG]

Yes, I can swear in court that these two came from the same spindle-box.  At any rate, I think most of my questions on this have been answered, namely:

1. My hardware (DVD drives) should be able to handle both kinds of media (+R and -R), as well as Double-Layer media.
2. The fact that some third-party software (like DVDNextTech) compresses a movie to fit on some media does not prove that the media itself has the required capacity for k3b or brasero to burn the same movie on the same media.

I'll mark this as solved, but if anyone disagrees with anything in the above, by all means, please enlighten me :)

---

### Post by mc4man on 2013-12-30
Yeah,  you'll either have to shrink vid down to dvd-5 size to burn on those disks or get some dvd-9 (dl) disks.

If the later,  I've no idea how brasero/kb3 do with dl's for dvd video, never have used or even wanted to waste a disk on to see.
Always used ImgBurn, either in windows or thru wine for all dvd burns, especially for dl where the layer break location can matter.
(imgburn lets you preview & pick from avail. valid break points if more than one.

As far as dl media, I'd only use Verbatim, preferably from individual cd case packs, (typically 3 to a box),  or from smallest cake box - 10 per cake.

---

### Post by coldraven on 2013-12-30
The Nero disc burning program used to have a disc info utility that could be run as a standalone program.
It was very good, it gave all the info that you could possibly want. I don't have my XP VM installed at the moment so I cannot verify if this is still the case.

---

### Post by r_avital on 2013-12-30
Thank you mc4man and coldraven, I finally understand.  I also found some fascinating details here on handling many different aspects of burning and formatting DVD (such as booktype) for the greatest playback compatibility:[http://www.afterdawn.com/guides/archive/how_to_set_booktype_for_blank_dvd_r_w__media.cfm](http://www.afterdawn.com/guides/archive/how_to_set_booktype_for_blank_dvd_r_w__media.cfm)

I'm going to give imgburn a try -- I dont' believe it will do a straight DVD to DVD copy (could be wrong, I'll check), but it definitely will handle an ISO image burn to the smaller capacity DVD media.

I'm also going to get a few DL (dvd9) blank disks to experiment with k3b (which I favor over brasero), just to see if the software can handle it.  I'll post results.

coldraven, according to this link, Nero still does that, but you have to spring for the full commercial product, or ask for a Serial Number just to try out the trial version: [http://www.afterdawn.com/software/cd_dvd/burning/nero.cfm](http://www.afterdawn.com/software/cd_dvd/burning/nero.cfm)

I haven't tried any of it yet, but the standalone info-tool is available here and seems to be freeware:
[http://www.techspot.com/downloads.php?action=download_now&id=578&evp=6def2b052ed7ff49b9890b4d6590ca60&file=1](http://www.techspot.com/downloads.php?action=download_now&id=578&evp=6def2b052ed7ff49b9890b4d6590ca60&file=1)

Thanks again!

---

