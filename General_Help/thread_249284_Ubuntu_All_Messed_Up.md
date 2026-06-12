---
title: "Ubuntu All Messed Up"
date: 2006-09-02
forum: General Help
---

### Post by TheReconHunter on 2006-09-02
Hey. I just tried installing the XGL/Compiz thing, but when i restarted the computer, I got a little suprise. It says X Server failed,  and when i look at the report, it says there is a fatal error. Is it possible to undo all changes since this morning, or somehow get my ubuntu working again without a reformat? Thanks.

---

### Post by whizbaby on 2006-09-02
Basically reinstalling the whole is not (nearly NEVER) necessary.
What changes did you apply ? (which packages newly installed and which configs edited?)

---

### Post by TheReconHunter on 2006-09-02
I tried folllowing these instructions [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

However, I got messed up on one part, and I used a command from the alternate way of doing it, before switching back to the way listed on the original post. Other than that, it was working fine this morning. However, if I could somehow undo all changes made since this morning, my problem would also be fixed.

---

### Post by mindtrick on 2006-09-02
I also don't know what to do with the command line if Xserver fails. I don't know the command for editing the xorg.config file. I've no idea if the xorg.config file can be configured through the command line. 
Once I had the same problem and reinstalled ubuntu from the CD.

---

### Post by whizbaby on 2006-09-02
Be descriptive, man.(which part,command,etc, I'm so bad at guessing...)

---

### Post by TheReconHunter on 2006-09-02
I changed basically every single file that the tutorial instructed, and in addition I ran this program

compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher

I have some really important files for school on there, and I cant afford to re-format. IF theres anything else i can help you wiht, just ask

---

### Post by moeFinley on 2006-09-02
How big are your important files.  Best to move them onto a floppy/USB Stick/Hard Drive first.  You can copy files at the command prompt using CP ([wiki]("http://en.wikipedia.org/wiki/Cp_(Unix)")),

Your floppy/USB Stick/Hard Drive will be in the 'media' folder.

In fact you could copy your whole home folder across?

I'm new to Ubuntu/Linux so I can't really help you with your X Server probs.  But I hope the CP thing helps.

---

### Post by whizbaby on 2006-09-02
Only to know: did you try this already (from the bottom of your howto-page)?


To Undo

This command:

Quote:
sudo gedit /etc/gdm/gdm.conf-custom

Then clear the file and save it.


If it doesn't help we will have to undo your changes to xorg.conf and gdm.conf.

---

