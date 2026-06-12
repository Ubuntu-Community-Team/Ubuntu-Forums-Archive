---
title: "CD Burner"
date: 2006-12-06
forum: General Help
---

### Post by disc on 2006-12-06
I have a problem, my CD Burner will not burn. Whenever I burn an image or files to a CD, it does not give me an error. However, every CD that I've burned does not work. Audio CD's will not play, and data CDs appear black when I put them in my Windows box. The following is what the terminal spits at me when I type in 'cdrecord -prcap'.

```

cdrecord -prcap
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX215E5 '
Revision       : '6.1G'
Device seems to be: Generic mmc CD-RW.

Drive capabilities, per MMC-2 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does not read DVD-ROM media
  Does not read DVD-R media
  Does not write DVD-R media
  Does not read DVD-RAM media
  Does not write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does not return R-W subcode de-interleaved and error-corrected
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does not support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 255
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  8467 kB/s (CD  48x, DVD  6x)
  Current read  speed:  8467 kB/s (CD  48x, DVD  6x)
  Maximum write speed:  8467 kB/s (CD  48x, DVD  6x)
  Current write speed:  8467 kB/s (CD  48x, DVD  6x)
  Buffer size in KB: 2048
  Copy management revision supported: 0

```

Any suggestions on what could be causing this problem and/or how I can fix it?

---

### Post by wpshooter on 2006-12-06
What CD burning program are you using ?

Suggestion, install and use **K3b** from Add/Remove programs.

---

### Post by disc on 2006-12-06
> **wpshooter said:**
> What CD burning program are you using ?

Suggestion, install and use **K3b** from Add/Remove programs.

I have K3b installed, and whenever I try to move .mp3 format to the window of files to be burned, it gives me the error of "Unsupported format: Unable to handle the following files due to an unsupported format." However, I have burned an .iso image using K3b, which successfully finished, however the CD did not work and it showed up as a blank CD when put in my Windows box.

---

### Post by wpshooter on 2006-12-06
I can not help you with the .mp3 problem since I am not into that type of thing.

However, I assume you are trying to burn a Ubuntu ISO image onto the CD.  Are you trying to boot to that CD ?  Have you made the CD-ROM drive the first boot device on that computer ?

---

### Post by PurplePenguin on 2006-12-06
I also don't convert MP3s to burn on audio discs (as it seems you're trying - if you wanted to just burn a data disc, it wouldn't matter what the filetype is), but a quick search in synaptic came up with this: libk3b2-mp3

It seems as if this is needed for k3b to decode mp3s.  Give it a shot, let me know if it helps! :)

Also, are you using default settings in k3b?  If you aren't sure, I think there's a button there to switch everything back to its default.  If, for example, you burn a disc with rockridge and no joliet, Windows won't recognize it.  If you burn a disc with k3b's defaults, I don't think there should be a problem.

You say that your discs don't come up under Windows... do they come up under linux?

What about GnomeBaker?  Have you tried burning things with it?

---

### Post by wpshooter on 2006-12-06
IMO, trying to use GnomeBaker would be a waste of his time.

P.S. - Disc:  When you install programs/software in Ubuntu try to always install thru either add/remove programs or Synaptic.  IMO, using any other method is somewhat risky.

---

### Post by PurplePenguin on 2006-12-06
> **wpshooter said:**
> IMO, trying to use GnomeBaker would be a waste of his time.

Why's that? :confused:  It's a good way to determine if he's got some kind of wrong setting in k3b (such as not supporting Joliet), wouldn't you think?  I suggested GnomeBaker since his profile says he's using Ubuntu 6.10, so it should be an easily accessible program.

---

### Post by wpshooter on 2006-12-06
> **PurplePenguin said:**
> Why's that? :confused:  It's a good way to determine if he's got some kind of wrong setting in k3b (such as not supporting Joliet), wouldn't you think?  I suggested GnomeBaker since his profile says he's using Ubuntu 6.10, so it should be an easily accessible program.

Yes, perhaps for test purposes, but the last time I tried that program it was not worth using, BUT that was a while back, it could possibly have been fixed by now but I sort of have my doubts.

---

### Post by PurplePenguin on 2006-12-06
"Test purposes" seem to be exactly why we're here right now. :D  The one major advantage that GnomeBaker has over k3b is the lack of a million settings.  If we can determine that he can successfully burn a disc that runs under linux, we can focus on the specific problem of getting his discs to run under Windows.

I've got a feeling that the problem with burning MP3s (that is, converting them from MP3 so they can be burned as an audio disc) is related to Ubuntu's lack of MP3 support out of the box.  Hopefully that libk3b2-mp3 that I mentioned earlier will help with that.  If not, we're probably into some more serious problems! :O

PS: Give GnomeBaker another shot! :)  I just switched to it from k3b and it works great!  I haven't tried the older versions that you were referring, to, though...

---

### Post by disc on 2006-12-07
I am on already on Ubuntu. I have installed K3b through Synaptic, etc. The problem is, every burning program I've used burns the CD's improperly. I've been able to "successfully" burn an .iso using both the CD/DVD Creator, and K3b. However, afterwards the CD appears as Blank on both this machine, and my Windows machine. So, it's not a problem with the installation of K3b, or my hardware because it detects CDs that I put in. My problem is that it is not burning the CDs properly.

---

### Post by disc on 2006-12-07
Okay, I've managed to burn a data CD with a test.txt on it using Gnomebaker. Both of my machines are picking it up. However, could anyone tell me an easy way to install the mp3 support for Gnomebaker? I've installed the all of the gstreamer0.8 plugins, but Gnomebaker is still giving me this error when I try to burn the .mp3's as an Audio CD.

```
The plugin to handle a file of type audio/mpeg is not installed.
```

---

### Post by PurplePenguin on 2006-12-07
Yesterday I did try burning some audio discs with a collection of MP3s (thanks for the inspiration!). :)  It works fine for me using GnomeBaker and the mp3 support that is on my system.  I used Automatix 2 to install my codecs (although I did go through one of the HowTos the first day I installed Ubuntu, so I might have added mp3 support that way), so I'm not sure how you'd go about it through Synaptic.  

Whatever Automatix did install, though, should show up as installed in Synaptic.  Here's a list of what I've got relating to mp3 decoding on my system:

gstreamer0.10-fluendo-mp3
libmad0

From what I understand from reading this forum, GnomeBaker for Dapper uses gstreamer0.8, whereas Edgy uses 0.10.

That said, [here's a post]("http://ubuntuforums.org/showthread.php?t=270371") by a guy who had to get rid of that fluendo plugin in order to get his mp3s to work! 

> I also had this problem. Rhythmbox and banshee played some mp3 files and not others.

My issue was that I installed two gstreamer plugins for playing mp3s:
gstreamer0.10-bad [universe]
gstreamer0.10-fluendo-mp3 [universe]

The solution was to uninstall either one of the two plugins.
I chose to removed gstreamer0.10-fluendo-mp3 and keep gstreamer0.10-bad.
After that, I was able to play mp3s that wouldn't play before.

I found the fix here:
[https://help.ubuntu.com/community/Re...515ba7630fcc59](https://help.ubuntu.com/community/Re...515ba7630fcc59)

-Ehtetur

A bit of fishing around ubuntuforums might help you figure it out... I checked into a few threads and it seems like you're not alone. :)

---

