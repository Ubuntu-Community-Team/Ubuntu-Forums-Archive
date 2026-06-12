---
title: "term font support on ubuntu 18"
date: 2020-07-02
forum: General Help
---

### Post by usrforum on 2020-07-02
Hi,

i've installed some of my favourite OLD terminal fonts on ubuntu 18.00 chosen since they appear
the best for writing code using emacs. Yep. I'm that old and I don't need tripped up by fancy
auto-completing auto-help auto-correcting auto-everything auto-nuisance stuff.
I know what I'm doing when writing code and I generally can do that much faster with emacs 
in a terminal window.

having said all that I downloaded the fonts followed some instructions elsewhere which amounted to

```

$sudo ln -s /etc/fonts/conf.avail/70-force-bitmaps.conf /etc/fonts/conf.d/
$sudo unlink /etc/fonts/conf.d/70-no-bitmaps.conf # For disabling no-bitmap setting

#I can see the fonts when I type 

$xlsfonts | grep whatever

#i cannot see the fonts when i type

$fc-list

#which seems to be the list $gnome-terminal works from

```

i then wanted to quickly try xterm but got a load of grief trying to install that from the package manager - I dont
want to change any of the stuff below because I spent a lot of time getting those packages where I wanted them

```

$sudo apt install xterm

Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 ffmpeg : Depends: libavcodec58 (= 7:4.1.4-1~deb10u1)
          Depends: libavdevice58 (= 7:4.1.4-1~deb10u1) but it is not going to be installed
          Depends: libavfilter7 (= 7:4.1.4-1~deb10u1)
          Depends: libavformat58 (= 7:4.1.4-1~deb10u1) but 7:4.0.4-0ubuntu1 is to be installed
          Depends: libavresample4 (= 7:4.1.4-1~deb10u1) but it is not going to be installed
          Depends: libavutil56 (= 7:4.1.4-1~deb10u1) but 7:4.0.4-0ubuntu1 is to be installed
          Depends: libpostproc55 (= 7:4.1.4-1~deb10u1) but 7:4.0.4-0ubuntu1 is to be installed
          Depends: libsdl2-2.0-0 (>= 2.0.9) but 2.0.8+dfsg1-4ubuntu1 is to be installed
          Depends: libswresample3 (= 7:4.1.4-1~deb10u1) but 7:4.0.4-0ubuntu1 is to be installed
          Depends: libswscale5 (= 7:4.1.4-1~deb10u1) but 7:4.0.4-0ubuntu1 is to be installed
 xterm : Depends: libutempter0 (>= 1.1.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

any solutions? any ideas? If this is not possible would anyone be up for getting some decent 'old' fonts
ported over? any suggestions welcome.

I particularly liked the old Sony fonts and the old Sun Microsystems fonts fwiw.

and if anyone wants to see what the best programmer's keyboard ever made was imho take a look at 
the old Sun Workstation keyboards.

---

### Post by Holger_Gehrke on 2020-07-02
You might want to rebuild the fontconfig-cache(s) using fc-cache, probably with the options '-s' and '-v' (system directories only, verbose). So a 'sudo fc-cache -sv' should get 'fc-list' to show the newly installed fonts.

Holger

---

### Post by usrforum on 2020-07-03
Thanks that worked,

---

