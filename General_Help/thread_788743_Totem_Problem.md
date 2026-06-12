---
title: "Totem Problem"
date: 2008-05-10
forum: General Help
---

### Post by dyniesty on 2008-05-10
[B]Hi Guys!

  I just have a problem today,its the video player.

Heres what happened,
 
  I opened a WMV file and tried to play it but then it says,

  " Failed to connect steam: Invalid argument "

 Then I tried another a AVI file and it says

  " Failed to connect steam: Invalid argument " again .

 So can somebody help me? If you know what is the problem
                  please tell me :([/B]

---

### Post by Bubba64 on 2008-05-10
Have you installed any codecs from synaptic or Ubuntu restricted extras or gstreamer from add remove.

---

### Post by cyberkost on 2008-05-15
> **Bubba64 said:**
> Have you installed any codecs from synaptic or Ubuntu restricted extras or gstreamer from add remove.

I'm having the same problem with .avi file. I did NOT install new codecs specifically, but
1) this .avi worked right after OS installation
2) it stopped working after I've install something (I don't recall what it was, it could have been Adobe flash player plugin for Firefox)
3) VLC plays the file Ok

I re-installed totem-gstreamer using synaptic, but it did not fix the issue.  So, the question remains -- how do I make movie player (or movie player (gstreamer) to play this movie?

---

### Post by mc4man on 2008-05-15
>  " Failed to connect steam: Invalid argument "
Is that steam or stream?
Maybe try to set audio to alsa in affected players

---

### Post by Exsecrabilus on 2008-05-15
If you got it from a site or LimeWire or something that lets you download free movies or clips, chances are, it's a virus file.

It was probably meant for a Windows computer, so when you click to play it, it'll destroy your computer. I recommend you delete it.

---

### Post by cyberkost on 2008-05-15
Ok, I've done some research and this appears to be a known problem with pulseaudio (and not totem, though this is where people see it most often).  Change in System/Preferences/Sound all default/pulseaudio settings to alsa and you'll be Ok.  I did the change and it solved the problem for me.

---

### Post by gustabuntu on 2008-06-10
Hi all

Problem: Is not totem, is actually something about pulse-audio conflicting with another package. It was working OK for me until I downloaded the packages to play mp* and play dvds, and after that, I got the same error.

Solution: I've disabled pulse-audio (new to ubuntu 8) from the system/session menu (and killed the process), and I reactivated the ALSA sound via services, and all works perfectly.

Is such a shame because people expect to install the OS and find all working. Is hard to get people to move to ubuntu when something like mp3 and sound are is working properly. I think pulse-audio should be optional for a few releases until is proven to be working always.

---

