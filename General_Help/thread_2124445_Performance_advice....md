---
title: "Performance advice..."
date: 2013-03-11
forum: General Help
---

### Post by StandartBoros on 2013-03-11
Hi, my pc is 1GB RAM, 1.8GHz processor,can you give me some tweak advices, because ubuntu runs a little slow(v.12.04)...

---

### Post by carl4926 on 2013-03-11
Use xubuntu or lubuntu

---

### Post by p_code on 2013-03-11
In general, with 1GB RAM and a 1.8GHz CPU, you should be seeing fairly good performance, so if you can give just a little more info about your configuration, and what you are trying to do when you notice the slowness, you might find you can get better advice.

For example did you install with full encryption, or home folder encryption, or perhaps both?  -that will slow things down a bit (especially if you use both at the same time, because Ubuntu will double encrypt swap, which is slower than molasses) 

Are you trying to run from a live DVD? -unfortunately, that will ALWAYS run slowly, because unlike some other distros, Ubuntu isn't really optimized for full time live DVD use.

Do you see why I asked for more specifics?  - without more info to go on, all we can do is guess.

---

### Post by jsabina1 on 2013-03-11
Hi,
I have 2Gb of ram but it was quite slow.
I've installed lubuntu and it's a new life!
Much faster!
And using chromium instead of firefox, I am sorry, but it goes faster :S

---

### Post by carl4926 on 2013-03-11
> **jsabina1 said:**
> Hi,

And using chromium instead of firefox, I am sorry, but it goes faster :S

True
It is

---

### Post by sudodus on 2013-03-11
> **carl4926 said:**
> Use xubuntu or lubuntu

+1

These flavours of Ubuntu have desktop environments with much lighter foot-print than standard Ubuntu, and they will run well on the hardware you describe.

---

### Post by StandartBoros on 2013-03-11
Probably I should install lubuntu,althogh it's not so bad when using GNOME (without effects)...How do I install lubuntu over ubuntu?And can I change it back if i like..?

---

### Post by sudodus on 2013-03-11
> **StandartBoros said:**
> Probably I should install lubuntu,althogh it's not so bad when using GNOME (without effects)...How do I install lubuntu over ubuntu?And can I change it back if i like..?

Either a fresh install from the Lubuntu iso file or by installing Lubuntu-desktop, that you can select at the log in screen (click on the round button near the login window according to the attached file).

```
sudo apt-get install lubuntu-desktop
```

---

### Post by jsabina1 on 2013-03-11
> **sudodus said:**
> Either a fresh install from the Lubuntu iso file or by installing Lubuntu-desktop, that you can select at the log in screen (click on the round button near the login window according to the attached file).

```
sudo apt-get install lubuntu-desktop
```

Yep I've used this code..
And as I am ... newbie.. I couldn't see it and I was getting mad :D
Then I discovered that in the login page you can choose in which enviroment you want to login.
So I think you can login back to GNOME if you don't like it.

But it's so much faster that now really I am only using lubuntu and I like it a lot!

---

### Post by sudodus on 2013-03-11
You are welcome to Lubuntu :-)

---

### Post by p_code on 2013-03-11
> **jsabina1 said:**
> Yep I've used this code..
And as I am ... newbie.. I couldn't see it and I was getting mad :D
Then I discovered that in the login page you can choose in which enviroment you want to login.
So I think you can login back to GNOME if you don't like it.

But it's so much faster that now really I am only using lubuntu and I like it a lot!

Acutally, if you installed over the base Ubuntu, you technically aren't actually running Lubuntu, which is a whole separated Ubuntu distro based on LXDX, what you are running is LXDE overlaid on top of the standard Unity version of Ubuntu.

I mention this, not to be overly technical, but just so if you ever need more help, you know exactly what you have :KS

LXDE does work very nicely - you don't get quite the level of desktop integration and goodies as you have available in Gnome Classic (which is why it's nice to have access to both) but LXDE is catching up fast on features, and it's definitely quite a bit faster.

---

### Post by jsabina1 on 2013-03-12
> **p_code said:**
> Acutally, if you installed over the base Ubuntu, you technically aren't actually running Lubuntu, which is a whole separated Ubuntu distro based on LXDX, what you are running is LXDE overlaid on top of the standard Unity version of Ubuntu.

I mention this, not to be overly technical, but just so if you ever need more help, you know exactly what you have :KS

LXDE does work very nicely - you don't get quite the level of desktop integration and goodies as you have available in Gnome Classic (which is why it's nice to have access to both) but LXDE is catching up fast on features, and it's definitely quite a bit faster.

Thanks a lot..
So I could have better performance reinstalling everything only using lubuntu?

---

### Post by carl4926 on 2013-03-12
> **jsabina1 said:**
> Thanks a lot..
So I could have better performance reinstalling everything only using lubuntu?

Technically it shouldn't be necessary to do a clean install, but in practice it does seem to work that way.

---

### Post by 3rdalbum on 2013-03-12
> **jsabina1 said:**
> Thanks a lot..
So I could have better performance reinstalling everything only using lubuntu?

I don't think so. Lubuntu is Ubuntu, but with LXDE instead of Unity. If you have both desktops installed but only use LXDE your computer will be running the exact same code as Lubuntu.

---

### Post by jsabina1 on 2013-03-12
> **3rdalbum said:**
> I don't think so. Lubuntu is Ubuntu, but with LXDE instead of Unity. If you have both desktops installed but only use LXDE your computer will be running the exact same code as Lubuntu.

ok so it's not true that

[COLOR=#000000][I]"what you are running is LXDE overlaid on top of the standard Unity version of Ubuntu"


I am only trying to undertand what is the best thing to do, thanks![/I][/COLOR]

---

