---
title: "Possible to install LMMS without Wine?"
date: 2013-05-09
forum: General Help
---

### Post by ztealmax on 2013-05-09
Hello all is it possible to install LMMS without Wine? i really dont want wine installed and im not using plugins VST thats for windows anyways

Could someone help me how to accomplish this really dont want wine installed, i tried installing LMMS then doing command sudo apt-get purge wine1.4* but it ofc also uninstall lmms


Looking forward to some genius way to get help ;)

Sincerally
Martin

---

### Post by dino99 on 2013-05-09
lmms is an ubuntu package, so install it as any other one  :confused:

sudo apt-get install lmms

---

### Post by ztealmax on 2013-05-09
dino99: yes thanx, but what i was asking was something else ;) iknow how to install, what i dont know is how to not install it without Wine1.4 (Windows emulator thingy)

---

### Post by monkeybrain2012 on 2013-05-09
Apparently Wine is required as a dependency for LMMS because of VSTs.  [http://lmms.sourceforge.net/wiki/index.php/0.4:Working_with_VSTs](http://lmms.sourceforge.net/wiki/index.php/0.4:Working_with_VSTs)

I don't know if you can install LmMS without those plugins. I don't know anything about music. :)

---

### Post by Hylas de Niall on 2013-05-09
I've installed LMMS on a number of different distributions and i don't ever recall it needing or calling in Wine? Is this a new thing?

---

### Post by ztealmax on 2013-05-09
yea its anoying as hell, it should be ([ x ] Do you want to install Wine1.4 for VST support Y/N) Not a forced install :(

---

### Post by CraigPid on 2013-05-09
I would imagine that if you built it from source you could build it without vst support.

---

### Post by ztealmax on 2013-05-09
Yea, trouble is im not good at building from source ;)

---

### Post by ztealmax on 2013-05-10
just wish i could recompile this LMMS without Wine

---

### Post by CraigPid on 2013-05-17
[http://lmms.sourceforge.net/wiki/index.php/Compiling_LMMS](http://lmms.sourceforge.net/wiki/index.php/Compiling_LMMS)

There's a fairly straightforward walkthrough. Just read it carefully.
Make sure you install git & cmake with the software centre or aptget if you don't already have.
Clone the git repository like it shows in the tutorial & then skip ahead to resolving unmet dependencies.
Under optional libraries it shows Wine. If you don't install it the compilation will just make it without Wine.
So after you resolve depencies go back to where you skipped ahead and follow the steps.
I haven't done this but it looks pretty straightforward. Don't be intimidated.Just follw the steps & when you're done you'll have learned something & have more confidence in stuff like this.
   Craig

---

