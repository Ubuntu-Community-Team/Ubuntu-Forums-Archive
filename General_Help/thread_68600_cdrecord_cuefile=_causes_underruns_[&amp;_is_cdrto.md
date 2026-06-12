---
title: "cdrecord cuefile= causes underruns [&amp; is cdrtools@packages.debian.org a black hole?]"
date: 2005-09-23
forum: General Help
---

### Post by Blueshell on 2005-09-23
This probably isn't Ubuntu-specific (though it affects Hoary's version of cdrecord!), but I've (a) asked in linuxforums.org and heard nothing, and (b) sent mail to [email]cdrtools@packages.debian.org[/email] and had the mail wait hours for delivery ("out of space, try again later") and then heard nothing for a couple of days after it was delivered. (And despite considerable searching, I can't even tell if cdrtools has any sort of archive---I sure can't find it.) Further, cdrecord's maintainer claims not to be answering end-user bug reports any more, and Ubuntu uses a modified version anyway which explicitly claims it's unsupported upstream past Debian. So I'm asking here, in the hopes that someone (a) knows what the bug is here, and (b) how/where I should file a bug report such that it actually gets fixed. I'm including my entire bug report below; hopefully someone here has a clue about what to do with it.

Thanks!

Bug follows:

I've just discovered that cdrecord, in (I believe) two different
Debian-based distributions (a Sarge that's well over a year old, and
Ubuntu Hoary 5.04), cannot write full speed at 40x if and only if
cuefile= is in use. In other words, I can write 40x if I just supply
a random file (or a pipe), but if I use a cuefile to write the -same-
file, cdrecord can't write above about 20x and gets underruns (either
invoking BurnFree 164 or so times if enabled, or blowing out with SCSI
errors if not).

I can't find any discussion of this anywhere. I've done Google
searches and I've also exhaustively checked all the ChangeLogs I can
find, looking for "cue" or "cuefile". Is there a Bugzilla somewhere
I should have searched? (If so, it's a documentation bug that that
info is so hard to find, as well.)

I'm really surprised at this behavior; without looking at the code, I
would have expected that both cases opened the actual large file to be
written identically (presumably with just open()), and so I can't see
any obvious reason why the behavior would be so different.

(And a PS, which maybe would be more relevant if sent directly to the
Ubuntu folks somewhere---can the packager PLEASE get rid of the bogus
warnings JS insists on sticking in about using /dev (ATAPI -DOES NOT
WORK- in my Ubuntu based on 2.6 kernel, as far as I can tell---cdrecord
just blows out if I try to specify a device that way, even though this
very hardware worked via ATAPI under the 2.4 kernel I used to run w/Sarge),
-and- the bogus warning about using a 2.6 kernel at all? I wasted a
fair amount of time researching these warnings before eventually
deciding they should just be ignored.)

