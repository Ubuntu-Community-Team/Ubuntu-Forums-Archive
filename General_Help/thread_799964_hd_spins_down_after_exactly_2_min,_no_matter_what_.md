---
title: "hd spins down after exactly 2 min, no matter what laptop-mode.conf says"
date: 2008-05-19
forum: General Help
---

### Post by mrowth on 2008-05-19
Hello forum,

I've got two PATA harddisks, hda and hdb. hda tends to be idle for hours at a time. I'd like to use laptop-mode to spin it down after half an hour. From /etc/laptop-mode/laptop-mode.conf:

```
LM_BATT_MAX_LOST_WORK_SECONDS=600
LM_AC_MAX_LOST_WORK_SECONDS=360

LM_READAHEAD=3072
NOLM_READAHEAD=128

LM_AC_HD_IDLE_TIMEOUT_SECONDS=1800
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
```

Yet hda does its customary little "click" and goes to standbyafter exactly 120 seconds - whether laptop-mode is started or stopped. 

**sudo laptop_mode status** then reports: 

```
Drive power status:

   /dev/hda:
    drive state is:  standby
```

It also reports the correct readahead times for whatever mode it's in... laptop-mode definitely "knows" whatever settings I've given it: 

```
me@computer:~$ sudo laptop_mode start

(...)
   Considering /dev/hda.
Setting spindown timeout on drives to 1800 seconds.
(hdparm configuration value = 241.)
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Executing: hdparm -S 241 /dev/hda

/dev/hda:
 setting standby to 241 (30 minutes)
(...)
```

```
me@computer:~$ sudo laptop_mode stop

(...)
   Considering /dev/hda.
Setting spindown timeout on drives to 7200 seconds.
(hdparm configuration value = 244.)
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Executing: hdparm -S 244 /dev/hda

/dev/hda:
 setting standby to 244 (2 hours)
(...)
```

It's just that that doesn't correspond to reality. 

Using a fully updated Gutsy... and I didn't have this problem before - also a Gutsy installation. (Okay, so it's Mint 4.0 KDE CE now.)

Anyone have any ideas what else could be interfering here? Because I don't. 

When I apt-get purge laptop-mode, the drive no longer goes to standby (well, maybe after hours or something, I won't wait for that now.) When I reinstall it, the "behaviour" is back (i.e. even with the default configuration).

---

### Post by mrowth on 2008-05-20
Hello? Still no idea what's up and it can't be easy on the harddisk.

---

### Post by sdennie on 2008-05-20
Do you have CONTROL_HD_POWERMGMT enabled in laptop mode?  Those clicks sound more like the hdparm -B values than the hdparm -S sounds (hard to know for sure without hearing it I suppose).

---

### Post by mrowth on 2008-05-20
The clicks are the same clicks it makes when turning comp on or off... what I don't hear is the whirring I'd for some reason expect from a HD spinning up (or down). But it's a very quiet drive.

No, CONTROL_HD_POWERMGMT=0. Uhm. Okay, when I set it to 1, the idle timeout values I've specified in laptop-mode.conf actually seem to matter! (Though who knows what's going to happen after a reboot...)

