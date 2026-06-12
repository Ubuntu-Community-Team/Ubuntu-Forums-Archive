---
title: "opening vlc player in terminal window"
date: 2013-05-23
forum: General Help
---

### Post by Catoga on 2013-05-23
when my computer finished updating from ubuntu to kubuntu...a few of my programs don't run.  For instance, vlc player...it won't open and dragon player won't work. Does anyone have the codes for updating vlc player and dragon player?

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **General Help**.*

Please use regular text. Your post has been edited accordingly. From the forum Code of Conduct:

[QUOTE=Ubuntu Forums CoC]Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

[/QUOTE]

Also, not sure what your thread title has to do with your post. Title mentions opening VLC in a terminal (open terminal, type 'vlc') but your post mentions nothing about it. I can change the title to reflect your problem more appropriately if you'd like.

Try this, one after the other, in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

If there's any packages/apps that have an upgrade waiting that will upgrade them, and NOT the release so don't panic. Good luck.

---

### Post by josephmills on 2013-05-23
what happens when you open your terminal (ctrl+alt+t)and enter in
```
vlc -v 
``` 

 what  is printed to the terminal screen can you paste that here ?

---

### Post by Catoga on 2013-05-23
@josephmills....this is what it says....VLC media player 2.0.6 Twoflower (revision 2.0.6-0-gbe9623c)[0x8509908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

---

### Post by deadflowr on 2013-05-23
What is the output of just running "vlc" in the terminal?

Does it launch anything, or give you text outputs?

---

### Post by josephmills on 2013-05-23
there should be more then that -v just means list things verbose aka debug well kinda but there should be way more things at least a seg fault if it does not launch 

try again

---

### Post by Catoga on 2013-05-23
@Bucky Ball...sorry about the color font...my favorite color is brown...didnt think it would be a problem. after sudo apt-get update...and sudo apt-get upgrade...vlc player and dragon player not opening. 
any more ideas?

---

### Post by Catoga on 2013-05-23
@dead flowr...when i typed vlc -v...all that was shown was "[COLOR=#000000]VLC media player 2.0.6 Twoflower (revision 2.0.6-0-gbe9623c)[0x8509908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.".....in reference to what is the output of running vlc in the terminal window...im not sure...what do i have to do exactly to get the output?

[/COLOR]

---

### Post by Catoga on 2013-05-23
@josephmills...when i typed it again..it says the same thing..[COLOR=#000000]VLC media player 2.0.6 Twoflower (revision 2.0.6-0-gbe9623c)[0x8509908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.....do you think i need to reinstall vlc player? and if so, do you know the terminal codes? when i checked in my ubuntu software center...it says that vlc player is installed.[/COLOR]

---

### Post by deadflowr on 2013-05-23
Do you get a vlc window to open at least?

If you try running a video or something using the cvlc command like such
```
cvlc path/tovideo/file.avi,or-something
```

Does it open a video screen, or do nothing?

---

### Post by Catoga on 2013-05-23
this is what it says once i type........cvlc path/tovideo/file.avi
rene@rene-Dimension-2300:~$ cvlc path/tovideo/file.avi
VLC media player 2.0.6 Twoflower (revision 2.0.6-0-gbe9623c)
[0x8ce81c0] dummy interface: using the dummy interface module...
[0x8b7ebe8] filesystem access error: cannot open file /home/rene/path/tovideo/file.avi (No such file or directory)
[0x8b7ebe8] main access error: File reading failed
[0x8b7ebe8] main access error: VLC could not open the file "/home/rene/path/tovideo/file.avi". (No such file or directory)
[0xb52005f0] main input error: open of `file:///home/rene/path/tovideo/file.avi' failed
[0xb52005f0] main input error: Your input can't be opened
[0xb52005f0] main input error: VLC is unable to open the MRL 'file:///home/rene/path/tovideo/file.avi'. Check the log for details.

---

### Post by Catoga on 2013-05-23
so to answer your question @dead flowr...it does nothing

---

### Post by Catoga on 2013-05-23
no it does nothing

---

### Post by andrew.46 on 2013-05-24
A slight misunderstanding: 'pathtovideo' is intended to be the *actual *path to (or location of) your own video :).

---

### Post by deadflowr on 2013-05-24
> **andrew.46 said:**
> A slight misunderstanding: 'pathtovideo' is intended to be the *actual *path to (or location of) your own video :).

+ let's say 6.

---

