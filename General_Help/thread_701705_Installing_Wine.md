---
title: "Installing Wine"
date: 2008-02-19
forum: General Help
---

### Post by Tony_photoplus on 2008-02-19
I am totally confused.  I have downloaded Wine (I hope the correct one) and read the info on how to install.  I found 'Terminal', so I opened it up and it stated to copy and paste into the terminal window.  I have done this:

tony@Tony-Desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

Do I save this window under the label 'Wine'?

Do I then go to Systems > Administration > Software Sources? 
Do I find APT there?  And I know I paste somewhere:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

Sorry have only just loaded Ubuntu on and I am completely lost here.  I know where to go as far as WinXP is concerened, but here totaly lost.  Hop you can help me.

Tony-photoplus

---

### Post by seventhc on 2008-02-19
to install wine just open a terminal and paste this in
```

sudo aptitude install wine

```
after you put this in the terminal just press <enter> on the keyboard :)

---

### Post by Dr. Octagon on 2008-02-19
Seventhc's got it

---

### Post by seventhc on 2008-02-19
One note in case you haven't done this yet. You will be asked for a password, when you type it in, you won't see anything, don't worry, just type it anyway and press <enter> again, then it will install. :)

---

### Post by dbqp on 2008-02-19
Also, make sure you have enabled all repositories (univers, multiverse...)

---

### Post by Tony_photoplus on 2008-02-19
Thanks for the info now downloaded.  I shall try next to load CS2 and all the software, thats the next challenge.  Do I save the terminal window I have used?

---

### Post by seventhc on 2008-02-19
> Do I save the terminal window I have used?
No, you can just close the terminal.

---

