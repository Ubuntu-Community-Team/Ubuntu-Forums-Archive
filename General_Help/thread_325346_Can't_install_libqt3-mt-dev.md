---
title: "Can't install libqt3-mt-dev"
date: 2006-12-25
forum: General Help
---

### Post by Starlight on 2006-12-25
Hello, I have a big problem... I need to compile one thing, but for that I need libqt3-mt-dev. When I try to install it, I get a weird error... here it is:

> The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libgl1-mesa-dev but it is not going to be installed or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

so I try to install libgl1-mesa-dev, and I get this:

> The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages

and so I have no idea what to do... can anyone help me?

---

### Post by jlintz on 2006-12-25
same problem here.  anyone know anything about this?

---

### Post by darenw on 2006-12-25
hunch - try removing mesa entirely, install the qt dev stuff, and then reinstall mesa.  i just installed the same qt stuff y'day for something, but don't have mesa at all on my machine.

---

### Post by darenw on 2006-12-25
and i'm wondering why, for you,  Qt dev stuff thinks it needs mesa....does it really?

---

### Post by jlintz on 2006-12-25
i had this problem when trying to install beryl-dev.  I just finally fixed it by removing mesa-common-dev and now it seems to work fine and install the correct version

---

### Post by Starlight on 2006-12-25
ok... I did that, and it still complained about libglu1-mesa... so I tried to remove it too, but then it started removing my whole system! Fortunately I did Ctrl-C before it removed anything except Adept and a few other small things, which I just reinstalled... then I tried to remove libglu1-mesa again, but I've noticed that the package manager said that after removing it 532 MB of disk space will be freed... so it would probably start removing my system again... does it mean that there's no way to install libqt3-mt-dev on my system? If yes, then can someone compile this: [http://www.kde-apps.org/content/show.php?content=49484](http://www.kde-apps.org/content/show.php?content=49484) and put it somewhere that I can download it? There's already a compiled one somewhere, but it crashes everytime I try to start it...

---

### Post by Starlight on 2006-12-26
bumping this thread...

---

### Post by Perfect Storm on 2006-12-26
Do you have any unofficial source in your repo? It's seen before that mixing diffrent sources courses broken packages.

---

### Post by Starlight on 2006-12-26
yes... I have sources for Beryl and for Wine... and that's all.

---

### Post by Perfect Storm on 2006-12-26
Try download the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) both the regular and the -dev and install it that way.

---

### Post by Starlight on 2006-12-27
It worked! Thanks! :)

---

