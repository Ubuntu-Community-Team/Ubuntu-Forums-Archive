---
title: "I Can't Install external apps from the Ubuntu Software App."
date: 2017-08-07
forum: General Help
---

### Post by andrewmalandrew on 2017-08-07
I was going to install unity3d on ubuntu and when i opened the .deb file it opens the Ubuntu Software app, thats normal for now, but when i click "install" nothing seems to happen, thats the same to the rest of external apps, Im using ubuntu 17.04
    ¿can you help me?, i really need to install it.

    *edit* =well, the install button works but, it just goes to 9% and stops itself.


    Sorry for bad english, im Colombian (we talk spanish, but i understand english.)

    **PC Specs**[B] (Laptop) :
    [/B]Pentium(R) Dual-Core CPU T4400 @ 2.20GHz × 2 **Proccesor**
    Mobile Intel® GM45 Express Chipset **Graphics**
    1,8 GiB **Memory**
    245,1 GB **DIsk Space**
    64 Bit OS **OS**

---

### Post by andrewmalandrew on 2017-08-07
also Installing apps from inside the app***(i mean,installing like Pencil2D inside the store.)*** works perfectly fine.

---

### Post by vocx on 2017-08-07
> **andrewmalandrew said:**
> i was going to install unity3d on ubuntu and when i opened the .deb file it opens the Ubuntu Software app, thats normal for now, but when i click "install" nothing seems to happen, thats the same to the rest of external apps
***¿can you help me?, i really need to install it.***
Why do you need to install that package?

Usually in Ubuntu you use the Software Center to install applications. If you use the terminal you use the "apt" command.
```

sudo apt install [package_name]

```

If you want to install a Debian package that is not in a repository and that you downloaded from some place else, then you use "dpkg".
```

sudo dpkg -i filename.deb

```

Please don't go installing Debian packages that you don't know what they do, or where they come from.

If your ultimate objective is to get something running, it's better if you explain with detail what it is, and then somebody here may be able to give you better advice.

Unity can be installed by simply using
```
sudo apt install unity
```

---

### Post by QIII on 2017-08-07
@andrewmalandrew:

Please use the default font and weight unless it is important to draw attention to a particular word or phrase.

---

### Post by andrewmalandrew on 2017-08-07
Thanks!!!

---

