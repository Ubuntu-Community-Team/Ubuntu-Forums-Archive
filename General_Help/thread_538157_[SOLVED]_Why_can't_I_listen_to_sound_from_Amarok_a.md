---
title: "[SOLVED] Why can't I listen to sound from Amarok and the internet at the same time?"
date: 2007-08-29
forum: General Help
---

### Post by bobleny on 2007-08-29
Why can't I listen to sound from Amarok and the internet at the same time?

If I'm listening to some Metallica ( :guitar: ) and decide to play some RuneScape ( :p ), there is no sound from RuneScape.

If I'm playing RuneScape and decide to listen to some Metallica, there is no sound from Amarok.

This is quite annoying....

How do I fix this?

Thanks!

---

### Post by mig5 on 2007-10-13
It's probably due to the way firefox interacts with the sound server (I had this problem aswell).  The way firefox is set up when you first install Ubuntu means that when firefox plays sounds it takes over the PCM sound channel (probably doesn't mean anything to you).
Anyway, here is how to fix it:

1. Goto a terminal and type 'sudo gedit /etc/firefox/firefoxrc' .
2. On the file that it opens look for the line FIREFOX_DSP=
3. If after the equals sign it says 'none' or anything else except 'aoss' then carry on with these instructions. If it already says 'aoss' then your problem isn't the same as mine.
4. Close the text editor, without making any modifications yet.
5. Go back to the terminal and type 'sudo apt-get install alsa-oss' .
6. Once it has installed write 'sudo gedit /etc/firefox/firefoxrc' again.
7. Find the line 'FIREFOX_DSP=' and change it to FIREFOX_DSP='aoss' (keep the commas around the aoss bit).
8. Save the file and exit the text editor.
9. Close any firefoxes that you have open.
10. Next time you run firefox the new aoss driver wrapper will be used and you should be able to hear runescape and your music at the same time.

NOTE: the text editor I used here is gedit . I'm not sure if comes preinstalled with Ubuntu (I'm using Xubunutu). If you get a 'command not found error' or something similar when you try to use a command with gedit it probably means you don't have it installed. In this case you can use some other editor or install gedit from synaptic.

---

### Post by bobleny on 2007-11-08
Sweet! Thanks a lot! I just wish I would of known about this 3 weeks ago when you posted it..... lol

---

