---
title: "Cannot listen to music and play videos at the same time... (OSS and ALSA conflict)"
date: 2008-02-26
forum: General Help
---

### Post by linuxvacuum on 2008-02-26
Hi, I listen to music with the following mplayer command, so I can upmix stereo to 5.1 speakers :)
> mplayer -channels 6 -af pan=6:1:0:1:0:0.5:0.5:0:1:0:1:0.5:0.5 "$@"

But if I am listening to music, or even if it is paused, then I am unable to hear sound from flash videos (Youtube.com, Metacafe.com, etc.) in Firefox!

How can I solve this problem? Doesn't OSS allows multiple sound sources?

---

### Post by der_joachim on 2008-02-27
Depending on your sound card, alsa supports resourse sharing. Only very old sound cards may break if you configure alsa sharing, but I reckon that that's why it isn't enabled by default. My 10 yr old SB128 works pefectly.

To configure alsa sharing, I recommend trying [this guide]("http://alsa.opensrc.org/AlsaSharing").

---

### Post by linuxvacuum on 2008-02-29
I have an integrated 8 channels AC97 nvidia sound card. Why doesn't Ubuntu enable alsa sharing by default?

---

### Post by der_joachim on 2008-03-01
Apparently, some very very old cards have a slight chance to break when alsa sharing is enabled. Any other reason not to enable alsa sharing is unknown to me. Even googling did not get me a satisfying answer. Perhaps different cards need different settings? Dunno. Configuring alsa is some kind of black magic mumbo jumbo to me to be honest. ;)

Your AC97 is probably safe though. I had one, in my last PC, which worked perfectly with the guide above.

---

