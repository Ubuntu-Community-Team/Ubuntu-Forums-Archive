---
title: "Firefox hides text on some websites when antialiassing is disabled"
date: 2007-06-07
forum: General Help
---

### Post by Bazz0847 on 2007-06-07
Hi,

I've been using Ubuntu 7.04 for a while now, works perfectly but for one thing: the blurry fonts where driving me crazy. So I disabled anti-alisassing in /etc/fonts/fonts.conf for all fonts and set the microsoft TT-fonts as default, using a script from this forum. Works perfectly in all applications (Konqueror, Nautilus, OpenOffice, the lot), but unfortunately it doesn't work without issues in FireFox. On some websites, only the first word on a row is displayed, and I need to select using the mouse to see the whole text. When I re-enable anti-aliassing, the problem is gone, but the text is blurry again...

So when you

	<edit mode="assign" name="antialias" >
		<bool>true</bool>
	</edit>

replace with

	<edit mode="assign" name="antialias" >
		<bool>false</bool>
	</edit>

it will cause problems... On both my PC's running Ubuntu 7.04...

Does anyone know how to fix it? I've been trying for hours now :(

Edit: used this tutorial [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by cojoco on 2007-06-07
No help from me, except a "Me Too!", as I have this problem too ...

---

### Post by Bazz0847 on 2007-06-07
well, it's promising to hear that more people suffer from this problem. Don't know if it's allowed, but the only example I can give at this moment is the following (commercial...) website:
[www.schoolinventaris.nl](www.schoolinventaris.nl) (not my site, btw)

If you apply the patch described above and then browse to this website, you only see the first words of the sentences in the blue part. When you select it sometimes shows the whole text. :?

There are more websites however, but these are private and can not be accessed without credentials :)

---

### Post by Bazz0847 on 2007-06-07
Just discovered; the problem is gone when I enable Desktop Effects... :?
When I disable it again, problem stays solved, but upon de first reboot it's there again!

---

### Post by Bazz0847 on 2007-06-08
anybody? :(

---

