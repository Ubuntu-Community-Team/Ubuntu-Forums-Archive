---
title: "Getting tired of this - who stole my soundcard?"
date: 2006-08-13
forum: General Help
---

### Post by zugu on 2006-08-13
I usually listen to online radio streams. But getting to know the wonders of Wine, I now also use my soundcard to play sounds in Windows games. I might use it to watch movies on YouTube, or to hear my friends using Skype.

However, there's a big problem I have: once a program gets to use the soundcard, no other program has sound. For example, if I start Firefox, go to YouTube and watch a movie, then start Diablo II - I have no sound in the game. I realised I need to close Firefox, as it's already using the soundcard. However, this isn't working either. Restarting the system solves the problem, only if Diablo II is the first application I start after login.

Same with movies. i just can't have XMMS playing something while VLC is running.

These are just examples. It's a complete mess. There's no way to tell what progam is using the soundcard. A visual interface would be nice, however, why can't just all the programs simultaneously use it? Like in Windows? I know Ubuntu is about choice - as far as I know there is ESS, ALSA and OSS in care of the sound on my system. However, none of them seems to do the right job (and yes, I know they are different things - but I also know they're supposed to be in charge of sound management, in some way).

So, are we living in the multitasking era or not?

---

### Post by wildutah on 2006-08-13
Same here.  Seems like I have to reboot after every time I use sound.

---

### Post by nanotube on 2006-08-14
go to the first link in my sig, and find the sound section. 
basically, the 'least invasive' way is to set your apps to use the esd sound daemon, instead of the soundcard directly. esd allows for the "multitasking" that you are looking for.

don't know how to do this for wine, though, but i bet there is a setting somewhere...

---

### Post by zugu on 2006-08-14
So basically, I need to set up programs to use ESD instead of directly using the soundcard. I get it. Thank you very much for the help.

---

### Post by th3james on 2006-08-14
Hi, I had the same problem, if that fix doesn't work for you, try this:

[http://ubuntuforums.org/showthread.php?p=1187967]("http://ubuntuforums.org/showthread.php?p=1187967")

---

### Post by zugu on 2006-08-14
Your answers were useful, thanks again. However, how do I set up a java applet to use ESS, and not directly my soundcard?

---

