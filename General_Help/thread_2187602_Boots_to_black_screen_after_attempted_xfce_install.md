---
title: "Boots to black screen after attempted xfce install"
date: 2013-11-12
forum: General Help
---

### Post by Joe_Nat on 2013-11-12
Alright so I was using Lubuntu 13.10 on a old machine and I was getting tired of having no graphical effects at all so I tried installing XFCE .I did the apt-get-install command and i logged out and it just gave me a black screen. I tried to do ctrl-alt-f1 to get a command prompt but nothing happened. I rebooted and the same thing happened, it totally frozen. But whats interesting is that if press the power button once it quickly switches off.  I have about 20gb worth of stuff I want to keep on the os partition. 

Pentium 4 (cant look up ghz right now)
Geforce fx 5600, proprietary drivers
1gb ram
hand-built, 2006 (?)

Obviously help would be appreciated. Thanks.

---

### Post by ibjsb4 on 2013-11-13
> **Joe_Nat said:**
> I tried installing XFCE .I did the apt-get-install command.

You didn't post the command.  Was it:
```

sudo apt-get install xfce4
```

---

### Post by Joe_Nat on 2013-11-13
Yes. It ran with no errors.

---

### Post by ibjsb4 on 2013-11-14
Usually adding a desktop is not a problem.

Since you cannot get to grub or console you can use the Live CD to access and move your files.  Use the option on the CD to try Ubuntu.  Then use Nautilus to mount your HDD.

Maybe someone running xfce will come along with some ideas.  I have nothing else at the moment.

Edit:  You do not have Nautilus installed and I do not know if your file manager will mount a HDD.

Edit2:  Ok, found it.

[http://www.lubuntu.net/blog/lubuntu-screencasts-diskutility](http://www.lubuntu.net/blog/lubuntu-screencasts-diskutility)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mount+partition+lubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mount+partition+lubuntu&sa=Search&cof=FORID:9)

---

