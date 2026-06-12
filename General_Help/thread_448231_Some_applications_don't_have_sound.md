---
title: "Some applications don't have sound"
date: 2007-05-18
forum: General Help
---

### Post by joslinar on 2007-05-18
Hello There, I'm using Edubuntu. I am able to play sound files with Totem music player but some applications like games don't have sound. The only thing I was doing before I notice the lack of sound was configuring the LTSP clients for the first time.

---

### Post by dbott67 on 2007-05-18
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 7 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

You may want to check for the presence of a hidden file in your home directory called .asoundrc.

-Dave

---

### Post by joslinar on 2007-05-18
I don't know how to thank you enough. I'm I really thankful. It worked.
My man,
You Rock!!! :guitar:

---

