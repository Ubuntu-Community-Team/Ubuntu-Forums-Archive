---
title: "harddisk health"
date: 2007-06-25
forum: General Help
---

### Post by atlfalcons866 on 2007-06-25
hi
i am starting to get concerned about my hdd. It makes a loud sound when it spins down. This didnt happen in windows. My harddirve is 46 degrees celcuis which is around 114Degrees feriheit. Is it normal for a harddisk to get this hot in my case?

---

### Post by lingnoi on 2007-06-25
Its normal for the country I am in which the normal outside temp is 28 C

---

### Post by jrusso2 on 2007-06-25
I would not worry until I get over 120 F.  Of course Hard drive failure is not a question of how but when.  So always be ready.

---

### Post by logos34 on 2007-06-26
46 C isn't too bad (mine get up to 42).  You should be ok up to around 60 C for a 7200 rpm (at least that's my impression reading manufacturer specs).  Might want to consider a small fan just for the drive.  If the drive supports S.M.A.R.T.:

**sudo apt-get install smartmontools**

Then run (hda=your drive)

[B]sudo smartctl -i /dev/hda 
sudo smartctl -a /dev/hda
sudo hdparm -v -i /dev/hda[/B]

---

### Post by frecon on 2007-11-27
> sudo smartctl -i /dev/hda 

That didn't work. "No such file or directory"

I found after googling that I can write sudo smartctl -i /dev/sda instead. That gave me 
> smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: ATA      FUJITSU MHV2100A Version: 0000
Serial number:         NT23T5B28K1Y
Device type: disk
Local Time is: Tue Nov 27 14:53:36 2007 CET
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging

Does that mean that I can't check the health of my hard drive? Can I check if it's damaged with something else?

Thanks in advance!

---

