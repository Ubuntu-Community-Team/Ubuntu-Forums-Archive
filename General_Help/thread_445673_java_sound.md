---
title: "java sound"
date: 2007-05-16
forum: General Help
---

### Post by Whizardx on 2007-05-16
Well, I am pretty new to Linux.
My problem is that when java uses sound it seems to block everything else. I would like to play runescape and listen to music in the background.
I can't.
I can eighter hear runescape sounds and nothing else(If I start the browser(firefox, epiphany) without anything using sound), in that case XMMS tells me that sound card hasn't been correctly installed or something is blocking it.
Or I can listen to music and hear no runescape sounds.
I can hear multiple sounds if java is not one of them, like flash in browser and XMMS.
I read the few old topics around here and found them not helpful
Running the latest java version)6 or something) and latest firefox.
Ubuntu 7.04

Thank you!

---

### Post by mig5 on 2007-06-08
I have the same problem in opera using the blackdown java JRE from synaptic.  However, it doesn't seem to take control of the sound completly, as I can still hear my line-in (I have a radio device plugged into the line-in slot of my soundcard, which I can still hear when I'm using the sound on runescape).  I think its just taking over the PCM line.  Maybe the web browsers need ALSA/OSS sound add-ins or something?  But then how come I can watch videos on youtube and hear the sound from those and from my media player at the same time? (I'm using VLC media player)
Maybe there's some setting in Java config files or something.  I'm going to try installing java SDK, to see if that makes any difference.

On a side note I'd also like to point out the sound in runescape is very far behind for me, like I do something in-game and the sound comes 4 seconds later.  Do you have this problem?

---

### Post by mig5 on 2007-06-09
I've fixed the sound-take-over problem (in firefox).  You need to do the following:

1.  Goto a terminal and type 'sudo gedit /etc/firefox/firefoxrc' .
2.  On the file that it opens look for the line  FIREFOX_DSP=
3.  If after the equals sign it says 'none' or anything else except 'aoss' then carry on with these instructions.  If it already says 'aoss' then your problem isn't the same as mine.
4.  Close the text editor, without making any modifications yet.
5.  Go back to the terminal and type  'sudo apt-get install alsa-oss' .
6.  Once it has installed write 'sudo gedit /etc/firefox/firefoxrc' again.
7.  Find the line 'FIREFOX_DSP=' and change it to FIREFOX_DSP='aoss' (keep the commas around the aoss bit).
8.  Save the file and exit the text editor.
9.  Close any firefoxes that you have open.
10.  Next time you run firefox the new aoss driver wrapper will be used and you should be able to hear runescape and your music at the same time.

NOTE: the text editor I used here is gedit .  I'm not sure if comes preinstalled with Ubuntu (I'm using Xubunutu).  If you get a 'command not found error' or something similar when you try to use a command with gedit it probably means you don't have it installed.  In this case you can use some other editor or install gedit from synaptic.

PS: If this doesn't work for you try using the blackdown java instead of the sun one.  But if you do this make sure you unistall the sun one first, as they conflict.

---

### Post by mig5 on 2007-06-09
To do the same fix on opera do
sudo apt-get install alsa-oss
Then just change your opera launchers (shortcuts) to aoss opera (instead of just opera).
If your like me then you might want to change the launchers to
aoss opera -notrayicon
This stops opera using that annoying system tray icon (which I personally hate!).

---

### Post by foamy3 on 2007-08-08
I had the same problem and your fix worked flawlessly!  Thank you VERY much. :)

---

### Post by mig5 on 2007-08-08
You're welcome.  I'm still trying to fix my java sound problem :( , [http://ubuntuforums.org/showthread.php?t=497589](http://ubuntuforums.org/showthread.php?t=497589).

---

