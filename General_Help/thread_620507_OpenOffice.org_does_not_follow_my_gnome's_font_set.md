---
title: "OpenOffice.org does not follow my gnome's font setting"
date: 2007-11-22
forum: General Help
---

### Post by wersdaluv on 2007-11-22
Before, I put [this]("http://taimila.com/files/fonts.conf") to my .fonts.conf for me to have smoother fonts and openoffice.org followed the font setting. A while ago, I chose "Subpixel Smoothing" as the rendering option. After doing that, my OpenOffice.org fonts were smooth no more.

Any idea on how I can make OpenOffice.org's fonts smooth again? :D

---

### Post by wersdaluv on 2007-11-22
Here's a screenshot...

---

### Post by rune0077 on 2007-11-22
Hmm, I have no idea how to help you, but I just really want my fonts to look like yours. Only, I have no fonts.conf to drop those lines you mentioned in. Where do I find it? Can I just create it, and if so, where do I put it?

Oh, and you're welcome for all the fantastic help I gave you;)

---

### Post by wersdaluv on 2007-11-22
> **rune0077 said:**
> Hmm, I have no idea how to help you, but I just really want my fonts to look like yours. Only, I have no fonts.conf to drop those lines you mentioned in. Where do I find it? Can I just create it, and if so, where do I put it?

Oh, and you're welcome for all the fantastic help I gave you;)

sudo gedit /home/<your user name>/.fonts.conf then copy and paste the text from [http://taimila.com/files/fonts.conf](http://taimila.com/files/fonts.conf) :)

---

### Post by avik on 2007-11-22
> **wersdaluv said:**
> sudo gedit /home/<your user name>/.fonts.conf then copy and paste the text from [http://taimila.com/files/fonts.conf](http://taimila.com/files/fonts.conf) :)

No need for sudo.  It's in your home folder, so it's owned by you.  Also, make sure to restart the X server (Control-Shift-Backspace).

As for the OP, I don't know of any way.  Is OO.o a Java application?  If so, there's not much I can say about getting it to respect you and your environment.  :)

---

### Post by FuturePilot on 2007-11-22
> **avik said:**
> No need for sudo.  It's in your home folder, so it's owned by you.  Also, make sure to restart the X server (Control-Shift-Backspace).

As for the OP, I don't know of any way.  Is OO.o a Java application?  If so, there's not much I can say about getting it to respect you and your environment.  :)

Yes, OO does use a lot of Java code. Also it's not a true native GTK app, so it's not going to follow the GTK rules.

---

### Post by rune0077 on 2007-11-23
> **wersdaluv said:**
> sudo gedit /home/<your user name>/.fonts.conf then copy and paste the text from [http://taimila.com/files/fonts.conf](http://taimila.com/files/fonts.conf) :)

Yay, I now have pretty icons. Thanks a bunch!

---

### Post by wersdaluv on 2007-11-23
What about my problem?! hahahaha

---

### Post by rune0077 on 2007-11-23
What problem was that again? Nah, just kidding.

I checked my OpenOffice, and the fonts there are the same as they used to be. Nothings changed. Everything else looks better though, far as I can tell. So, I know practically nothing about fonts (minus the practically), but could it be that OpenOffice just uses its own font.config file somewhere? Dunno, it was just a guess.

---

### Post by wersdaluv on 2007-11-25
*bump*bump*bump*

---

