---
title: "I don't know what else to do"
date: 2008-04-28
forum: General Help
---

### Post by kelvingeorge on 2008-04-28
Somebody please help me. I have been trying to get this flash issue in firefox working for about month now. I have tried almost everything on this forum and nothing seems to be working for me. No audio on youtube, myspace. Please help me. I think I just about had it with this issue.

---

### Post by quixote on 2008-04-28
Yeah, the flash stuff was driving me nuts too.  The secret is to install the regulation adobe flashplugin nonfree, rather than the nice open source stuff like swfdec or gnash :(

This page: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
has the most complete instructions to recover from a previous install of flash where the open source stuff was used. It's near the top under the heading "Adobe Flash Installation."  The crucial bit is doing this in a terminal: ```
sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla
```

(I installed the open source versions originally.  If you take the first choice when the popup to install additional plugins comes up, that may be what you did too.  The second choice is the one you want.  D.u.m.b. way to set up the automated flash installation!)

---

### Post by kelvingeorge on 2008-04-28
> **quixote said:**
> Yeah, the flash stuff was driving me nuts too.  The secret is to install the regulation adobe flashplugin nonfree, rather than the nice open source stuff like swfdec or gnash :(

This page: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
has the most complete instructions to recover from a previous install of flash where the open source stuff was used. It's near the top under the heading "Adobe Flash Installation."  The crucial bit is doing this in a terminal: ```
sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla
```

(I installed the open source versions originally.  If you take the first choice when the popup to install additional plugins comes up, that may be what you did too.  The second choice is the one you want.  D.u.m.b. way to set up the automated flash installation!)

Nope, didn't work for me. The videos just seem to be of a better quality now but still no audio with flash videos or the sites. Thanks for the help though. Anything else you could think of please let me know.

---

### Post by quixote on 2008-04-28
Audio is a different issue. That could be an mp3 problem.  For that you need something called liblame0 in the right plugins directory.  On that same site I linked, search on the page for "liblame" or "mp3" and see if some of those commands don't help.  I hope they do!

By the way, the fact that flash runs better means that your original problem probably was the same as mine: open source packages installed that couldn't really do the job.  That was the same symptom I had.

---

### Post by kelvingeorge on 2008-04-28
Mp3 plays fine its just no audio for videos on youtube. I installed the windows version with wine. I will just use this until everything in ff3 gets sorted out.

---

### Post by quixote on 2008-04-28
Using ff under wine seems like admitting defeat ;) but it may be the smartest thing to do.  I haven't had that problem.  Once I got the flash correctly installed I had sound (although before I hadn't), so I have no idea what's wrong.  Maybe just a bad install?  Maybe some weird setting on the flashplugin?

---

### Post by kelvingeorge on 2008-05-01
Still without sound. Is there a browser I can install that needs no configuration? Something that works as soon as you install it. I went back to  ff 2.0. Works well minus the audio which works for everything else.

---

### Post by quixote on 2008-05-01
The problem is that flash is not a free format.  (Although just today I saw on Slashdot that Adobe has decided to make it freely available.  Hallelujah!)  That means that any linux distro can't come with it pre-configured without paying royalties to Adobe, at least officially.  What you do yourself is your own fault, so to speak, which is why you have to go to all this trouble. :(

So, no, I don't think there's a browser *under free linux* that has flash pre-configured.  (Anyone who knows I'm wrong, speak up!)  

If I understand you right, sound isn't working even under wine.  That suggests to me that the problem may be somewhere in the sound software (ALSA?) rather than firefox or flash.  I know this sounds stupid, but right-click on the little speaker icon, open volume control, and make sure PC speakers, headphones, Master, are actually on.  Or maybe you've already done this?

---

### Post by damis648 on 2008-05-01
Install the package libflashsupport

That fixed it for me :)

---

### Post by kelvingeorge on 2008-05-01
> **quixote said:**
> The problem is that flash is not a free format.  (Although just today I saw on Slashdot that Adobe has decided to make it freely available.  Hallelujah!)  That means that any linux distro can't come with it pre-configured without paying royalties to Adobe, at least officially.  What you do yourself is your own fault, so to speak, which is why you have to go to all this trouble. :(

So, no, I don't think there's a browser *under free linux* that has flash pre-configured.  (Anyone who knows I'm wrong, speak up!)  

If I understand you right, sound isn't working even under wine.  That suggests to me that the problem may be somewhere in the sound software (ALSA?) rather than firefox or flash.  I know this sounds stupid, but right-click on the little speaker icon, open volume control, and make sure PC speakers, headphones, Master, are actually on.  Or maybe you've already done this?

Firefox works fine in wine just a bit sluggish. I felt as if the pc won when I gave up and used ff in wine....lol. What you said in your earlier post gave me that push to keep at it...lol. I tried all you suggested but still no luck. Thanks for the suggestions. Keep them coming thank you. Damis648, I installed libflashsupport before and still without sound. Thanks anyway.

---

### Post by kelvingeorge on 2008-05-05
I got youtube audio on firefox. I went to systen > preferences >session >startup programs tab  then check the box that says pulseaudio session management. I also followed the thread that said to edit the firefox file from "none" to "aoss". All this was done on Sunday and nothing happened and I am guessing it was because I needed to restart. I tunen on the laptop today and there was a screen prompting me to enter enable a default sound card. That was it.....sweeeeeeeeeeeeeeet sound. I am new to linux so any output you want me to check just let me know.

---

### Post by quixote on 2008-05-05
Thanks for sharing the solution!  One of the endearing / not endearing things about Linux (and Unix) is that there's always a way to do anything you want, it can just be near-impossible to find it.  :D

---

### Post by kelvingeorge on 2008-05-06
Just want to say thank you all for the suggestions. I really got me through when I wanted to give up.

---

