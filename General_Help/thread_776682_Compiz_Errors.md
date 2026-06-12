---
title: "Compiz Errors"
date: 2008-04-30
forum: General Help
---

### Post by X Driver on 2008-04-30
Compiz Errors
I could use a little help with Compiz in the new Hardy Heron.

1) I lost the script for having Compiz start up automatically on boot. Does anyone have the Script?

2) When I run "Compiz" in terminal, I get these messages.

sam@sam-laptop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (204: Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I've reloded Compiz several times and differnt ways trying to fix various problems and it seem to store my old settings.

This all started when I was trying to get "My Video" to work in Skype (It turns to a blue screen when I start my video. It still sends images, I just can't see it on my end).

I really don't want to start over to fix it, as it did work right in the beginning, except for Skype. If I turn off all the stuff in Compiz, the camera works.

Any help would be appreciated.

Thanks,
Sam
Last edited by X Driver; 1 Hour Ago at 07:21 PM. Reason: Fixed a couple problems

---

### Post by ryanhaigh on 2008-05-01
You could try using synaptic, search for compiz and 'completely remove' it including all plugins, then reinstall it again. The completely remove option should remove all configuration information but you could check to ensure the files/folders the error mentions are actually removed before reinstalling.

---

### Post by maniacmusician on 2008-05-01
That probably won't do anything.

If you were trying to get skype video to work, you might have messed around in this file; /etc/X11/xorg.conf   , or some similar file, that caused the screw up. 

To help us best diagnose the problem, I would make post with exactly what you did while trying to get skype to work so we can figure out which change screwed up your direct rendering (which I'm gathering is the problem here).

---

### Post by X Driver on 2008-05-01
Here's where I'm at.

I got Compiz up and working again. I'm embarrassed to say what I did there, but let's just say I out thought myself.

I still have the Skype problem, see here.
[http://ubuntuforums.org/showthread.php?t=773099](http://ubuntuforums.org/showthread.php?t=773099)

If I turn Compiz off, Skype works, when I turn it on, I have the above problem.

I've got a different camera driver I'm going to try and load, I'll let you all know if it works.

Thanks,
Sam

---

