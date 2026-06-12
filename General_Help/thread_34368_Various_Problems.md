---
title: "Various Problems"
date: 2005-05-14
forum: General Help
---

### Post by monkeybounce on 2005-05-14
Ok, I'm sorry if this doesn't make any sense, but I'm a linux newbie (I admit it) and am having several problems since upgrading from Warty to Hoary.

First problem--
I have no sound in VLC.  I don't quite know what to do.  I have sound in any other application, but when I try to use VLC to play DVD's, I get the message:

[00000247] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000256] oss audio output error: cannot open audio device (/dev/dsp)
[00000268] main private error: no audio filter module matched "ALSA"
[00000256] main audio output error: cannot add user filter ALSA (skipped).

I've checked the internet and have found nothing that I can understand to help me.

Thanks for any help on this one.

Second Problem--
For some reason, my up arrow key does not work.  It is the only key that doesn't work on my keyboard within Hoary.  It works in BIOS and Grub but not within anything inside the Hoary Desktop.  I've got a Toshiaba Satellite a15-s127 if helps at all.

Third Problem--
Evolution Mail will not connect to my exchange server.  It tells me that the backend process does not exist.  Again, I'm new and have no idea what to do to fix it.

I'm sorry for posting three problems in one thread, but I can't figure out where else to go.  Remember, I'm new and am getting very confused trying to fix this without "dumbed-down" help.

Thanks again!

Monkeybounce

---

### Post by bruizer on 2005-05-14
The issue you are seeing (#1 from original) is similar to something that I was seeing with XMMS. I could not get sound to play when upgraded from Warty to Hoary. The problem had to do with ALSA. Try swithing to use another output plugin like eSound.

Sorry, got nothing for the other 2 issues, hope this helps!

---

### Post by monkeybounce on 2005-05-16
I tried switching to e-sound but for some reason the change wouldn't take.  I would change it but it would automatially revert back to ALSA.  Then I looked some more and realized that the Codec that it was using for Audio was one that I had removed for some reason or another.  Once I changed the codec, everything worked just fine.  Thanks for the help though!
...now if I could just get the up arrow key to work, the Terminal would be so much easier....blast! \\:D/

---

### Post by bruizer on 2005-05-17
With the keyboard thing, what happens if you try to use another session (ie - Ctrl + Alt + F2)? It sounds like it probably has something to do with Gnome/KDE instead of hardware. Let me know if this works.

---

