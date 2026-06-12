---
title: "Wine Help"
date: 2008-02-14
forum: General Help
---

### Post by jsnelli2 on 2008-02-14
I installed wine via add/remove programs and had no luck getting the program to run so I removed it and installed it via apt-get in the terminal.  I still am unable to get the program to run whenever I click on ANY of the icons for it-i.e. configure, uninstall, browse, or even notepad.  I have previously used it (before reformatting) and I don't remember having a problem getting it to start.  What am I not doing?

---

### Post by taurus on 2008-02-14
Open a terminal and configure it first with

```
winecfg
```

---

### Post by stevejesus on 2008-02-14
Yes Taurus.
Jsnelli2; it is important that you know that using synaptic and using "apt-get" are the same thing.

---

### Post by jsnelli2 on 2008-02-14
OK thanks- Yeah I just tried running it in terminal and got it going.  Thanks, I didn't realize that add/remove and apt-get were the same process.

---

### Post by UK-Wobbie on 2008-02-14
> **jsnelli2 said:**
> I installed wine via add/remove programs and had no luck getting the program to run so I removed it and installed it via apt-get in the terminal.  I still am unable to get the program to run whenever I click on ANY of the icons for it-i.e. configure, uninstall, browse, or even notepad.  I have previously used it (before reformatting) and I don't remember having a problem getting it to start.  What am I not doing?

You do know, When you install wine.
All you need to do is right click on windows file and go to run with windows wine emulator, And it will run!

---

### Post by jsnelli2 on 2008-02-14
Yeah, I just couldn't get anything to go before I ran the config file

---

### Post by jsnelli2 on 2008-02-15
Is there a way to up the physical memory that wine uses?  I am trying to install Phantasmagoria 2 and it is claiming I only have 7000 kb of physical memory and 11000 is necessary. It won't install

---

### Post by Tatty on 2008-02-15
You will need to put more RAM into your computer.

---

### Post by jsnelli2 on 2008-02-15
I have 1 GB and a 3GB swap...that's not sufficient to run 11MB through wine?!

---

### Post by Tatty on 2008-02-15
> **jsnelli2 said:**
> I have 1 GB and a 3GB swap...that's not sufficient to run 11MB through wine?!

Aha, yeah that doesnt sound right at all...  Afraid i dont have a clue:confused: sorry

---

### Post by jsnelli2 on 2008-02-15
That's ok- thanks for the reply though.  I'm trying to install it through dosbox now, using a patch for dos but I'm not having any better luck there. I'm at a loss

---

### Post by jsnelli2 on 2008-02-15
I got it going....Finally got it to ignore the "lack of" system requirements and got it installed through Wine and then patched it through dosbox.  Thanks all for the help

---

