---
title: "No Sound through HDMI"
date: 2024-01-03
forum: General Help
---

### Post by SciGuy1872 on 2024-01-03
Hi. I have sound through my screen using the HDMI--it was working before but now there is no sound.  I was wondering what I could do about this.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293263&stc=1[/IMG]

---

### Post by ActionParsnip on 2024-01-03
If you install and use pavucontrol, does it help? You don't need a screenshot for text, just post the text

---

### Post by SciGuy1872 on 2024-01-03
Hi.  The sound worked reliably until now; I tried to make the machine boot from a usb of Windows so that I could install it alongside 22.04 Mate in order to play a Windows game.  I changed the UEFI settings and the boot order--I don't think these could affect the sound output.
     As you can see in the screenshot, PulseAudio reports the HDMI as unplugged; how would it be unplugged after I didn't mess with the cable?  Furthermore, I still have display--I would expect that to go out too.

---

### Post by ActionParsnip on 2024-01-03
I'd reseat the cable or try a new cable if possible

---

### Post by SciGuy1872 on 2024-01-03
I was wondering if this screenshot indicates what the problem is?  I can see the sound meter increase and decrease with what the people on the streaming channel are saying.

---

### Post by SciGuy1872 on 2024-01-04
The issue is solved--I just had to reinstall the Nvidia proprietary driver; the sound now works and my flight sims work.

---

