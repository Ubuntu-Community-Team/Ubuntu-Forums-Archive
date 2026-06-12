---
title: "So ubuntu is great and all...."
date: 2008-05-07
forum: General Help
---

### Post by JacobZlogar on 2008-05-07
So, Ubuntu is great, i love it, i love the GUI, the customization, the easy downloading, and i just love it compared to XP, vista. But i'm having two problems. 
1- My sound, it's incredibly incredibly low, even with my speakers all the way up and the volume turned all the way up. I have a soundMAX audio card and dell speakers, i tried adjusting values in Alsamixer, nothing... 
2- The flash extension for firefox seems to be messed up, when i first dloaded ubuntu i was going to dload the firefox flash plugins and i ended up dloading some codec, idk... but anyways now whenever i go to watch a video theres a grey arrow with a circle around it and i have to click on this to watch the video. Is there any way to get rid of this?
Any help would be greatly appreciated

---

### Post by danwood76 on 2008-05-07
1.
What is the exact model of your sound card?

Could you post the results of this command in the terminal?

```

lspci | grep -i audio

```

2. Search flash in synaptic package manager and remove gnash if you have installed it.

Then search for flashplugin-nonfree and install that.

---

### Post by JacobZlogar on 2008-05-07
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Do i want to remove gnash -common, gnash -cygnall, and gnash -tools as well?

---

### Post by abuakel on 2008-05-07
2. Search flash in synaptic package manager and remove gnash if you have installed it.

Then search for flashplugin-nonfree and install that.[/QUOTE]

I too have the gray arrow problem with flash in Firefox. I tried what you suggested but with no avail. and I never had gnash installed. When I got Firefox, I installed a plug-in (to the best of knowledge) but forgot what it was.

---

### Post by JacobZlogar on 2008-05-07
I think i figured it out, theres a mozilla extension known as flashblack, which is on my computer. except i dont know how to uninstall it..

---

### Post by JacobZlogar on 2008-05-07
*flashblock

---

### Post by danwood76 on 2008-05-07
if you go tools -> addons you should be able to disable it.

gnash is poor for watching youtube videos, unfortunatly the nonfree version seems to be the only one that works.

---

### Post by JacobZlogar on 2008-05-07
Ok, what can i do about my sound though?

---

### Post by danwood76 on 2008-05-07
Your soundcard should be fully supported as its quite old.
Is this a laptop or desktop PC?

What exact model of PC do you have?
You may need to specify some alsa options to get your card working properly

---

### Post by JacobZlogar on 2008-05-07
Desktop, dell dimension 8400

---

### Post by N.N. on 2008-05-07
Perhaps the following wiki entry can be of help to you: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). Also, I read a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859") on launchpad where someone said that it could be fixed by simply appending the following to /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=auto
```
It should be risk-free to try it out. However, that fix could be obsolete by now or simply not relevant to your sound card.

---

### Post by davidpbrown on 2008-05-07
I found that the PCM was turned right down. Long time ago now so I can't recall but check volume manager for the levels of Master, PCM and Front all of which appear to have a large contribution to the overall. I now have the PCM and the main volume control in the panel.

---

### Post by davidpbrown on 2008-05-07
Should have suggested also Surround which was default to zero turning that up was wonderful having had no sound for a year \\:D/

---

### Post by abuakel on 2008-05-07
> **JacobZlogar said:**
> I think i figured it out, theres a mozilla extension known as flashblack, which is on my computer. except i dont know how to uninstall it..

hmm, that's not what I have. Here is the list of Pugins for me:
Default Plugin
Demo Print Plugin for unix/linux
DivX Web Player
Helix DNA Plugin: RealPlayer G2 Plugin Compatible (compatible; Totem)
iTunes Application Detector
QuickTime Plug-in 7.2.0
Shockwave Flash
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin (compatible Totem 2.22.1)
Windows Media Plug-in 10 (compatible; Totem)

and that's it. :confused:

---

