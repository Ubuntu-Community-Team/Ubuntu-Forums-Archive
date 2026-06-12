---
title: "Gutsy hardware confusion -- no sound."
date: 2007-10-19
forum: General Help
---

### Post by khazor on 2007-10-19
I installed Gutsy yesterday, and everything seemed ship-shape. Today, I can't get sound to function correctly. Seems like the sound issue is a common problem, but I haven't seen anything about this particular variation:

When I load alsamixer from the terminal, it shows this (which is correct):
Card: ATI IXP
Chip: Conexant id 30

System > Sound displays "Conexant id 30 (OSS Mixer)" as the only available device. 

The volume control preferences on the panel only detects Conexant id 30 as a sound controller, but it should be using ATI IXP... and it WAS yesterday, but not when I booted up today. 

However, when I doubleclick the volume control, the following appears: "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

When I try and play a sound file, this shows up: 
"Couldn't open audio.
Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard. [sic]
3. Your soundcard is configured properly."

Here is my card information from lspci:
"00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)"

...What can I do to get my sound back?

---

### Post by anaconda on 2007-10-19
This is a long shot, but do you belong to audio group? If you dont then you dont have the rights to use your sound card..

You can check it eg. from terminal. just type:
groups

and if audio is mentioned then you are ok. if not you can add yourself to audio group with:
sudo adduser yourusername audio
and reboot..

PS. if you dont belong to audio, then you propably dont belong to some other groups which you should belong to.. eg. cdrom..

---

### Post by khazor on 2007-10-19
Yeah, I'm in the group, but that was a good tip; I didn't even know about that.

Still have the problem though. :-/ 

But thanks.

---