Buuut! Why were all the drives specified in laptop_mode.conf's HD="..." line previously sent to standby after two minutes? Where does that value, these two minutes, come from, and why didn't it happen until I took an active look at laptop-mode - and why did it happen then even when laptop-mode was disabled? (Is disabled = not active = not running = NOLM? Doesn't look like it)

I think I don't understand how laptop mode works.

For example, if ENABLE_LAPTOP_MODE_ON_AC=0, and I start laptop_mode manually (with verbose output): 

```
On AC power: Deactivating, because ENABLE_LAPTOP_MODE_ON_AC is not set.
Laptop mode enabled, active.
```

First it says "deactivating" - then it's "enabled, active"? So when I start laptop mode, it doesn't matter if the .conf doesn't ENABLE it? Is that just for laptop mode getting run on boot? 

And what's the difference between "active" and "enabled"? 

And is "no laptop mode" distinct from laptop-mode not running? Or... wait... "no laptop mode" *is* a mode *of* laptop mode? 

When laptop mode "isn't running", it's actually running with the NOLM values? 

Feep...

One thing I'm guessing is that when you set some value, it remains effective until actively overwritten (rather than just, say, ommitted in a revision of the .conf)?

---

### Post by sdennie on 2008-05-20
My guess is that your disk has a default power management value and so without specifically using hdparm to set, it just defaults to a 2 minute timeout.  By telling laptop-mode to issue the hdparm -B254 on AC power, it's completely disabling power management on the drive when the laptop is plugged in.

If you are never hearing the whine of a disk spinup and not seeing the several second delay that accompanies it, it's highly likely that your disk isn't actually spinning down.  There are two things at play here.  One is a just putting the disk in power savings mode (the clicking sound and the hdparm -B value) the other is completely spinning down the drive (so, later a spinup sound, pause and the hdparm -S value).

---

### Post by mrowth on 2008-05-20
> **vor said:**
> My guess is that your disk has a default power management value and so without specifically using hdparm to set, it just defaults to a 2 minute timeout.  By telling laptop-mode to issue the hdparm -B254 on AC power, it's completely disabling power management on the drive when the laptop is plugged in.

If you are never hearing the whine of a disk spinup and not seeing the several second delay that accompanies it, it's highly likely that your disk isn't actually spinning down.  There are two things at play here.  One is a just putting the disk in power savings mode (the clicking sound and the hdparm -B value) the other is completely spinning down the drive (so, later a spinup sound, pause and the hdparm -S value).

It wouldn't be so bad if two minutes weren't so short (there's a slight delay and it doesn't feel right to have every third disk operation accompanied by a metallic click)

Trying to understand...

Putting CONTROL_HD_POWERMGMT=0 again to experiment (180 seconds is just for testing).

```
   Considering /dev/hda.
[B]Setting spindown timeout on drives to 180 seconds.
(hdparm configuration value = 36.)[/B]
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
**Executing: hdparm -S 36 /dev/hda**

/dev/hda:
** setting standby to 36 (3 minutes)**
CONTROL_DPMS_STANDBY is disabled, skipping...
CONTROL_TERMINAL is disabled, skipping...
Intel IPW Wireless power setting is disabled.
Module /usr/local/lib/laptop-mode-tools/modules/* is not executable.
Module /etc/laptop-mode/modules/* is not executable.

```

Wasn't there an **hdparm -B** in that before?

The drive spins down after the desired time now, for whatever reason, and doesn't go into "click-but-no-whine" powersaving mode after two minutes.

I.e. it does the opposite of what it did before when I had CONTROL_HD_POWERMGMT=0.

With CONTROL_HD_POWERMGMT=1:

```
   Considering /dev/hda.
**Setting powermanagement on drives to 255.**
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
**Executing: hdparm -B 255 /dev/hda**

/dev/hda:
[B] setting Advanced Power Management level to disabled
Setting spindown timeout on drives to 180 seconds.
(hdparm configuration value = 36.)[/B]
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
Querying /dev/hda media type using udevinfo: type 'disk on bus 'ata' detected
**Executing: hdparm -S 36 /dev/hda**

/dev/hda:
** setting standby to 36 (3 minutes)**
CONTROL_DPMS_STANDBY is disabled, skipping...
CONTROL_TERMINAL is disabled, skipping...
Intel IPW Wireless power setting is disabled.
Module /usr/local/lib/laptop-mode-tools/modules/* is not executable.
Module /etc/laptop-mode/modules/* is not executable.
```

That seems to have the same result, except it also explicitly disables APM via **hdparm -B 255**...? 

Something's not the same anymore...

Maybe the settings got stuck somewhere and laptop-mode isn't canceling its own previous orders... or... something...

---

### Post by sdennie on 2008-05-20
I honestly don't know.  I understand what laptop-mode tries to do but, I don't use it because it seems like overkill and I'm never sure if I can trust it (admittedly, it's been several years since I've tried it so, my distrust may be unfounded).  I instead use a method described in this thread: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) (Same thread that is in my signature).  It basically accomplishes the same thing as laptop-mode but, you have more fine grained control over what is being executed.

---

### Post by mrowth on 2008-05-20
Hm, interesting.... that might help me understand what's actually being executed. 

Not sure I could make it to work - no SATA disk... no laptop for that matter. 

Oh, today (or was this always?) hdparm -B commands to my "main" drive (hdb) give this error, no matter the value: 
HDIO_DRIVE_CMD failed: Input/output error

syslog:
```
May 20 18:46:55 localhost kernel: [20936.264000] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
May 20 18:46:55 localhost kernel: [20936.264000] hdb: drive_cmd: error=0x04 { DriveStatusError }
May 20 18:46:55 localhost kernel: [20936.264000] ide: failed opcode was: 0xef
```

It does seem to respond correctly to hdparm -S, and spins down (and up, with the "whine") after the allotted time...

It's a new drive (couple weeks), perhaps it just doesn't have APM?

sudo hdparm -i /dev/hda: (this is the drive we've been working with all the time)
```
/dev/hda:

 Model=ExcelStor Technology J880, FwRev=PF2OA21B, SerialNo=PFD200K207N01A
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=51
 BuffType=DualPortCache, BuffSize=1719kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode
```

sudo hdparm -i /dev/hdb: (this is the "Ubuntu drive" - I don't normally want it to spin down)
```
/dev/hdb:

 Model=SAMSUNG HD400LD, FwRev=WQ100-15, SerialNo=S0AXJ1CPB00654
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 **AdvancedPM=no** WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```

I'm a bit bothered that it doesn't list udma6... guess that's what I get for always buying the not-quite-but-almost cheapest stuff I find...

Sorry if I'm asking too many questions.

Anyway, I put some hdparm scripts into /etc/acpi/start.d, /etc/acpi/resume.d, and /etc/acpi/ac.d. 

I can suspend and resume but the scripts don't seem to be executed... not on boot, either

---

### Post by mrowth on 2008-05-22
> **mrowth said:**
> Anyway, I put some hdparm scripts into /etc/acpi/start.d, /etc/acpi/resume.d, and /etc/acpi/ac.d. 

I can suspend and resume but the scripts don't seem to be executed... not on boot, either

Why is this? 

Where else can I put scripts to be run at boot time and again on resume from suspend-to-RAM and/or whenever else it's necessary to reapply such settings?

---

