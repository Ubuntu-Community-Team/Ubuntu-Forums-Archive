---
title: "Random Sound Failure"
date: 2008-02-05
forum: General Help
---

### Post by barrack on 2008-02-05
I am running Feisty on a Compaq C500 Laptop. When I first installed ubuntu back in August 2007, I upgraded ALSA driver to the latest version to get the headphones working properly. I haven't had a problem since.

However, today, February 5, 2008, I boot up my computer and I have no sound! The volume control icon shows mute and clicking on it gets this message:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

After I close that and double-click on the volume icon, I get this message:

> No volume control GStreamer plugins and/or devices found.

As of last night, it was working and I had made no changes or downloaded any updates. The second message had me checking Synaptic to see about gstreamer plugins, but they were all there.

Any idea what may have caused this and what I might do to fix it?

Thanks in advance.

---

### Post by Crusty Juggler on 2008-02-06
I have the same problem.  Toshiba A200, sound worked fine yesterday, doesn't work at all today.

---

### Post by barrack on 2008-02-06
> **Crusty Juggler said:**
> I have the same problem.  Toshiba A200, sound worked fine yesterday, doesn't work at all today.

I'm glad I'm not alone. Strange that it was the same day.

---

### Post by barrack on 2008-02-06
I took some initiative on this and ended up fixing my sound! I hope that it works for you. 

I followed the instructions on this page to remove current the current alsa driver and load up the newest one. (The code shown is for an older version of alsa, so I just changed the numbers to reflect the new version. 1.0.16.)

[Here is the link if you'd like to read it. ]("http://ubuntuforums.org/showthread.php?t=455147")

The last detail that will save you is a small bit from [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Basically, you will enter this code:
```
sudo gedit /etc/modprobe.d/alsa-base
```

It should open up an empty file, to which you will create one line:

```
options snd-hda-intel model=laptop
```

Reboot and you're golden. Even my headphone jack works correctly!

---

### Post by barrack on 2008-02-13
*BUMP*

So I thought I had this fixed, but I guess not!

Something updated (in the background, I don't know what it was) and a system restarted was required. No big deal.

I restart, and I'm back to no sound.

Seriously, what's going on?

---

