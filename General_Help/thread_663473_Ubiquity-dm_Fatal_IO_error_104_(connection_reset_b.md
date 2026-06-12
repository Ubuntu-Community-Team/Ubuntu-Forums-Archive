---
title: "Ubiquity-dm Fatal IO error 104 (connection reset by peer) on X server..."
date: 2008-01-10
forum: General Help
---

### Post by flyingmekk on 2008-01-10
Hi everybody,

I'm trying to install Ubuntu 7.10 using Wubi on a computer with windows vista as follow...

1) I've downloaded the Wubi exe and put in the same directory the ubuntu 7.10 iso file.
2) I've launche the wubi exe and filled all the required fields, everything went smooth and then I rebooted.
3) I've choosed Ubuntu as OS and the pc starts to load it... but... it stops telling me that it has to start in safe graphic mode and to choose manually the correct display and resolution.
4) I've tryed several configuration but nothing changed, ubuntu continues to displays all the application it is starting untill it arrives to "starting ubiquity" and, at this point, it fails showing the message:

**Ubiquity-dm Fatal IO error 104 (connection reset by peer) on X server :0.0.**](*,)

5) It continue to load the GNOME and then it definetively stops.:confused:

If I use the same ISO to make the live CD, ubuntu 7.10  works perfectly

What's wrong?

Thanks in advance!

---

### Post by ago on 2008-01-10
At the countdown press esc, then select the safe graphic mode

---

### Post by flyingmekk on 2008-01-10
> **ago said:**
> At the countdown press esc, then select the safe graphic mode

Already done, but the result is always the same...

"Ubiquity-dm Fatal IO error 104 (connection reset by peer) on X server..."

I've also tryed to reconfigure the graphic using

sudo dpkg-reconfigure xserver-xorg

but the problem is that is not recognised as a command...

---

### Post by ago on 2008-01-10
You should be able to run the command in a terminal, looks like the X server crashes
What do you mean by "not recognised as a command"?

---

### Post by flyingmekk on 2008-01-10
I mean that I'm not in the terminal... I can write the command line, but when I press "enter" I just go down one line on the screen and stop!

---

### Post by ago on 2008-01-10
ctrl + alt + f1

---

### Post by flyingmekk on 2008-01-11
Thank You, I'll try it asap!

---

