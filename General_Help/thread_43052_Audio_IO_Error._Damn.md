---
title: "Audio I/O Error. Damn"
date: 2005-06-20
forum: General Help
---

### Post by Dave_is_sexy on 2005-06-20
Hey. I don't really know what i'm doing yet, everything's a bit different to windows. However I do know that this error:

there was an error initiating the audio i/o layer
You will not be able to play or record audio
Error: Host Error

Is a bad thing, and means that I wont be a ble to play or record audio in Audacity (which gives the error).

Is something wrong with my drivers? Ican play vorbis and wav in rhythmbox. If we ignore the message and try to play something in the program anyway (hopeful) we get:

Error while opening ound device. 
Please check the output device settings and the propper sample rate

On inspecting these things there are none. Which would be the problem. 

Anybody? Thanks

---

### Post by intangible on 2005-06-20
Sounds like Audacity is trying to open /dev/dsp and something already has that locked up, probably ESD.

Try this before starting audacity, **killall esd**

Your gnome sounds won't work after that, but you'll be able to use audacity.

After finishing with audacity, just run **esd** to start the gnome sound server again.

What is probably happening is that your sound card only does software mixing, in other words it requires a program on the computer to act as a mixer for multiple sound sources (in Gnome that program is ESD).

Here's a thread to help your drivers themselves do the mixing instead of requiring ESD to do it: [http://www.ubuntuforums.org/showthread.php?t=30076](http://www.ubuntuforums.org/showthread.php?t=30076)

You will also want to install **libesd-alsa0** to replace **libesd0** with synaptic to make esd use the newer ALSA drivers instead of falling back to the old OSS drivers

---

### Post by Dave_is_sexy on 2005-06-20
OK I have done that. 
Ending ESD did allow Audacity to work
But even with the new ALSA thing we are seeing the same (exactly) problems.

I followed the guide but replaced nforce with cmedia.. cos cmedia make the sound chip.

Although now if i close all other audio aps it works. But that's not good enough. What if i needed both open to say.... record a real media audio stream?

---

### Post by intangible on 2005-06-20
Here ya go, this thread is a little more helpful and a better solution:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

However, anything that uses the OSS drivers will still lock the sound card.  Look through the settings of audacity and see if it has an option to use "ALSA"

---

### Post by Dave_is_sexy on 2005-06-20
OK we have a pipeline problem... naturally gnomeclipboard has forgotton it, because i closed the window i copied the text from (jeez).....

Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

And that occurs on default source input pipeline. OSS sems to work but with no sound... erm. I assume that's cos it's an input.

---

### Post by intangible on 2005-06-20
Sorry, I'm not familiar with all the intricate parts of the sound system, hopefully someone else will pick this up and run with it.

BUT on a good note, to make your clipboard maintain what's in it when you close the source application, install gnome-clipboard-daemon it's a life-saver.  I hope it's in Breezy by default.

Installing gnome-clipboard-daemon: 
[http://www.ubuntuguide.org/#clipboard-daemon](http://www.ubuntuguide.org/#clipboard-daemon)
or
[http://ubuntuforums.org/showthread.php?t=10319](http://ubuntuforums.org/showthread.php?t=10319)

---

### Post by Dave_is_sexy on 2005-06-20
Oh. Awesome clipboard mod. ^_^

Yeah, if anyone does want to help out that's absolutely fine. We have problems with ALSA source inputs *waves*  ;-)

---

