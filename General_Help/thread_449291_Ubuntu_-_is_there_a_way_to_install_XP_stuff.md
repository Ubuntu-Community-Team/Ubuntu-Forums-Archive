---
title: "Ubuntu - is there a way to install XP stuff"
date: 2007-05-20
forum: General Help
---

### Post by Cloudedbrains on 2007-05-20
Sorry another newbie question here :oops:

But is there away to install my XP (windows) only stuff under Ubuntu :-k

Like using an emulator or virtual machine or something #-o

It needs to be really simple to setup and step by step process as I am learning Ubuntu here
and so far its been a rough ride and I need something to go smoothly [-o<

---

### Post by Ub1476 on 2007-05-20
You can use Wine.. You find it in add/remove..:)

---

### Post by jamieplucinski on 2007-05-20
Wine, Cedega, CrossoverOffice. All just a tiny Google search away.

Wine is free, the rest are not.

---

### Post by jtraub on 2007-05-20
You may try to use Wine for small simple software.
If you want to use really big applications, it would be better to install these apps on virtual machine like qemu.

---

### Post by WakkiTabakki on 2007-05-20
Yup, it's called WINE, but bear in mind, it's far from perfect... Some programs work flawlessly and some won't run at all (esp. directX-proggies).

Install is the easiest part: Start 'Add/Remove...' from the menu 'Applications' and search for wine.
Check out [http://www.winehq.org/](http://www.winehq.org/) and their AppDB for tips and tricks on how to get applications running...

Good luck
/N

---

### Post by Cloudedbrains on 2007-05-20
Thanks everyone :)
Will checkout WINE today ;)

---

### Post by Syr0 on 2007-05-20
Just hit this in the terminal to install WINE: (since you're a Feisty Fawn User)

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get install wine

---

### Post by de_pol on 2007-05-20
some programs need special DLL files from the API of windows, which wine can't emulate.

If you have that problem, you can install Vmware, it wil emulate a new pc environment, and you can install xp on it. since i have vmware with xp on it, i was finally able to remove my dualboot, and still happy about it :)

---

### Post by Cloudedbrains on 2007-05-20
> **de_pol said:**
> If you have that problem, you can install Vmware, it wil emulate a new pc environment, and you can install xp on it. since i have vmware with xp on it, i was finally able to remove my dualboot, and still happy about it :)

That sounds better but how do I get it and install it ??
Is it easy to do ?? 
I have an XP Home cd to install windows !!

---

### Post by de_pol on 2007-05-20
you will have to look for a way to obtain vmware...

---

### Post by WakkiTabakki on 2007-05-22
> **de_pol said:**
> you will have to look for a way to obtain vmware...

It's available from 'Add/Remove...' under the Applications menu. Just search for 'VM'. You use VM server to create a new virtual machine with your XP-install CD:s and VMPlayer to run the virtual machine...

With WINE you are using Linux to "emulate" (yes, I know 'Wine Is Not An Emulator') windows, while VMWare runs the full windows install. 
It means that while WINE may not run all programs perfeclty, it doesn't require more than a few MB:s of space. Using VMWare you create and run a full windows install, i.e hogging up a few Gb of space, and hardware support is very limited (no 3D-accel etc). Although, it does look pretty cool running windows in a window in linux :P

/N

---

### Post by ArieT on 2007-05-22
> **de_pol said:**
> you will have to look for a way to obtain vmware...
Or install Virtualbox which is free (and partly open source).

---

### Post by MarshallClan on 2007-09-24
Greetings All...
 Definitely look into the Virtualbox route.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

 I found it easy to use after reading this How-To:

[http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/](http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/)

 I'm running Windows XP inside Feisty and it works Amazingly well depending on your needs (no 3d capable.)   
Best of Luck!
K-

---

### Post by kenchuamy@gmail.com on 2007-09-24
hi,
i just install the wine software at Ubuntu, is pretty simple, pls refer to user guide and opy and paste the command given.automatic install.

i still under testing period.....just refer to [www.winehq.org](www.winehq.org)

regard,

ken

---

