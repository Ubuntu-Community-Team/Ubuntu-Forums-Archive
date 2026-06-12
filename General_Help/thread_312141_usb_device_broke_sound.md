---
title: "usb device broke sound?"
date: 2006-12-03
forum: General Help
---

### Post by shoagun on 2006-12-03
This is kind of an odd problem.  After I installed ubuntu a while back, sound worked perfectly.  Multiple applications could use sound at the same time, including mplayer, xmms, firefox (youtube, google video, flash, etc).  All of this worked automatically, so I never tinkered with sound.  

I recently tried using a USB auido adapter because my headphone jack broke on my laptop.  This is essentially a usb soundcard.  I plugged it in, and it was automatically detected.  It didn't quite work correctly. 

I unplugged the usb soundcard, and now sound is broken.  I can no longer have multiple applications using sound at the same time.  

Does anyone know how this might have happened?  Or does anyone have an idea how I can go back to however sound was set up before ever plugin in the usb device?

---

### Post by drphilngood on 2006-12-04
You can try troubleshooting your problems with this guide:

[Comprehensive Sound Problem Solutions Guide v0.5e]("http://www.ubuntuforums.org/showthread.php?t=205449")

---

### Post by shoagun on 2006-12-04
> **drphilngood said:**
> You can try troubleshooting your problems with this guide:

[Comprehensive Sound Problem Solutions Guide v0.5e]("http://www.ubuntuforums.org/showthread.php?t=205449")

I wasn't sure how to use that guide because my soundcard actually does work.  For some reason, I just can't use multiple applications anymore.  I tried purging alsa and reinstalling it (and consequently had to reinstall gdm and ubuntu-desktop), but that didn't help at all.

---

### Post by drphilngood on 2006-12-04
> **shoagun said:**
> I wasn't sure how to use that guide because my soundcard actually does work.  For some reason, I just can't use multiple applications anymore.  I tried purging alsa and reinstalling it (and consequently had to reinstall gdm and ubuntu-desktop), but that didn't help at all.

I would start by experimenting with the settings in your Alsa mixer(I am constantly adjusting mine).  My guess would be that one of the controls has simply been muted as some programs change the settings for some reason when they start.  In addition, don´t forget that there are additional controls that you might need to add through ¨edit¨ -> ¨Preferences¨ in the Alsa mixer in order to adjust them.

---

### Post by shoagun on 2006-12-04
A good suggestion.  However, I know this is not the problem.  Before, XMMS had no problems, now it says the soundcard is not working.  If I change the output plugin to OSS driver, it works, but then nothing else can use sound.  If I try to open a video in mplayer while XMMS is playing, I get an error.  If I close XMMMS, then the video opens and works with sound.

---

### Post by drphilngood on 2006-12-04
> **shoagun said:**
> A good suggestion.  However, I know this is not the problem.  Before, XMMS had no problems, now it says the soundcard is not working.  If I change the output plugin to OSS driver, it works, but then nothing else can use sound.  If I try to open a video in mplayer while XMMS is playing, I get an error.  If I close XMMMS, then the video opens and works with sound.

I had the same thing happen, including the error message, but it was XMMS and a flash video.  I had to open both windows, pause the flash video and then open the Alsa mixer to unmute the setting in question.  Funny thing is, it started for me after the flash update a couple of days ago.

Not saying this is your problem, just telling you my story.

Good luck!

edit:
see [this thread]("http://www.ubuntuforums.org/showthread.php?t=312309")

---

### Post by karderio on 2006-12-07
I had a problem similar to yours, I just stumbled upon a solution to mine so I thought I'd post it here, maybe it could ghelp you too.

I had two cards, a SB live, and an integrated ICH. I removed the SB Live, and after audio would work in only one app at a time with the other card. It seems ALSA was no longer working, apps were using OSS which aparently locks the soundcard...

I found a command called "asoundconf". If you type "asoundconf list" in a terminal, it will give you the list of available cards. The trick seems to be using this command to set the default card as so : "asoundconf set-default-card [name_of_card]", replacing [name_of_card] with the name got from the list.

Remember to set all your apps to use ALSA afterwards.

Hope this helps :o)

Love, Karderio.

---

### Post by shoagun on 2006-12-07
Thanks for the suggestion Karderio.  However, this solution doesn't seem to apply to me.  I already have my default soundcard correctly set and my applications set to use ALSA.

---

### Post by karderio on 2006-12-08
> **shoagun said:**
> Thanks for the suggestion Karderio.  However, this solution doesn't seem to apply to me.  I already have my default soundcard correctly set and my applications set to use ALSA.

Sorry this doesn't help :(

Just a quick note for others : with my problem, despite the default card seeming to be set to the right one in all the graphical tools, it still needed setting via the command line.

Shoagun seems to have a different problem however, as his ALSA seems to be working :-/

Love, Karderio.

---

