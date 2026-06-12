---
title: "Rhythmbox"
date: 2015-08-24
forum: General Help
---

### Post by prc320 on 2015-08-24
I have installing Rhythmbox on 14.04 LTS but it can't get music of the Blackberry 10. What am I doing wrong?

trebor

---

### Post by prc320 on 2015-08-26
any ideas?

---

### Post by Frogs Hair on 2015-08-26
This thread is very old, but might be worth looking at.   [http://ubuntuforums.org/showthread.php?t=1401643](http://ubuntuforums.org/showthread.php?t=1401643)

---

### Post by prc320 on 2015-08-26
Where do they put the file?

---

### Post by Frogs Hair on 2015-08-26
Home , press CTRL + H to display hidden folders. Files starting with a . are hidden. Example : .config

---

### Post by prc320 on 2015-08-26
I don't understand,walk me through the operations please?

---

### Post by Frogs Hair on 2015-08-26
The instruction explains it better than I could and I don't have blackberry so can't work through the process and explain it. Unfortunately most of the threads on the subject are old and Rhythm Box has changed since then. I will see what else I can find though.

---

### Post by prc320 on 2015-08-27
ok thanks

I need to know if it is pc or blackberry and on the pc whether it is cli or gui

---

### Post by howefield on 2015-08-27
What exactly is it that you are trying to do ?

You have music on the Blackberry that you want to play on the computer via Rhythmbox, is that right or is it something else ?

---

### Post by prc320 on 2015-08-27
Yes I have music on the Blackberry and I want it on the Rhythbox to play music!

---

### Post by howefield on 2015-08-27
Try this, open gedit and paste the following into it..

```
audio_folders=/Blackberry/music/
```

and name it..

```
.is_audio_player
```

Connect the Blackberry to the computer and unlock, set it it to USB device if offered. Open the file manager and navigate to /media/user/BLACKBERRY/ and copy the file that you made into this (perhaps the screenshot will help).

You should then see the Blackberry listed in Rhythmbox.

I get some import errors after that, but it might be enough to get you going. To be honest, I'd recommend Clementine which recognises the Blackberry straight away and imports and plays music from the phone like a champ. Much better music player than Rhythmbox imo.

---

### Post by nmyrick on 2015-08-28
In my opinion, what you did wrong was to install RhythmBox. Have you tried Banshee?  It is a much superior media player. You can go to the website at [http://www.banshee.fm](http://www.banshee.fm) to check it out.

To install Banshee, open a terminal and run the following commands:

[COLOR=#333333][FONT=Droid Sans Mono]sudo add-apt-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get upgrade




[/FONT][/COLOR]

---

