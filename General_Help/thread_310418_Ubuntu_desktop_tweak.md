---
title: "Ubuntu desktop tweak?"
date: 2006-12-01
forum: General Help
---

### Post by k3rmit on 2006-12-01
First of all, as it is my first post I wanted to say hi to everybody :)

I started using ubuntu some time ago. Mostly as a desktop OS (+apache with mysql). What I don't like and keeps me to Windows is that Ubuntu is noticeably slower. I mean such things as starting programs switching between them or even Opera tabs switching etc takes much longer that WinXP.

On the other hand - Windows runs smoothly.

I think that the performance whould improve if I turned some (server-like) services off.

Can anybody help me optimizing my Ubuntu?
Please note that I can use apt-get, but when it comes to manual configuration I'm not very advanced ;)

Any help appreciated :)

---

### Post by xabbott on 2006-12-01
[http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)

---

### Post by frodon on 2006-12-01
Tell us what hardware you use and what drivers you installed first..

---

### Post by k3rmit on 2006-12-01
The hardware is Athlon XP@2.0G 512mb of ram
I use geforce2 at the moment - I haven't installed any 3rd party drivers.
I installed ati drivers (for radeon 9800) before though.

---

### Post by frodon on 2006-12-01
> **k3rmit said:**
> I use geforce2 at the moment - I haven't installed any 3rd party drivers..duh, first thing to do it will really improve performances.
All you need to now about nvidia drivers installation is there (i advice you the method 1 if you don't want to bother to much with driver installation) : 
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

If you installed the 32 bit version of ubuntu then install the k7 kernel and boot the generic kernel rather than the i686 : ```
sudo apt-get install linux-k7
```

---

