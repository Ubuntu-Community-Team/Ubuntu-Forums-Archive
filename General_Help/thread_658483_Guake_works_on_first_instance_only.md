---
title: "Guake works on first instance only"
date: 2008-01-04
forum: General Help
---

### Post by usnmustanger on 2008-01-04
I recently installed **guake** via the deb package [available here ]("http://gnomefiles.org/app.php/Guake").  (I first tried compiling from source, but make failed with errors).  After running the necessary gconf command given in [this thread]("http://ubuntuforums.org/showthread.php?t=567604"), it works--sort of.
If fires up and opens once without problem.  However, after hiding (F12) and reopening (F12), the dropdown terminal is a solid blank gray panel.  No terminal.  Every invokation after this does the same thing.  Closing and restarting the app results in the one good (first) instance, followed by the gray panel.  See screenies below:

First Instance:
[[IMG]http://img442.imageshack.us/img442/9194/guakegoodok8.th.png[/IMG]](http://img442.imageshack.us/my.php?image=guakegoodok8.png)

Follow on invokations:
[[IMG]http://img247.imageshack.us/img247/2756/guakebadok6.th.png[/IMG]](http://img247.imageshack.us/my.php?image=guakebadok6.png)

FWIW, here's my system info:
Apple 20" iMac 2Ghz CoreDuo
ATI vid card using fglrx driver
Ubuntu Gutsy Gibbon (the deb is specified as a Feisty package on the website--could this be part of the problem?)
Gnome
Compiz effects fully enabled
XGL running (I think--I don't really know what this is).

Anyone else experiencing this?  Fixes?
Any other info I can provide to help you help me?

I love having a dropdown terminal, but Yakuake refuses to render its terminal (Konsole) transparent under Gnome, and tilda is way too broke--crashes immediately on launch.

TIA!

---

### Post by avatarms on 2008-01-06
I had the same problem and found the solution on a site:

> Guake is currently in Alpha State, and I found two small issues, which can be workarounded easily:

- before starting it, you need to logout, to make your gconf installation find guakes schemas file, else you'll get an error

- if it does not refresh, after the second pop-up, simply right-click on the tray-icon and click on the settings entry, then disable "Animate on show and hide", then exit and start guake again, it will now work as expected  

[Edit] Source: [http://www.nanolx.org](http://www.nanolx.org)

Hope it helped ^^

Bye

---

### Post by dlegend on 2008-01-06
> **avatarms said:**
> I had the same problem and found the solution on a site:



Is it possible to name the source or it goes against the forum policy?

Hope it helped ^^

Bye

Naming the source of your information is never against the rules of UF as I'm sure the UF community promotes the spread of information and give credit where it is due.  Especially if it is useful!

---

### Post by avatarms on 2008-01-07
> **dlegend said:**
> Naming the source of your information is never against the rules of UF as I'm sure the UF community promotes the spread of information and give credit where it is due.  Especially if it is useful!

Tnx ^^ I will now edit my post.

---

### Post by rfurman24 on 2008-01-30
Just wanted to say thanks for the post with the fix for the only working once. Yakuake has been flaky and I prefer not using Kapps.

---

### Post by Vorian on 2008-01-30
I have guake going through the REVU process right now, hopefully it can make the cutoff to be included in hardy.  

In the mean time, if you are running hardy, you can test guake from my ppa
[http://ppa.launchpad.net/vorian/ubuntu/pool/main/g/guake/](http://ppa.launchpad.net/vorian/ubuntu/pool/main/g/guake/)

---

