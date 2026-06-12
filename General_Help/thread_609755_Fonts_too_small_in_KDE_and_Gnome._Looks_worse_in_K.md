---
title: "Fonts too small in KDE and Gnome. Looks worse in KDE."
date: 2007-11-11
forum: General Help
---

### Post by Serpiko on 2007-11-11
hey everyone.

I recently installed Ubuntu 7.10 on my Intel pentium IV  pc and had no problems, except the fonts on all program bars were too small. (u know where it says for example "firefox, ubuntu forums" that part of the program ui )


Btw my gfx card is an ATI x1950 and im using a samsung tv (1360x768 res) as my main monitor.


I didn't mind working with this bug but after i installed kde (and got rid of gnome) i see i can't use ubuntu any more.
Everything on kde has small fonts. The menus, everything and i prety much can' do anything about it since i can't find where is the control panel and maybe tweak the settings there.


Can somebody help me fix this, using keyboard shortcuts or something?

---

### Post by tubasoldier on 2007-11-11
It would more than likely have something to do with the DPI (dots per inch) of your computer. You can set this in the xorg.conf file. I have not had to do this for quite some time. 
Here is a list of a few websites with informatino on the subject. Definitely read up on it before you commit anything:

[http://scanline.ca/dpi/](http://scanline.ca/dpi/)
[http://linux-blog.org/index.php?/archives/227-KDE-and-Xorg,-Fonts-and-DPI.html](http://linux-blog.org/index.php?/archives/227-KDE-and-Xorg,-Fonts-and-DPI.html)
[http://www.linuxquestions.org/questions/linux-software-2/how-to-stop-dpi-from-changing-on-resolution-change-403450/](http://www.linuxquestions.org/questions/linux-software-2/how-to-stop-dpi-from-changing-on-resolution-change-403450/)
[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

Hope this helps

---

### Post by Happy_Man on 2007-11-11
For KDE at least, it's easy enough. Right-click an empty area of the desktop and click "Run Command". Enter ```
kcontrol
``` and navigate to Appearance and Themes --> Fonts. Click the adjust all fonts button and tweak it up until it's readable.

---

### Post by Serpiko on 2007-11-11
Ill try this in a minute. Do you mind telling me which is the run command? I mean, is it the first in order after i right click, the second, what? :( Can't make it out.

Some screenshots would help if it isn't much of a hassle :)

---

### Post by Happy_Man on 2007-11-11
When you right-click on an empty area of the desktop, it's the second one down. Should have a gear icon.

---

### Post by Serpiko on 2007-11-11
> **Happy_Man said:**
> When you right-click on an empty area of the desktop, it's the second one down. Should have a gear icon.

YES! It worked! I also changed dpi to 120 grasping from tubasoldiers answer and everything seems to work ok! I switched every font to size 20 :)


Thank you guyz!

---

### Post by Serpiko on 2007-11-11
Well, now that i can see right, i tried some combinations.


It seems that with Menu Font set to size 20, i get a decent start menu, but huge menu buttons IN programs. There seems to be no middle setting, after 20 my start menu becomes unreadable. Any clues on how to change that separately?

---

### Post by Happy_Man on 2007-11-11
Well, right above the button I told you about earlier, there should be a whole list of fonts. One of them is for the menu. Edit that, and you should be good.

---