[If someone can tell me where to send either this bug report, or the
complaints in the paragraph above, so they get fixed at least in the
next Ubuntu report, that'd be great. Tnx.]

I've included below:

(a) Version info for my current cdrecord & distro (but, going back
through my saved output histories, this was screwing up in what I
believe to be the same way in a year-old version of Debian Sarge and
whatever cdrecord it shipped with, and---for the next few days---I
-could- boot that distro if it was important for fault isolation.)
(b) A working and nonworking case. (I have many other examples of
variations in the command line showing that it doesn't seem to
matter whether it's run via sudo or from a root shell, whether or
not it uses a pipe, whether or not fs= is used, etc---experiments
in this distro & Sarge were all run in Emacs shell buffers & I
saved them.)
(c) The cuefile I was using in the nonworking case.
(d) A message I wrote to linuxforums.org a couple of days ago, before
I fully understood the problem, which provides more background in
case it's important for debugging.

Okay, here goes:

(a) VERSIONS:

$ uname -a
Linux darkstar 2.6.10-5-k7 #1 Thu Sep 8 06:54:12 UTC 2005 i686 GNU/Linux
$ cdrecord --version
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
$

(b) WORKING AND NONWORKING CASES:

[--NOTE-- The last-write-at-16x stuff in the "working" case (writing
BG.bin directly) is probably because of the SCSI sense errors at the
very end. The progress indicator, disk activity, and wallclock time
clearly indicate that writing ramped up smoothly from ~20x at the
inside of the CD to ~41x at the outside, and certain of my tests
actually showed all 3 readouts at the end as being 40x. This is
unlike the "nonworking" case, where the write speed kept wildly
fluctuating from 10 to 40x, the progress indicator kept pausing for a
few seconds at a time, and the disk activity tended to "pulse" every
3-5 seconds instead of just flickering constantly.]

-- CUEFILE DOESN'T WORK --

$ time sudo cdrecord -dummy -v -dao -gracetime=5 -overburn driveropts=burnfree dev=/dev/cdrw cuefile=BG.cue
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type : Removable CD-ROM
Version : 0
Response Format: 1
Vendor_info : 'PLEXTOR '
Identifikation : 'DVDR PX-708A '
Revision : '1.10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x001B
Profile: 0x001A
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE VARIREC FORCESPEED SINGLESESSION HIDECDR
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1190112 = 1162 KB
Drive DMA Speed: 29323 kB/s 166x CD 21x DVD
FIFO size : 4194304 = 4096 KB
Track 01: data 1 MB
Track 02: data 707 MB
Total size: 708 MB (70:12.86) = 315965 sectors
Lout start: 709 MB (70:14/65) = 315965 sectors
cdrecord: Success. start/stop unit: scsi sendcmd: no error
CDB: 1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 02 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x02 Qual 0x00 (no seek complete) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 26.455s timeout 200s
Current Secsize: 2048
ATIP info from disk:
Indicated writing power: 5
Is not unrestricted
Is not erasable
Disk sub type: Medium Type B, low Beta category (B-) (4)
ATIP start of lead in: -11607 (97:27/1
ATIP start of lead out: 359849 (79:59/74)
Disk type: Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Single session is OFF.
Hide CDR is OFF.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43884
Forcespeed is OFF.
Power-Rec is ON.
Power-Rec write speed: 40x (recommended)
Starting to write CD/DVD at speed 40 in dummy SAO mode for single session.
Last chance to quit, starting dummy write 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01: 1 of 1 MB written (fifo 100%) [buf 96%] 18.8x.
Track 01: Total bytes read/written: 1058400/1058400 (450 sectors).
Starting new track at sector: 450
Track 02: 707 of 707 MB written (fifo 100%) [buf 56%] 12.5x.
Track 02: Total bytes read/written: 742091280/742091280 (315515 sectors).
Writing time: 249.529s
Average write speed 16.9x.
Min drive buffer fill was 0%
Total of 37 possible drive buffer underruns predicted.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time: 2.287s
Last selected write speed: 40x
Max media write speed: 40x
Last actual write speed: 40x
resid: 4
BURN-Free was 164 times used.
cdrecord: fifo had 11703 puts and 11703 gets.
cdrecord: fifo was 0 times empty and 3307 times full, min fill was 92%.

real 5m18.899s
user 0m0.120s
sys 0m7.978s

-- DIRECTLY FROM THE FILE DOES WORK --

$ time sudo cdrecord -dummy -v -dao -gracetime=5 -overburn driveropts=burnfree dev=/dev/cdrw BG.bin
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type : Removable CD-ROM
Version : 0
Response Format: 1
Vendor_info : 'PLEXTOR '
Identifikation : 'DVDR PX-708A '
Revision : '1.10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x001B
Profile: 0x001A
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE VARIREC FORCESPEED SINGLESESSION HIDECDR
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1190112 = 1162 KB
Drive DMA Speed: 13301 kB/s 75x CD 9x DVD
FIFO size : 4194304 = 4096 KB
Track 01: data 708 MB
Total size: 813 MB (80:38.22) = 362867 sectors
Lout start: 814 MB (80:40/17) = 362867 sectors
Current Secsize: 2048
ATIP info from disk:
Indicated writing power: 5
Is not unrestricted
Is not erasable
Disk sub type: Medium Type B, low Beta category (B-) (4)
ATIP start of lead in: -11607 (97:27/1
ATIP start of lead out: 359849 (79:59/74)
Disk type: Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Single session is OFF.
Hide CDR is OFF.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: -3018
cdrecord: WARNING: Data may not fit on current disk.
cdrecord: Notice: Overburning active. Trying to write more than the official disk capacity.
Forcespeed is OFF.
Power-Rec is ON.
Power-Rec write speed: 40x (recommended)
Starting to write CD/DVD at speed 40 in dummy SAO mode for single session.
Last chance to quit, starting dummy write 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01: 708 of 708 MB written (fifo 100%) [buf 97%] 40.1x.
WARNING: padding up to secsize.
Track 01: Total bytes read/written: 743149680/743151616 (362867 sectors).
Writing time: 174.106s
Average write speed 27.8x.
Min drive buffer fill was 97%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
cdrecord: Success. flush cache: scsi sendcmd: no error
CDB: 35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 05 A1 B1 0A 00 00 00 00 02 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x02 Qual 0x00 (no seek complete) Fru 0x0
Sense flags: Blk 369073 (valid)
cmd finished after 34.125s timeout 200s
Trouble flushing the cache
Fixating time: 34.126s
Last selected write speed: 16x
Max media write speed: 40x
Last actual write speed: 16x
resid: 4
BURN-Free was never needed.
cdrecord: fifo had 11706 puts and 11706 gets.
cdrecord: fifo was 0 times empty and 6704 times full, min fill was 92%.

real 3m34.553s
user 0m0.079s
sys 0m1.435s

(c) THE CUEFILE:

FILE "BG.bin" BINARY
TRACK 01 MODE2/2352
FLAGS DCP
INDEX 01 00:00:00
TRACK 02 MODE2/2352
FLAGS DCP
INDEX 00 00:04:00
INDEX 01 00:06:00

(d) MY EARLIER FORUM POST (W/NO REPLIES) W/SOME MORE BACKGROUND.

I've got a very puzzling problem with slow writes in cdrecord. It
seems that all the usual culprits have been eliminated; in particular,
I think I've eliminated -all- of (a) hardware and (b) distro!

I've got an Plextor 708A (IDE interface) as /dev/hdc on a K7N2 Delta-L
motherboard with an AMD 2800+ CPU, 1GB RAM, and a Seagate 300GB disk
on /dev/hda. These are the only two IDE devices, and there are no
other unusual devices (no USB, etc---just a couple of Xinerama's
screens, a keyboard, a mouse, and a 100baseT ethernet connection on an
idle home network).

This drive does NOT write above about 20x on a CDR under -either-
Ubuntu Hoary (2.6 kernel) -or- Debian Sarge (2.4 kernel) without
getting underruns (if I turn on the drive's BurnFree, it averages
about 16x), but it -does- write up to 40x if I boot under Windows 98!
And yes, I trust that both the DiscCopier app and Nero are reporting
speeds correctly---for one thing, Windows can write the same CD in
substantially less time than either of the Linux distros I've tried,
using the same CD's and the same hardware. (I don't know -exactly-
what versions of cdrecord, or indeed even exactly what Debian version
I was using, since I'm now using Ubuntu, but I still have snapshots of
all the old installations and could look up version numbers if
necessary. I'm certainly using a completely stock Ubuntu Hoary right
now.)

Yes, DMA is on. (Sarge turned it on by default, Ubuntu for some
reason didn't & I had to use "hdparm -d1 /dev/hdc" to do so.)

Under Debian (2.4 kernel), I was using ide-scsi to talk to
ATAPI:0,0,0; under Ubuntu, I'm -not- using ide-scsi (2.6 kernel) and
am using /dev/cdrw instead.

Even better, if I copy from /dev/zero instead of from some file in my
homedir (which is on /dev/hda, of course), then I -can- write up to
40x! And BurnFree is never used at all in this case. For example:

time sudo cdrecord -dummy -v -dao -gracetime=5 -overburn driveropts=burnfree dev=/dev/cdrw tsize=707m /dev/zero

works fine and reports all speeds as 40x (and runs in 3m17s wallclock
time). But if I drop the tsize & pick some 707meg file in ~/,
BurnFree gets used 164 times (repeatably) and the drive writes at
about 16x (and runs in 4m19s wallclock time; it's not as big a
difference as might be expected because of course no drive can write
40x until it gets pretty close to the outside of the CD). If I omit
BurnFree, it underruns and blows out a hundred meg in or so. In both
distros, the filesystem is ext3fs.

Okay, so now it looks like there's something wrong with the IDE
controller. But for it to have such poor performance would be a
noteworthy thing---no motherboard manufacturer or distro could get
away with it. And I've done disk-to-disk copies on this very
hardware, such as dd'ing one 200GB disk to another, in around an hour
or so---so I'm getting transfer rates across both IDE controllers of
2-3GB/min. This is -far, far faster- than any CDR wants data. This
is true in both distros, of course. And, of course, since I'm going
hda -> hdc, the data source & sink are on opposite IDE channels and
are both masters, so it ain't bus contention. (My disk-to-disks were
also typically master-to-master, but it hasn't made much of a
difference in speed either way.)

Could cdrecord be reading data extremely inefficiently from the
filesystem? Perhaps. (Surely ext3fs isn't the problem; again, people
would scream.) I -did- try screwing around with fs= to change the
FIFO size; going from the default 4m to 8m made the problem slightly
worse. Going to 2m wasn't any better than 4m. (And, of course, it
doesn't matter -which- big file I try in my filesystem.)

I'm now out of ideas. I haven't tried non-cdrecord-based CD-writers;
suggestions on what to try would be appreciated, but it'd be even more
appreciated if someone knows if this is a known cdrecord problem (also
hard to believe, but...). I can get very specific version numbers,
commands, command outputs, etc if anyone thinks they'd help (I did all
of my experients in an Emacs shell buffer, so it's all there), but
given that the behavior hasn't improved across different distros (and
presumably different cdrecord versions---these distros were installed
something like a year apart!), it's hard to believe that it's some
specific bad version.

If there's a more-appropriate place to ask this question (some
cdrecord-specific forum, or any other place), please let me know; I'm
basically guessing on asking here because this problem has manifested
on two different Debian-ish distros and thus doesn't even seem
specific to any one distro (unless it's anything derived from
Debian...).

-- THAT'S ALL, FOLKS! --

---

### Post by manis on 2005-09-27
hai,
I suggest you using k3b to burn all your video, data, copy cd and,,.
I use this application because a found error when I using cdrecord.
thank.
;)

---

### Post by Blueshell on 2005-09-27
Er, doesn't K3B internally call out to cdrecord to do its work?  If so, it might bypass the cuefile= issue by never happening to call it that way, but this -would- mean I'd have to rewrite any scripts that try to use cdrecord directly...

---

