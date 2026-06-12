---
title: "Gnome2 Calculator?"
date: 2015-09-14
forum: General Help
---

### Post by pearj2 on 2015-09-14
gnome-calculator has changed since gnome3. I like the old gnome-calculator (gcalc / gcalctool?)... The Mate fork changed their calculator from gnome-calculator..

Does any one know if the old version is available somewhere? I've looked all over, and tried all the calculators in the repos...

I have my 10.04 install in another partition.. is it possible to use that (should be configured to use gnome2)?

---

### Post by iulian X on 2015-09-14
> **pearj2 said:**
> gnome-calculator has changed since gnome3. I like the old gnome-calculator (gcalc / gcalctool?)... The Mate fork changed their calculator from gnome-calculator..

Does any one know if the old version is available somewhere? I've looked all over, and tried all the calculators in the repos...

Do you miss the appearance or the function of the old gnome-calculator ?

[https://apps.ubuntu.com/cat/applications/natty/gcalctool/](https://apps.ubuntu.com/cat/applications/natty/gcalctool/)

You can install gnome-calculator in Ubuntu Mate.

---

### Post by pearj2 on 2015-09-14
Yep - it's now called "gnome-calculator" (think it used to be called gcalctool or similar).

"gnome-calculator" is the correct calculator, but it's using gnome3 and requests a different theme engine. I was wondering if anyone knew how to make it work for gnome2, or if theres a fork of this calculator for Mate (gnome2).

I'm using the Mate desktop (mate-desktop.org), but not Ubuntu-Mate.

---

I do have a 10.04 install, that has gcalc (now gnome-calculator). I was also wondering if I could migrate the app (executable script) to the 15.04 install - and how to make that work?

---

The Ubuntu Mate calculator is "galculator".

---

### Post by tgalati4 on 2015-09-15
I thought *mate-calc* was a simple fork of *gcalctool* or *gnome-calculator*.  If you are running MATE, what happens when you Alt-F2 and type in *mate-calc*?

> tgalati4@Mint17 ~ $ apt-cache depends mate-calc
mate-calc
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpango-1.0-0
  Depends: libxml2
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: mate-calc-common
  Recommends: mate-icon-theme
  Conflicts: mate-calc:i386


---

### Post by Yellow Pasque on 2015-09-15
> **tgalati4 said:**
> If you are running MATE, what happens when you Alt-F2 and type in *mate-calc*?

Ubuntu MATE doesn't have mate-calc. It has galculator, because that's what MATE is moving to:
[http://mate-desktop.org/blog/2014-03-17-galculator-is-coming-to-mate/](http://mate-desktop.org/blog/2014-03-17-galculator-is-coming-to-mate/)

So, I would suggest trying galculator from the repository. It has a more traditional feel, though it's built with gtk3.

Optionally, you could build it with gtk2 if you absolutely must have gtk2. Something like this should do it:
```
sudo apt-get install libxml-parser-perl libgtk2.0-dev intltool build-essential
wget http://galculator.mnim.org/downloads/galculator-2.1.4.tar.bz2
tar xjf galculator-2.1.4.tar.bz2
cd galculator-2.1.4/
./configure --disable-gtk3
make
sudo make install
```

---

### Post by pearj2 on 2015-09-15
Galculator will work - it has an algebraic function that shows a string, which is what I miss about the old calculator - so I'll just use that.

Thanks folks!

---

