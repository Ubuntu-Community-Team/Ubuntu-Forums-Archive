---
title: "New Install - Can't get sound working"
date: 2005-06-23
forum: General Help
---

### Post by Duffy on 2005-06-23
Just installed Ubuntu.  The startup sounds come through perfectly.  With nothing else running, when I try to play an MP3 file from a CD, it tries to start Totem and gives me the following error message "ALSA device "default" is already in use by another program" - what other program?  I did not start anything.  This is after a reboot.  OSS is what I'm using for the mixer, not the other choice ALSA - I am confused!  Anyone shed some light on how to get the audio working?

---

### Post by elvis on 2005-06-24
First obvious question, what sound hardware are you using?

From a terminal, typing:

"sudo lspci"

will tell you.

Secondly, look through your kernel's boot messages and see if there are any glaring errors referring to sound problems:

"dmesg | less" and use the arrow keys, or page up and page down keys.

ALSA is what you should be using.  OSS is depreciated in the 2.6 kernels.

---

### Post by Duffy on 2005-06-24
[QUOTE=elvis]First obvious question, what sound hardware are you using?

From a terminal, typing:

"sudo lspci"

will tell you.

Secondly, look through your kernel's boot messages and see if there are any glaring errors referring to sound problems:

"dmesg | less" and use the arrow keys, or page up and page down keys.

ALSA is what you should be using.  OSS is depreciated in the 2.6 kernels.[/QUOTE]

The sound hardware is part of the motherboard.  It shows it is an ATI Technologies Inc. IXP150 AC'97 Audio Controller.

The only issue in dmseg is PCPI: Looking for DSDT in initrd....not found!

Everything else looks good.

Switched to the other audio mixer, and it still has the sma problem.

---

### Post by Duffy on 2005-06-24
O.K., I have partial resolution.  I unchecked "sound server" which appears to be what controls issuing sounds to different system event.  Now, the Totem player comes up, but says it does not have the codecs to play a simple MP3 file!  What has to be downloaded for that.  I thought those codes would have come with the system.

And ubuntu does not have the ability to have multiple sound programs going at the same time like Windoz?  I would have thought the sound server could run at the same time as a CD player application.  A bit surprising or is does something else have to be checked or unchecked to allow that?

---

### Post by elvis on 2005-06-24
Installing codecs in Ubuntu:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

As for two audio streams at once:  AFAIK this is an issue that many people find frustration with, and there doesn't seem to be a simple answer.  I can't help you there, I'm sorry.

---

### Post by Dave_is_sexy on 2005-06-24
Oh it's well complicated. It's possible with ALSA but hard. I can play multiple songs now but not much more. there's no sound it any gtk aps which is a pain

---

