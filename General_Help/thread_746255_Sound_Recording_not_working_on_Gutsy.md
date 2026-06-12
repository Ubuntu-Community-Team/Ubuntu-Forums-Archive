---
title: "Sound Recording not working on Gutsy"
date: 2008-04-05
forum: General Help
---

### Post by buried on 2008-04-05
I tried all configuration, won't work, I am a musician, I have a Ibanez Gio, I need to record with Jokosher, but I get this error in Prefences>Sound 
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat
```
Help needed.
btw I'm no newb in Ubuntu, using it since dapper.

---

### Post by bobkat60 on 2008-04-05
> **buried said:**
> I tried all configuration, won't work, I am a musician, I have a Ibanez Gio, I need to record with Jokosher, but I get this error in Prefences>Sound 
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat
```
Help needed.
btw I'm no newb in Ubuntu, using it since dapper.

I'm having probs with the sound since getting all the updates. but I think you may find to cure your problem open up System/preferences/ Sound and try changing in the panels which driver/card you are using.. I always get the same message on capture, I figure that is because I haven't got anything connected to receive sound from, if you are connecting a midi device or suchlike double try clicking on the speaker symbol(top right )and enable microphone or try adding the other settings... reboot and try again ... 
There seems to be some problem in the updates ,depending on hardware you have .I find disabling my NVidia graphic card restricted driver get things going until I reboot with them in again.
Good luck with it.
 Bobkat60

---

### Post by buried on 2008-04-05
I tried changing Drivers/Devices, same error occured.

---

### Post by buried on 2008-04-06
bump, need this I have to record, or I shall have to use Windows again!

---

### Post by BandD on 2008-04-06
There are many people who have trouble getting sound imput to work in Linux, mostly due to the fact that the sound card manufactures don't open up or offer their drivers to the linux community.

How are you hooking your guitar to your computer?

Also, can you post the output of the below run in a terminal:

```
lspci | grep Audio
```

The fix may depend on what sound card you have.

---

### Post by buried on 2008-04-06
I'm not connecting as input, just recording from the inbuilt microphone, works in windoze.
Output of Terminal
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

```
Thanks

---

### Post by buried on 2008-04-06
bump.

---

### Post by buried on 2008-04-06
bump again

---

### Post by buried on 2008-04-06
this is the last bump before in 27 hours Im switching back to windows.

---

### Post by BandD on 2008-04-06
I did a google search of your sound card and came across these links:

This link is a possible easier fix:
[http://ubuntuforums.org/showthread.php?t=506515]("http://ubuntuforums.org/showthread.php?t=506515")

This link will help you update to the newest version of ALSA configured with an ATI card, a more complex fix:

[http://ubuntuforums.org/showthread.php?t=624002]("http://ubuntuforums.org/showthread.php?t=624002")

Anyway, good luck!

---

### Post by buried on 2008-04-06
thanks for the help, now I'll try it and I won't need to switch to windows, thanks so much, I was thinking oh no, I like Ubuntu, do i have to? thanks anyways

---

### Post by buried on 2008-04-06
Nope none of that worked for me, still stuck with no recording :(

---

