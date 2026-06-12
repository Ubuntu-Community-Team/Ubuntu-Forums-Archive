---
title: "Monitor goes blank and back on intermittently"
date: 2014-09-30
forum: General Help
---

### Post by Yahoé on 2014-09-30
For some reason, my screen goes blank and back on, sometimes more often, sometimes less, for about 1 to 2 seconds. When that happens my monitor is not going to sleep.
Ubuntu 14.10 fully updated, Radeon HD 4250. Any idea whats happening?

---

### Post by ventrical on 2014-10-01
> **Yahoé said:**
> For some reason, my screen goes blank and back on, sometimes more often, sometimes less, for about 1 to 2 seconds. When that happens my monitor is not going to sleep.
Ubuntu 14.10 fully updated, Radeon HD 4250. Any idea whats happening?


Have had the same problems here.

  I had the Radeon HD 5450 Silent. I put in a nVidia adapter card. Voila' No more blanking  or itermittent screen.

  Appears to be a Radeon Drivers problem but then it could be something else.

*edit*

It *is* something else because the same PC with new nVidia card gave me the 'blink' after I switched over to the terminal on KVM.

Regards..

---

### Post by jerrylamos on 2014-10-01
Did an install of "final beta" amd64.  Booted to flashing wallpaper.
Was able to boot in recovery mode screen res 800x600 ugly.  That uses some sort of software device driver.
this was with linux-image 3.16.0-17.  There was an entry in /var/crash about a compiz failure (as usual).
Did sudo apt-get update and sudo apt-get dist upgrade to 3.16.0-18.
Booted O.K.
Tried sudo ubuntu-bug /var/crash/*crash which said it could not report the bug since compiz had changed since the bug had occurred.
So compiz was updated between -17 and -18.  I don't think I could possibly count how many times compiz has been updated, for both better and worse.....

Oh, well, it's running now:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
Linux Aspire1 3.16.0-18-generic #25-Ubuntu SMP Fri Sep 26 02:44:15 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

Note this is a netbook with 1024x600 screen plugged into an external display TV at 1360x768.  Runs ubuntu O.K. except firefox flash jerky on BBC videos. I also do Lubuntu utopic which is noticeably better.

BTW, my Lenovo M58p desktop intel core 2 duo 3 gHz would not get past flashing screen from utopic 3.16.0-7 to 3.16.0-14.  Been running O.K. since.

---

### Post by ventrical on 2014-10-01
I had been having a few hicups here and there but no show stoppers to bring to the table.

---

### Post by Yahoé on 2014-11-10
Bump.

I wish someone could help me with this to try to fix it. Buying a new video card is not a valid solution... The monitor sometimes blinks several times by minutes. Quite a problem!

---

### Post by bapoumba on 2014-11-10
*Thread moved to **General Help**.*
Was still in the Development forum :)

---

### Post by Doug S on 2014-11-11
In my case, and on my test server (currently running 14.04, but only sometimes with the correct kernel), the monitor screen going blank and flashing on for a second or two started when I switched monitors, to an older one. The grub menu always displays fine, but thereafter the blank with flashing thing occurs. In my case it is fixed by powering down the monitor, waiting a few seconds, then powering it up again. I never turn the test server off, but re-boot it often, and have to do this every time.

I took this same older monitor from my main, but still 12.04, server. The issue never occurred on that computer.

---

### Post by Yulra on 2014-11-12
In my case... it appears to be MESA on certain AMD cards usually the newer stuff, but try the proprietary FGLRX driver.

---

### Post by decrepit on 2014-11-12
Are you sure it's not the monitor? I had a similar sounding problem on bootup. I had to power the monitor down and up several times before it stayed on permanently.
Fixed it by replacing most of the electrolytics.

---

### Post by Yulra on 2014-11-12
A faulty monitor is one item that can go wrong but this one isn't on boot. The symtoms sound awfully close to mine. 

1. Boot System
2. Do random stuff
3. Wait for random amount of minutes
4. Screen goes black. 
5. Screen switches off
6. Screen switches on.
7. System resumes as normal
OR
8. System freezes. Only mouse moves and nothing for Alt-SysRq+SUB works....

---

### Post by Yahoé on 2014-11-17
The monitor is not at fault, the symptoms are identical with a different one. My system never freezes though, I only experience a blinking monitor.
I do not experience this issue with an older kernel. I'm now using kernel 3.13.11 and there never is any blinking. Maybe a bug report should be filled.

---

### Post by Yahoé on 2014-12-17
The newest kernel I can use without experiencing the problem is 3.14.25-031425. Anything after that and the blinking comes back, just by booting with a newer kernel.

---

### Post by Yahoé on 2015-02-10
Alex Deucher from AMD told me wrote to me yesterday that a fix was committed upstream into the 3.18-stable tree, titled drm/radeon: fix PLLs on RS880 and older v2.

This is a workaround for RS880 and older chips which seem to have an additional limit on the minimum PLL input frequency.

[https://bugzilla.kernel.org/show_bug.cgi?id=91861](https://bugzilla.kernel.org/show_bug.cgi?id=91861)
[https://bugzilla.kernel.org/show_bug.cgi?id=83461](https://bugzilla.kernel.org/show_bug.cgi?id=83461)


To be tested.

---

### Post by Yahoé on 2015-02-13
This annoying problem is finally dealt with in 3.19.0-031900-generic from ~kernel-ppa/mainline

---

### Post by bapoumba on 2015-02-13
Glad to see this has finally been worked out :)

---

### Post by rsidd120 on 2015-06-24
> **Yahoé said:**
> This annoying problem is finally dealt with in 3.19.0-031900-generic from ~kernel-ppa/mainline

Unfortunately for me (Radeon HD 8490) the problem persists in Ubuntu Vivid, kernel 3.19.0, with both the fglrx and radeon open source drivers.  Certain webpages, opened in either Firefox or Google Chrome (maximised window), trigger it reliably, for example [this one]("http://genome.ucsc.edu/cgi-bin/hgTracks?tsCurTab=advancedTab&tsGroup=Any&tsType=Any&hgt_mdbVar1=dccAccession&hgt_tSearch=search&hgt_tsDelRow=&hgt_tsAddRow=&hgt_tsPage=&tsSimple=&tsName=&tsDescr=&db=hg19&hgt_mdbVal1=wgEncodeEH000210").  The screen goes blank when I open it; if I close it with ctrl-W the screen returns after a moment or two.   At other times it happens randomly and I can't really tell why.  I found that using redshift to reduce the screen brightness/temperature solves the problem, though.  At least as of now.

---

