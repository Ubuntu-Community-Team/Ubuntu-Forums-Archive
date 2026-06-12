---
title: "How to install Linux Beryl"
date: 2007-09-18
forum: General Help
---

### Post by noobie_atlinux on 2007-09-18
Ok I just downloaded Linux Beryl application from my WinXP OS, I have it saved onto cd. Now the Question is, with the Files inside the Linux Beryl folder, when I opened it, how do I install the application onto my Linux Ubuntu:confused:

---

### Post by por100pre1 on 2007-09-19
Which Beryl application? Can't you do this from Ubuntu?

```
sudo aptitude install beryl-manager emerald emerald-themes
```

---

### Post by drlouis on 2007-09-19
> **noobie_atlinux said:**
> Ok I just downloaded Linux Beryl application from my WinXP OS, I have it saved onto cd. Now the Question is, with the Files inside the Linux Beryl folder, when I opened it, how do I install the application onto my Linux Ubuntu:confused:
I'm not sure what you're trying to do  with Windows.  Personally, I installed Beryl via Synaptic.  worked great.

---

### Post by lenswipe on 2007-12-08
> **drlouis said:**
> I'm not sure what you're trying to do  with Windows.  Personally, I installed Beryl via Synaptic.  worked great.

hmm thats interesting

my freind has Ubuntu 7 on his laptop but beryl doesnt apear in synaptec. I also im currently installing Ubuntu so im not sure wether or not it will apear in synaptec ther either...


What ubuntu version are you using?

---

### Post by lenswipe on 2007-12-08
> **noobie_atlinux said:**
> Ok I just downloaded Linux Beryl application from my WinXP OS, I have it saved onto cd. Now the Question is, with the Files inside the Linux Beryl folder, when I opened it, how do I install the application onto my Linux Ubuntu:confused:

you could try getting beryl off the interet on the ubuntu system and then saving it say to documents. Then going into terminal and typing the following:

```
cd path for ur documents folder here 
```

the terminal window should have documents as the path.

then type 
```
./make
```
 then 

```
./configure
```

hope that works for you :)

---

### Post by fmartinez on 2007-12-08
why are you trying to install Beryl??? Compiz-Fusion is the combination of both Beryl and Compiz.... that's the most up to date version.... it's very easy to install in Ubuntu.

---

### Post by UK-Wobbie on 2007-12-08
Look for "Advanced Desktop Effects Settings" More better then Berys and can do more stuff then Berys :)

Go to your "Synaptic Package Manager" And look for "compizconfig-settings-manage":)

---

### Post by ~LoKe on 2007-12-08
> **lenswipe said:**
> you could try getting beryl off the interet on the ubuntu system and then saving it say to documents. Then going into terminal and typing the following:

```
cd path for ur documents folder here 
```

the terminal window should have documents as the path.

then type 
```
./make
```
 then 

```
./configure
```

hope that works for you :)

That's bad information, mainly since it would be...

```
./configure && make && sudo make install
```

---

