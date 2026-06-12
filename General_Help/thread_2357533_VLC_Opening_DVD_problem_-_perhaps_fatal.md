---
title: "VLC Opening DVD problem - perhaps fatal?"
date: 2017-04-03
forum: General Help
---

### Post by Bobby_James on 2017-04-03
I purchased a region 1 DVD. I am in the UK (region 2). I used "regionset" to set the region to 1. I am using 16.04.

However, when I use VLC to "open disc" I get:

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

Some of the more dubious log entries are:
[COLOR=#00008b][I]
dvdnav[/I][/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/sr0)
[COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/sr0
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access 'dvd' location='/dev/sr0', path='/dev/sr0'
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 25 candidates
[COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*core*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]open of `dvd:///dev/sr0' failed
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 1/2)
 [COLOR=#00008b]*core*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play

The "Files" program shows the name of the DVD on the left hand side. The DVD does spin / make noises, etc. 

Any ideas? Many thanks.

---

### Post by mc4man on 2017-04-05
Other than the few licensed software dvd players dvd  regions are not enforced at the player level. So there would be no issue playing dvd's from   regions other than what drive is set to. 
(- one reasonably common laptop dvd drive manufacturer does enforce regions in the drive itself, Matshita, with those drives you can only play from the region the drive is set to.
Considering you only get 5 sets of the region on the dvd drive before it's locked at last setting you should not switch just to play 1 dvd..

As far as current - 
first try removing ~/.dvdcss folder (hidden folder), then try vlc again
If still no good then with the dvd in the drive run this, ck. what is reported in the *-cdrom section, post if desired.
```
sudo lshw -c disk
```

---

### Post by Bobby_James on 2017-04-09
Thank you for your help!

I deleted the .dvdcss folder and this time the DVD opened in VLC. However, it only showed an introductory animation screen for a few seconds (a .VOB file) then went black. There was no menu.

The VLC error showed: 

 [COLOR=#ff0000]Your input can't be opened:[/COLOR]

 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/xxx/NATIONAL_GEOGRAPHIC/VIDEO_TS/'. Check the log for details.


Here are the results of lshw:

```
  *-cdrom
       description: DVD-RAM writer
       product: DVDRW SSM-8515S
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/xxx/NATIONAL_GEOGRAPHIC
       version: GRS6
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/xxx/NATIONAL_GEOGRAPHIC
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted
```

I also ran cdck -i and got:

```
Track list (1-1):
  1: 00:02:00 (sec: 000000) data 
170: 255:59:74 (sec: 1151849) data (leadout)

Disc status: data mode 1
Multisession: 0
Audio status: failed to get, reason: Input/output error

Try to find out what sort of CD this is...
CD-ROM with iso9660 fs
iso9660: 4428 MB size, label 'NATIONAL_GEOGRAPHIC
``` 
[/COLOR]

---

### Post by Bobby_James on 2017-04-13
Bump!

---

### Post by efflandt on 2017-04-14
Have you followed this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I don't think vlc pays attention to regions because I used vlc in WinXP at work some time ago to play a Region 2 DVD (US is Region 1), but I don't think I had ever played a region disc in that computer before because when I later inserted a DVD and Windows Media Player came up, it said that no region was set on the DVD drive, asking if I wanted to set it to Region 1.

---

### Post by mc4man on 2017-04-14
Maybe try to see if this is vlc specific by trying dvd in totem.
Otherwise for starters open vlc > Tools > Preferences & under the Input/Codecs > 1st option (Hardware-accelerated.. ),  set it to disabled, save setting & try vlc again. If that helps & you do want hwdec then post specs on display adapter, this command should suffice for info, inxi package needs to be installed.
```
inxi -G
```

---

### Post by Bobby_James on 2017-04-14
Totem says "The DVD device you specified seems to be invalid."

I tried VLC with the modifications but I still can only get a very brief intro and the FBI warning. I can't see any menus. 

The DVD does contain in VIDEO_TS a 4.2 GB .BUP file but I've no idea how to access said file via VLC or Totem.

Any ideas? Thanks again. Perhaps there is a problem with the DVD itself? VLC says "  [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/sr0'. Check the log for details."[/COLOR]

---

### Post by mc4man on 2017-04-14
> **Bobby_James said:**
> Totem says "The DVD device you specified seems to be invalid."

I tried VLC with the modifications but I still can only get a very brief intro and the FBI warning. I can't see any menus. 

The DVD does contain in VIDEO_TS a 4.2 GB .BUP file but I've no idea how to access said file via VLC or Totem.

Any ideas? Thanks again. Perhaps there is a problem with the DVD itself? VLC says "  [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/sr0'. Check the log for details."[/COLOR]

Probably would be good to try a different dvd if possible. 
As far as a 4.2 GB .BUP file, that is not normal. A .BUP (backup file) is a backup of a .IFO file. For dvd's to play correctly the .IFO's must be readable, the corresponding .BUP(s) is 'positioned'  a slight distance away on the  disk  so a minor scratch can't impact both. The pair are the same size, typically  less than 200 kB

---

### Post by Bobby_James on 2017-04-15
I have tried a different DVD and it worked fine. Is there a way to test if the DVD is the problem?

Here is the file structure for VIDEO_TS. As you can see, there is a large BUP file.

```
-r--r--r-- 1 xxx xxx       8192 Feb  9  2015 VIDEO_TS.BUP
-r--r--r-- 1 xxx xxx       8192 Feb  9  2015 VIDEO_TS.IFO
-r--r--r-- 1 xxx xxx      12288 Feb  9  2015 VTS_01_0.BUP
-r--r--r-- 1 xxx xxx      12288 Feb  9  2015 VTS_01_0.IFO
-r--r--r-- 1 xxx xxx    7817216 Feb  9  2015 VTS_01_1.VOB
-r--r--r-- 1 xxx xxx 4200000000 Feb  9  2015 VTS_02_0.BUP
-r--r--r-- 1 xxx xxx      79872 Feb  9  2015 VTS_02_0.IFO
-r--r--r-- 1 xxx xxx      10240 Feb  9  2015 VTS_02_1.VOB
-r--r--r-- 1 xxx xxx      10240 Feb  9  2015 VTS_02_2.VOB
```

VTS_01_1.VOB loads a brief animation for a few seconds but there is no menu once the animation ends.

---

### Post by mc4man on 2017-04-15
> **Bobby_James said:**
> I have tried a different DVD and it worked fine. Is there a way to test if the DVD is the problem?

Here is the file structure for VIDEO_TS. As you can see, there is a large BUP file.


VTS_01_1.VOB loads a brief animation for a few seconds but there is no menu once the animation ends.

Clearly the dvd is the problem. It's either a damaged original disk or a very bad rip & burn or a rip & burn on media that's severely degraded.
The only other possibility for an orig. disk  is it's some structure protection I've never seen, unlikely.. 
To test that put it in a hardware dvd or blu-ray player hooked up to a tv  & see..

---

