---
title: "Help - where had my sound gone!"
date: 2007-02-10
forum: General Help
---

### Post by sammydee on 2007-02-10
Hi.

I installed edgy on my T30 a couple of days ago. Everything worked fine (even beryl and aiglx) except that when you closed the lid down, the system would hang.

I was trying to sort it out, so i changed the settings in the gnome power management panel to suspend when the lid was closed. It suspended and booted itself back up quite happily - but then I noticed the sound wasn't working.

After numerous reboots and hard resets, shutdowns, hibernates whatever, there is still ABSOLUTELY NO SOUND on my system. Yes, the volume control is set to max, but there is still no sound. I get a beep if I plug or unplug the power cord, thats it. Playing videos, the ubuntu startup sound, the gdm startup sound, all gone.

How do I get my sound back?!?

Thanks
Sam

---

### Post by sauravbhaumik on 2007-02-10
Try checking whether any of your sound softwares (like Xmms, mplayer, real player etc) has been mute. I had this problem yesterday and I found that some of my music softwares was mute. I increased its sound and it worked.

---

### Post by amano on 2007-02-11
And make sure that neither your master nor your pcm settings are muted!

Check those in the taskbar volume applet.

---

### Post by dckirba on 2007-02-11
Here's a helpful howto:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solutions]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solutions")

Cheers,
David K

---

### Post by sammydee on 2007-02-11
Thanks guys, turned out the PCM channel on alsamixer was muted for some reason.

I'll bookmark that guide though, that's very helpful, thanks a lot!

Sam

---

