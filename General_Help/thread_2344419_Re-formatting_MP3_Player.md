---
title: "Re-formatting MP3 Player"
date: 2016-11-25
forum: General Help
---

### Post by daniell59 on 2016-11-25
I have an old MP3 player that I made inoperative by formatting it in Linux. It will no longer allow me to re-format it in the hope of fixing the problem. Is there anyway that I can again format it properly?

---

### Post by ajgreeny on 2016-11-25
I am not sure what the image you have posted has to do with your query; it shows disk sda which I imagine is your computers internal disk and has nothing to do with an mp3 player.  Neither can I see why you think this is the reason for the player being inoperable now, other than the OS comment below.

What filesystem type did you format the mp3player to and what was it before you did that?  I suspect there would also have been a number of system files for the mp3player's own OS which have now been overwritten by your format, but without more information it is impossible to say.

Tell us a lot more detail of exactly what you did, the mp3player details; make, model, etc etc, and we may be able to suggest something to assist, though if you removed all its system files we will probably be unable to do anything really useful.
Unless, of course, you backed them up before starting on this operation.

---

### Post by Dennis N on 2016-11-25
Does the manufacturer have a web site? It may have documentation for their players (even the discontinued ones) online, maybe a support forum for your make and model of player. Even ancient posts years old may be helpful.

---

### Post by daniell59 on 2016-11-25
Sorry for my inadequate description of the problem.

Sandisk Model Sansa 250

I formatted using Disks Compatible with modern systems and hard disk >2TB
I chose to overwrite files

When I try to format again I get this message
Error synchronizing after initial wipe. Timed out waiting for object.
Perhaps I wiped the firmware. I would think the device is toast.

---

### Post by Bucky Ball on 2016-11-25
You generally drop the device's firmware into the appropriate folder on the device, unmount the device, unplug it then turn it on. It will reinstall the firmware and in the process wipe the lot and reset back to defaults. Hopefully it would work after that.

You would need to research to find the appropriate firmware for your device. You would be looking for how to 'upgrade firmware'. Even if you're installing the same version of firmware as you've already got it will achieve the same end; wipe device to defaults.

Not really a Linux issue, just happened to be caused by trying to format it in Linux (and I'm presuming you mean you tried to format the SD card or internal drive on it?). To reformat the device you would need to do that on the device. To reformat the SD card you would generally take that out and put it in the actual computer via an SD card slot and do it that way with Gparted or Disks or something else.

---

### Post by Dennis N on 2016-11-25
No, don't think you wiped the firmware. It is intended to be formatted. From their web site:

> "SanDisk tech support recommends formatting the m200 series in both MSC and MTP modes to completely clear out all work areas,"fragments" and residual data. The m200 has a very basic Operating System that doesn't have a defrag option. According to tech support, the m200 needs formmating occasionally to keep it working smoothly."

---

### Post by Bucky Ball on 2016-11-25
> **Dennis N said:**
> No, don't think you wiped the firmware. It is intended to be formatted. From their web site:

Point taken, but reinstalling firmware may be the quickest and easiest way out of this at this point. Also, could you include reference links when you quote another site, please? Thanks.

There are many ways to skin a cat and there are several ways of formatting this device (that I have found so far). Unfortunately, you have not included the 'official' procedure from the site you have quoted from. Right click the device in a file manager and 'format'?

---

### Post by daniell59 on 2016-11-25
. Right click the device in a file manager and 'format

I tried formatting it both in Linux and Windows. I wont allow me to do it in either. Since I just bought a much newer model, I wont spend anymore time on this. A lesson learned however. I wont be formatting it in Linux anymore.

---

### Post by Dennis N on 2016-11-25
Still had the page open in a tab. Google is omniscient:

[http://forums.sandisk.com/t5/All-other-MP3-players/Deleting-Songs-From-a-Sansa-M250/td-p/35271](http://forums.sandisk.com/t5/All-other-MP3-players/Deleting-Songs-From-a-Sansa-M250/td-p/35271)

Intended for Windows, however, so adapt.

---

