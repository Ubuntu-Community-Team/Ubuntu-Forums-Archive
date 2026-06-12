---
title: "GnomeBaker says &quot;Wrong medium type&quot;?"
date: 2007-08-27
forum: General Help
---

### Post by Rundi on 2007-08-27
Hello all -

Seems I'm not the only one having trouble with GnomeBaker. Here is mine:

I have an old 500 mhz 512 MB RAM computer and I am trying to burn a DVD+RW (Memorex brand). Some time ago (before I installed Ubuntu on this box, I think) I did burn a data DVD with a old Mandrake 9.1 distro on this computer. However, I seem to be having no success at present. Unbuntu appears to be recognizing the DVD+RW when I insert it--The DVD comes up as empty in GnomeBaker and I can add material to the project. But, when I attempt to write the DVD I get the following error:

> 
Executing 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p Erend -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker/rundy/gnomebaker-VfH6uK | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
/dev/hdc: pre-formatting blank DVD+RW...
/dev/hdc: "Current Write Speed" is 2.5x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=06h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type


"Wrong medium type" isn't particularly helpful, as the recognition of DVD+RW is correct. I think the error message isn't telling me what the real problem is, or else I'm not understanding what it is saying.

Any help would be much appreciated.

Thanks.

---

### Post by jamvegan on 2007-08-27
Apologies if this is a silly question, but does your drive support both DVD+RW and DVD-RW, and if not, are you sure you've got the right one?

Another possibility is that there is an incompatibility with Memorex discs.  I just Googled your error and, while very few matches came up, two of them specifically mentioned that they got the error with Memorex discs.

---

### Post by Rundi on 2007-08-27
Interesting question. Initially I had no answer initially as I hacked this computer together from cannabalized parts from various machines and thus the documentation to the DVD drive is long gone. There is no brand name on the front of the drive, so the only clue I had to go on was a link on the front of the drive to [www.drvupdate.com](www.drvupdate.com). I went to the address and found a list of drives . . . all of which support DVD+RW, so I don't think it can be a straight down incompatibility with DVD+RW.

My drive is 16x, so I'm making an educated guess that it is either DVDRW 1016, DVDRW 1116, or DVDRW 2016 on the list provided at drvupdate.com

A quick Google search did not find any information for me on a incompatibility between Memorex and these drives . . . which doesn't mean there necessarily isn't a problem there.

If anyone else knows of anything more, or can give any further pointers, I'd be interested.

---

### Post by Rundi on 2007-08-27
Some further info . . .

On  the off chance there was just something wrong with the first DVD+RW I tried, I decided to try a fresh one. When I attempted to format with GnomeBaker I got this error message:

> * BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
|/-\|/-\|/-* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.


I don't know if that information is valid, or how to attempt a format with "-lead-out" or if that is even advisable. Maybe this will give someone else a lead.

---

