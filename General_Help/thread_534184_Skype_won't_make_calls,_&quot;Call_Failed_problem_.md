---
title: "Skype won't make calls, &quot;Call Failed: problem with audio playback&quot;"
date: 2007-08-24
forum: General Help
---

### Post by baklava on 2007-08-24
Recently a buddy tried to give me a call through skype, (I'm using 1.4 beta) he was using the windows client. My speaker works fine, my audio works flawlessly, my microphone is working well also (I can hear myself through the speakers when I talk into it). 
However, when I make a call, it hangs up before it ever opens and says "Call Failed: Problem with Audio Playback"

I'm using ALSA on a Creative SB Live! 5.1 [SB0220] sound card. I've already tried to reinstall the skype .deb package. Help please?:(

---

### Post by cyberiaes on 2007-08-25
Okay, first time posting. But anyway, I had the same problem as you. I solved it by going to options. (click the gear like icon or Ctrl + O ). And then playing around with the sound devices. 

I use Audigy 2 Value and the options that worked for me are:

Sound In: Audigy 2 Value [SB0400] (hw:Audigy2,2)
Sound Out: Audigy 2 Value [SB0400] (hw:Audigy2,0)
Ringing: Default device (default)

Hope this helps.

---

### Post by sagara on 2007-08-26
Follow the instructions on this post: [http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16)
This fixed it for me!

---

### Post by cesium62 on 2008-01-07
This isn't working for me.  I recently upgraded from fiesty to gutsy.  I've had numerous problems with the bug in fiesty whereby gnome user administration trashes /etc/groups, but I seem to have rebuilt that file to where it should be.  I continue to have problems with Skype as described in the title of this thread.

I've tested both capture and playback with Applications:Sound Recorder and sound seems to work fine.  I've tested with System:Preferences:Sound, and that seems to work, if we ignore the known bugs with gstreamer seeming to generate spurious error messages.

I've used the Volume Control tool to turn on all of the inputs and outputs at least slightly.  I've fiddled around with selecting various inputs and outputs in skype.  If there is some magic settings for various items in various tools, those settings are eluding me.

---

### Post by ukripper on 2008-01-07
try using skype beta - download deb where it is written ubuntu feisty as it works fine with gutsy too.
[http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/)

---

### Post by cesium62 on 2008-01-11
Skype beta doesn't help.

---

### Post by cesium62 on 2008-01-11
I read various pages on the skype forums which suggested using "esddsp /usr/bin/skype" as a command in a terminal window.  When doing this, I got additional error messages telling me that a slave could not be started.  Googling the error text led to [http://ubuntuforums.org/showthread.php?t=601522](http://ubuntuforums.org/showthread.php?t=601522) .

I killed skype, executed "asoundconf reset-default-card", tested skype -- no better.

I killed skype, added libsdl-1.2-debian-all, tested skype, no better.

I killed skype, removed all installed 'pulse' software, added libesd-all, and tested skyp.  no better.

I rebooted.  Skype worked.

So I believe thread 601522 contains the solution to the problem I had, but I did not reboot at the correct location to figure out which step is necessary.

---

### Post by firmit on 2008-04-05
I just made an apt-get update/upgrade in 8.04 beta, and Skype won't work anymore. I found the reason to be that I had Listen - music-player running. I needed to close this before starting skype. Otherwise it would not work.

---

### Post by wayne888 on 2008-04-17
Thanks cyberiaes; this solve my problem as well. 
Cheers,
Wayne

---

### Post by diabolustheslayer on 2008-04-18
I'm sorry to bother with such matter, but i'm a totally new ubuntu user, don't know a **** about linux. I cannot make my skype work, it seems it's not recognizing the microphone, neither some other recording tools i managed to download, the info i've found in the forums doesn't seem to fit to my problem and i have to accept i don't really know what to look for. what can i do?

---

### Post by merj on 2008-06-22
Thank you cyberiaes. My settings were called something slightly different, but that got Skype working.

---

