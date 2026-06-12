---
title: "why can no-one solve this!"
date: 2008-04-29
forum: General Help
---

### Post by alexi66 on 2008-04-29
everytime i download a file it goes into a download folder i set up and then ill copy and paste it into the folder it should be in, i.e. music, videos etc

but when i have an ogg or an mp3 file in the folder as soon as i load up the download folder it freezes and the screen turns grey and i cant copy and paste them or even scroll my mouse over them

does anyone have the solution to this?

xx

---

### Post by seamuso on 2008-04-29
> **alexi66 said:**
> everytime i download a file it goes into a download folder i set up and then ill copy and paste it into the folder it should be in, i.e. music, videos etc

but when i have an ogg or an mp3 file in the folder as soon as i load up the download folder it freezes and the screen turns grey and i cant copy and paste them or even scroll my mouse over them

does anyone have the solution to this?

xx

Do you have Compiz enabled? If so, try disabling that and see if the problem goes away.

---

### Post by alexi66 on 2008-04-29
ok I'll try that
but do you know if there is a way to do it without permanently disabling compiz (should that be the problem)?

because obviously its gonna be a bit of a pain to have to keep disabling compiz every time i want to copy and paste a file

xx

---

### Post by olskar on 2008-04-29
It is easy to permanently disable compiz, just choose no desktopeffects in the apperancedialog you find in settings

---

### Post by alexi66 on 2008-04-29
i dont want to disable it permanently
just so i can see if it is the problem

is there a command i could use in the terminal to disable it
cause I've tried 'killall' ccsm, compiz, compiz-fusion, and pretty much every other command i could think of?

---

### Post by Zorael on 2008-04-29
```
$ metacity --replace &
```
Or 'kwin --replace &' for KDE.

---

### Post by alexi66 on 2008-04-29
it turned it off but it didn't solve the freezing folder problem

btw how do i turn it back on
my computer feels naked with out it :P

x

---

### Post by olskar on 2008-04-29
Oh misunderstood you :) turn on with "compiz --replace"

---

### Post by alexi66 on 2008-04-29
yeah that did it
cheers :)

so you don't know about the problem where the home folder freezes?

x

---

### Post by yaknowwat on 2008-04-29
What OS version do you have and what are your system specifications?

It sounds to me like something went wrong on install and was corrupted.
(Happens if connection when downloading goes jumpy or there is some small scratches on the install CD.)

---

### Post by alexi66 on 2008-04-29
I'm using ubuntu 7.10
1gb RAM
Dual Core AMD Turion 64 X2 Mobile Technology TL-52 1.6GHz
nVidia graphics card

but I'm going to upgrade to 8.04 as soon as I can

x

---

### Post by yaknowwat on 2008-04-29
Your hardware seems to be alright.

It sounds more and more like a corrupted file. (Causes are normally corrupted install/update file something that can happen to any OS just one of those almost unpredictable things).

Upgrading to 8.04 should solve the problem.

Possibly a Reinstall of Nautilus would solve the problem maybe (if its nautilus that is corrupted) but, theres no tell what is so it'd be better just to upgrade to 8.04.

---

### Post by alexi66 on 2008-04-29
its ok, I've sorted it now
i just downloaded thunar and used it instead of nautilus 
i turned out that is what was solving the problem

thanks for everyone's help :)

xx

---

