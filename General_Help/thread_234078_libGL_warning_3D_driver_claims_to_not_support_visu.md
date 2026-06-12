---
title: "libGL warning: 3D driver claims to not support visual"
date: 2006-08-10
forum: General Help
---

### Post by featherking on 2006-08-10
When i run certain programs i get this error:

```
chris@Chris-Laptop:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32

```

I am using an Intel 945G, i believe, and im using the i810 driver with DRI enabled. When testing DRI using glxgears i get this error followed by a message telling me that DRI is enabled. Also, using glxgears my frames are like 700-800 FPS, i think that may be a little low considering some FPS ive seen people post. Does anyone know anything about this error, or how to fix?

---

### Post by miseryshining on 2006-08-18
there is a discussion about it here: 
[http://fcp.homelinux.org/modules/newbb/viewtopic.php?topic_id=24572&forum=11](http://fcp.homelinux.org/modules/newbb/viewtopic.php?topic_id=24572&forum=11)

it's fixed in the lates cvs releases. I didn't compile them yet, because it might cause x to get unstable. 

Btw, I have the same intel chipset and get around 1000 points in glxgears with a core duo 2300 CPU.

---

### Post by hikaricore on 2006-10-27
getting the same error with a Matrox G400 and the mga driver :/

might try doing a mesa cvs build to see if this resolves the issue

---

### Post by Architeuthis on 2006-10-27
I am having a very similar issue: see my thread about it [http://www.ubuntuforums.org/showthread.php?t=284088](http://www.ubuntuforums.org/showthread.php?t=284088)

when i execute glxgears i get this error message:
> libGL warning: 3D driver claims to not support visual 0x4b
drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)


Is it the same error? When will the updated version of mesa be updated in ubuntu (edgy)?

---

### Post by hikaricore on 2006-10-27
> **Architeuthis said:**
> 
Is it the same error? When will the updated version of mesa be updated in ubuntu (edgy)?

Yea alot of people are having this same issue across many linux distros.  It's currently fixed in the Mesa CVS and hopefully there will be an update for edgy soon.  Edgy was just relased the other day so give em a bit to get the issue resolved in the form of an update.  :)

---

### Post by Architeuthis on 2006-10-27
> Yea alot of people are having this same issue across many linux distros. It's currently fixed in the Mesa CVS and hopefully there will be an update for edgy soon. Edgy was just relased the other day so give em a bit to get the issue resolved in the form of an update. 

I'm very happy to hear that, finally i will be able to run 3dapps again.

---

### Post by hikaricore on 2006-10-28
Yea i'm holding off upgrading to edgy on my main system due to the number of problems i've seen and the experience I had on one of the two machines I upgraded on.  I already have enough trouble with direct rendering working randomly on my i810 setup, I fear if I install edgy my video hardware will team up with the graphical bugs in mesa and murder me in my sleep.  Mesa is sneaky like that.

---

### Post by graigsmith on 2006-10-28
im getting this with the open source ati 9200 drivers.

and the sound is popping when i play wow.

and sometimes nautilus crashes with 100% cpu usage.

and if you hit ctrl alt backspace, you can never log back in until you reset the thing.

:(  this thing is pretty buggy.  im tempted to go back to the last version.

---

### Post by calvmari on 2006-12-08
Has there been an update on this? I'm still getting this error on Edgy with everything updated (always have gotten this error since I upgraded from dapper Dec 3)

---

### Post by trippinnik on 2006-12-15
libGL warning: 3D driver claims to not support visual 0x4b

Any updates or reason for this error?  Is it even harmful?  I've been able to get direct rendering to work but not Beryl (not really a priority and not surprising) but this error turns up in the console whenever I run something with 3D accell.   I've got a Mobility 9000 aka Radeon Mobility M6 LY.  Are there even flgrfx drivers for older cards somewhere?  I know this one is not supported anymore.

---

### Post by xopher on 2006-12-15
> **hikaricore said:**
> getting the same error with a Matrox G400 and the mga driver :/

might try doing a mesa cvs build to see if this resolves the issue

For the mga [MATROX] driver issue, check this out: [http://ubuntuforums.org/showthread.php?t=319102](http://ubuntuforums.org/showthread.php?t=319102)

---

### Post by mrv on 2006-12-16
For both of the ATI problems, see my reply in [other post](http://ubuntuforums.org/showpost.php?p=1893660&postcount=5). Ie, Radeon 8500-9200 fixed in kernel 2.6.19, Radeon 9500 - X850 fixed in MESA/DRM development tree (currently).

Don't know how large portions of people these are affecting. I had (before the fix) problems with my X800, but all the other people I know who have X800 have had working radeon driver (not fglrx) without any problems.

---

### Post by w0rds on 2006-12-22
did anyone try to fix the visual blablabla? a howto would be pretty welcome

(i'm on a thinkpad t20 - savage ix videocard and getting the same error, btw)

---

### Post by mrv on 2006-12-27
Like mentioned, the visual blabla warning should not cause any problems, and if you have some problems it's not because of that (or should not). See Fd.o bug [6689](https://bugs.freedesktop.org/show_bug.cgi?id=6689).

Anyway, I'm writing this to confirm that the drmRadeonCmdBuffer error is now also fixed in kernel 2.6.20-rc2, ie. also for Radeon 9500 - X850 series.

---

### Post by w0rds on 2007-01-02
in my videocard, gl doesn't work... and that's the only error shown. it's not an ati card. :|

---

### Post by daradib on 2007-03-25
> Don't know how large portions of people these are affecting. I had (before the fix) problems with my X800, but all the other people I know who have X800 have had working radeon driver (not fglrx) without any problems.

I have Radeon X800 and have the libGL warning: 3D driver claims to not support visual 0x4b. I'm using Radeon (not fglrx) drivers on Kubuntu Feisty Herd 5 32-bit with AIGLX (I updated, upgraded, and dist-upgraded via apt-get, so I may be at same version as Kubuntu Feisty Beta 32-bit). I have looked hard, but I can't find a fix.

I heard that this warning has no impact on rendering, but 3D desktop effects (like Beryl) look horrible. It seems like the framerate is low, since when using wobbly windows to move windows around lines appear on the windows (or when rotating the desktop cube), but the windows and desktop do not appear to be affected by a reduction in speed. I had this same problem (though not necessarily the libGL warning) with the fglrx drivers on XGL.

---

### Post by rcmullins on 2007-04-10
I get the same warning.  Trying to run the Beryl Manager;

LibGL Warning:  3D driver claims to not support visual 0x4b reloading options

and it just hangs there.  Any suggestions?  Maybe a new graphics card?

---

### Post by rcmullins on 2007-04-10
Well, it runs beryl, but as listed in the above post, it runs crappily.  Better than upgrading to Vista though!

---

### Post by gottferdamnt on 2007-08-02
Same issue here with a Intel GMA 950. Neverwinter nights is very slow. I get this error:
> user@pc:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x5b


---

