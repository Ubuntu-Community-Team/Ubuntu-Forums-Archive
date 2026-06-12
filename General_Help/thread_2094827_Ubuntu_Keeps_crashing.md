---
title: "Ubuntu Keeps crashing"
date: 2012-12-14
forum: General Help
---

### Post by KristySEK on 2012-12-14
Okay for the last month or so my Ubuntu keeps crashing. It freezes first then a window pops up and says Ubuntu is not working properly and when I click details it shows nothing. Then a black screen and green letters and number pop up and I have to turn off my laptop (samsung). anyone experience this before and know what to do. FYI I have used Ubuntu for over a year so i am still fairly new with command prompts and what not

---

### Post by ibjsb4 on 2012-12-14
Overheating?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=monitor+temperatures&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=monitor+temperatures&as_qdr=all&sa=Google+Search&lang=en)

HDD going bad?

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

---

### Post by KristySEK on 2012-12-14
> **ibjsb4 said:**
> Overheating?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=monitor+temperatures&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=monitor+temperatures&as_qdr=all&sa=Google+Search&lang=en)

HDD going bad?

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

its an amd so it does it get hot sometimes.I have only had this laptop for about 8 months its in fantastic condition

---

### Post by QIII on 2012-12-14
AMD graphics?  Hybrid Intel/AMD graphics?  

Heat issues are common in laptops with AMD graphics when using the open source Radeon driver without Jupiter.

Hybrid Intel/AMD graphics can be a can of worms.

Pure AMD graphics setups run much cooler with the proprietary driver with laptops.

---

### Post by ibjsb4 on 2012-12-14
A runaway process eating up %CPU and/or %MEM?

In terminal:

```
top
```

---

