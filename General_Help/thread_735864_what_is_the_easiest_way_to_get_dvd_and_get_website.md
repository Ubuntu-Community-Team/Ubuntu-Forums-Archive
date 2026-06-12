---
title: "what is the easiest way to get dvd and get websites to play enet movies"
date: 2008-03-26
forum: General Help
---

### Post by timetoballj on 2008-03-26
i am new to gusty and i have tried to get dvds to play but everytime i try to get libdvdcss2 i get error and how do i get movies to play off the net

---

### Post by kesman on 2008-03-26
you could try installing a package called ubuntu-restricted-extras and mozilla-mplayer to get your movies to work.

---

### Post by timetoballj on 2008-03-26
it did not work my dvds still want play is there an program with the pulgins that i can use to get my dvds to play i get error after error or not right pulgins everytime

---

### Post by Oldsoldier2003 on 2008-03-26
> **timetoballj said:**
> it did not work my dvds still want play is there an program with the pulgins that i can use to get my dvds to play i get error after error or not right pulgins everytime

```
sudo apt-get install vlc
```

---

### Post by timetoballj on 2008-03-26
i also cant add or remove apt its says run dpkg config --a how do i get that working so i can add or remove apts

---

### Post by timetoballj on 2008-03-26
and when i try to run sudo apt-get install vlc it said invaild op. install

---

### Post by shadyedsan on 2008-03-26
for the problem of getting dvd's to work:

you could try installing automatix2 which includes the w32 codecs at [www.getautomatix.com](www.getautomatix.com)

then go down to easy direct installation and select your version of ubuntu (i.e. fiesty or gutsy amd64 or just the standard ones) and click the link to download and open it with the default package installer and it installs it for you, no compiling.

did you try sudo dpkg --configure -a ?

as for the apt problem, try opening a terminal and typing update-manager, it's possible apt mat be broken so any updates might fix it

also, if apt is indeed broken, you could try using synaptic to see if this is the case, Main menu --> System --> Administration --> Synaptic Package Manager. If apt is broken then synaptic will not install selected packages as this uses apt

hope this helps

---