### Post by GreenMeanie on 2007-10-18
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p greenmeanie -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-greenmeanie/gnomebaker-VGE6ZT | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using JOHNNY_CASH___CHRISTMAS_000.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 07 - Oh Come All Ye Faithful.mp3 (Johnny Cash - Christmas With Johnny Cash - 11 - Silent Night.mp3)
Using JOHNNY_CASH___CHRISTMAS_001.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 11 - Silent Night.mp3 (Johnny Cash - Christmas With Johnny Cash - 05 - Blue Christmas.mp3)
Using JOHNNY_CASH___CHRISTMAS_002.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 05 - Blue Christmas.mp3 (Johnny Cash - Christmas With Johnny Cash - 02 - The Christmas Guest.mp3)
Using JOHNNY_CASH___CHRISTMAS_003.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 02 - The Christmas Guest.mp3 (Johnny Cash - Christmas With Johnny Cash - 04 - The Gifts They Gave.mp3)
Using JOHNNY_CASH___CHRISTMAS_004.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 04 - The Gifts They Gave.mp3 (Johnny Cash - Christmas With Johnny Cash - 06 - Merry Christmas Mary.mp3)
Using JOHNNY_CASH___CHRISTMAS_005.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 06 - Merry Christmas Mary.mp3 (Johnny Cash - Christmas With Johnny Cash - 03 - Hark, The Herald Angels Sing.mp3)
Using JOHNNY_CASH___CHRISTMAS_006.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 03 - Hark, The Herald Angels Sing.mp3 (Johnny Cash - Christmas With Johnny Cash - 12 - Christmas As I Knew It - (Bonus Track, Previously Unreleased).mp3)
Using JOHNNY_CASH___CHRISTMAS_007.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 12 - Christmas As I Knew It - (Bonus Track, Previously Unreleased).mp3 (Johnny Cash - Christmas With Johnny Cash - 09 - The Christmas Spirit.mp3)
Using JOHNNY_CASH___CHRISTMAS_008.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 09 - The Christmas Spirit.mp3 (Johnny Cash - Christmas With Johnny Cash - 01 - I Heard The Bells On Christmas Day.mp3)
Using JOHNNY_CASH___CHRISTMAS_009.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 01 - I Heard The Bells On Christmas Day.mp3 (Johnny Cash - Christmas With Johnny Cash - 10 - Joy To The World.mp3)
Using JOHNNY_CASH___CHRISTMAS_00A.MP3;1 for  music/Johnny_Cash-Christmas_With_Johnny_Cash-2003/Johnny Cash - Christmas With Johnny Cash - 10 - Joy To The World.mp3 (Johnny Cash - Christmas With Johnny Cash - 08 - Away In A Manger.mp3)
Using HEART___A_LOVEMONGERS__C000.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 05 - William And Rose.mp3 (Heart - A Lovemongers' Christmas - 03 - Mary.mp3)
Using ALBUMART__4C2ADEEA_A2F8_000.JPG;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/AlbumArt_{4C2ADEEA-A2F8-48FF-841F-2FAF9814B30B}_Small.jpg (AlbumArt_{4C2ADEEA-A2F8-48FF-841F-2FAF9814B30B}_Large.jpg)
Using HEART___A_LOVEMONGERS__C001.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 03 - Mary.mp3 (Heart - A Lovemongers' Christmas - 10 - It's Christmas Time.mp3)
Using HEART___A_LOVEMONGERS__C002.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 10 - It's Christmas Time.mp3 (Heart - A Lovemongers' Christmas - 01 - Here Is Christmas.mp3)
Using HEART___A_LOVEMONGERS__C003.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 01 - Here Is Christmas.mp3 (Heart - A Lovemongers' Christmas - 07 - Balulalow.mp3)
Using HEART___A_LOVEMONGERS__C004.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 07 - Balulalow.mp3 (Heart - A Lovemongers' Christmas - 11 - Oh Holy Night.mp3)
Using HEART___A_LOVEMONGERS__C005.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 11 - Oh Holy Night.mp3 (Heart - A Lovemongers' Christmas - 08 - Ave Maria.mp3)
Using HEART___A_LOVEMONGERS__C006.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 08 - Ave Maria.mp3 (Heart - A Lovemongers' Christmas - 06 - Let's Stay In.mp3)
Using HEART___A_LOVEMONGERS__C007.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 06 - Let's Stay In.mp3 (Heart - A Lovemongers' Christmas - 04 - How Beautiful.mp3)
Using HEART___A_LOVEMONGERS__C008.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 04 - How Beautiful.mp3 (Heart - A Lovemongers' Christmas - 02 - Christmas Waits.mp3)
Using HEART___A_LOVEMONGERS__C009.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 02 - Christmas Waits.mp3 (Heart - A Lovemongers' Christmas - 12 - Bring A Torch.mp3)
Using HEART___A_LOVEMONGERS__C00A.MP3;1 for  music/Julmusik-Heart-A Lovemonger's Christmas/Heart - A Lovemongers' Christmas - 12 - Bring A Torch.mp3 (Heart - A Lovemongers' Christmas - 09 - The Last Noel.mp3)
:-[ PERFORM OPC failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

same problem here.

---

