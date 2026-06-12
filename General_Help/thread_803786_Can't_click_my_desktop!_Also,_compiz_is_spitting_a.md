---
title: "Can't click my desktop! Also, compiz is spitting an error at me..."
date: 2008-05-22
forum: General Help
---

### Post by themightymegatron on 2008-05-22
Okay, my main worry here is that for some reason I can't click my desktop. I 'm unable to add objects to it whatsoever, no context menu, nothing. The panel and app windows work fine. I tried 

> sudo apt-get remove gdm

Which removed

> gdm fast-user-switch-applet ubuntu-desktop

Then for the sake of it I rebooted, then ran

> sudo apt-get install gdm fast-user-switch-applet ubuntu-desktop

then restarted X-server. Still nothing.

Then, I tried running compiz.

> compiz --replace

and I get this output:
> primus@vectorsigma:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
**/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format**
**GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge.** Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I have no idea what to do about the /usr/bin/compiz.real error. I did, however, run 

> sudo rm -rf /apps/compiz/plugins/scale/allscreens/options/initiate_edge

And it resulted in me reinstalling compiz only to get these same two errors again. I'm at a loss here, hehehe. 

Any help is much appreciated!

---

### Post by Sam Lars on 2008-05-22
The desktop problem sounds more like a problem with Nautilus.  Try
```
killall nautilus
```
or
```
nautilus
```
Do you have anything in fstab or something like that that would cause Nautilus to stop responding?  I've had this thing happen when my NFS connections could not be mounted.
Try running
```
gconf-editor
```
and finding that value and changing it.  I've a similar thing happen before, too.

---

### Post by themightymegatron on 2008-05-22
> **Sam Lars said:**
> The desktop problem sounds more like a problem with Nautilus.  Try
```
killall nautilus
```
or
```
nautilus
```
Do you have anything in fstab or something like that that would cause Nautilus to stop responding?  I've had this thing happen when my NFS connections could not be mounted.
Try running
```
gconf-editor
```
and finding that value and changing it.  I've a similar thing happen before, too.

YAY! My desktop is back! Thank you so much! I can't believe it was that simple, heheh. one of my theme files was causing the error, so I switched to a clean-working one and it's all fine now!

Now I just need to fix the compiz issue. Still kinda lost on that though.

---

### Post by Forlong on 2008-05-22
> **themightymegatron said:**
> /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
This is not an error but a warning you can safely ignore.
> **themightymegatron said:**
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
That's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

---

### Post by themightymegatron on 2008-05-22
> **Forlong said:**
> This is not an error but a warning you can safely ignore.

That's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

thank you very much! Now it works fine. Next I get to have the fun time of backing up everything, wiping/reinstalling, and then restoring. Fun.

---

### Post by fsanchezcv on 2009-02-24
> **Sam Lars said:**
> The desktop problem sounds more like a problem with Nautilus.  Try
```
killall nautilus
```
or
```
nautilus
```
Do you have anything in fstab or something like that that would cause Nautilus to stop responding?  I've had this thing happen when my NFS connections could not be mounted.
Try running
```
gconf-editor
```
and finding that value and changing it.  I've a similar thing happen before, too.

Sorry to butt in, but how am I to tell what value is the one causing the trouble??

---

### Post by Sam Lars on 2009-03-03
He mentioned it in the original post as part of the error:
```
GConf backend: There is an unsupported value at path **/apps/compiz/plugins/scale/allscreens/options/initiate_edge**. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Forlong used a command to change it:
```
gconftool-2 -s -t string **/apps/compiz/plugins/scale/allscreens/options/initiate_edge** Disabled
```

---

