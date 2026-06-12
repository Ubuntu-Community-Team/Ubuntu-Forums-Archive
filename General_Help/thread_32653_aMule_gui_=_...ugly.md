---
title: "aMule gui = ...ugly"
date: 2005-05-08
forum: General Help
---

### Post by royg1234 on 2005-05-08
Hey all, how do I make aMule look pretty?  The way it is right now, it's so ugly ([screenshot](http://www.geocities.com/pilstilin9/Screensho_aMule2rc7.png)) I can't even use it because words are impossible to read.

XMMS looks like this also, but that's tolerable, since I don't have to endure it unless I do some right-clicking.

I've tried using different gnome themes, but aMule's gui hardly changes, and the letters don't change at all.

Thanks in advance!

---

### Post by tread on 2005-05-08
Is aMule using gnome? QT maybe?

---

### Post by Sam on 2005-05-08
[QUOTE=royg1234]Hey all, how do I make aMule look pretty?  The way it is right now, it's so ugly ([screenshot](http://www.geocities.com/pilstilin9/Screensho_aMule2rc7.png)) I can't even use it because words are impossible to read.

XMMS looks like this also, but that's tolerable, since I don't have to endure it unless I do some right-clicking.

I've tried using different gnome themes, but aMule's gui hardly changes, and the letters don't change at all.

Thanks in advance![/QUOTE]
XMMS uses skins, and in the same format as winamp. Just put the skin file into the ~/.xmms/Skins directory and hit Alt-S in XMMS and you skin will be there.
You can download skins [here (xmms)](http://www.xmms.org/skins.php) or [here (winamp)](http://www.winamp.com/skins/).

AFAIR, amule uses QT and there is a way to apply a theme on QT apps (try the steps on this [thread](http://ubuntuforums.org/showthread.php?t=32567))

---

### Post by bored2k on 2005-05-08
For the cute amule just get 2.00 fina from amule.org

---

### Post by RastaMahata on 2005-05-08
is there any way to get a "pretty gnome gui" amule deb?

---

### Post by royg1234 on 2005-05-09
> 

XMMS uses skins, and in the same format as winamp. Just put the skin file into the ~/.xmms/Skins directory and hit Alt-S in XMMS and you skin will be there.
You can download skins here (xmms) or here (winamp).

 

Yeah I skinned it, but when I right-click XMMS, the font's all jagged and almost impossible to read, just like in aMule (see screenshots).

---

### Post by bored2k on 2005-05-09
[QUOTE=RastaMahata]is there any way to get a "pretty gnome gui" amule deb?[/QUOTE]
 amule.org has a .deb for rc8, I'm not sure they have a .deb for the final one.

---

### Post by kestasjk on 2005-05-09
Look into sorting out your GTK (not GTK+) default font.

---

### Post by royg1234 on 2005-06-01
> Look into sorting out your GTK (not GTK+) default font. 

How do I do this?

---

### Post by ow50 on 2005-06-01
It's a gtk1 vs gtk2 thing. aMule debian packages are gtk1, because they can't compile with gtk2 on powerpc.

If you're using i386, you can try my packages:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

It's built for hoary from debian unstable sources altering it to gtk2.

---

### Post by Psquared on 2005-06-02
[QUOTE=ow50]It's a gtk1 vs gtk2 thing. aMule debian packages are gtk1, because they can't compile with gtk2 on powerpc.

If you're using i386, you can try my packages:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

It's built for hoary from debian unstable sources altering it to gtk2.[/QUOTE]

This worked out well for me .... except I could not install the amule-utils file because of some dependencies. Anyway, it looks much better. 

Thanks.

---

### Post by ow50 on 2005-06-02
[QUOTE=Psquared]This worked out well for me .... except I could not install the amule-utils file because of some dependencies.[/QUOTE]
Looking at the dependencies, they both seem to depend on the backported version of libgcc1. I hadn't noticed that. All other dependencies should be in normal hoary repositories.

---

### Post by psychicdragon on 2005-06-03
Thanks alot ow50, these packages worked great for me!
The gtk1 look is really hard the eyes.

---

### Post by Psquared on 2005-06-03
[QUOTE=ow50]Looking at the dependencies, they both seem to depend on the backported version of libgcc1. I hadn't noticed that. All other dependencies should be in normal hoary repositories.[/QUOTE]

No, it was something called libnoxpm. Anyway, I got it straightened out now.

Thanks for your work. This really looks and feels a lot better.

---

