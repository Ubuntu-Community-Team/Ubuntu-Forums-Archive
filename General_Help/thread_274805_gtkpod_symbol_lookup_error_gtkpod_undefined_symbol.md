---
title: "gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint"
date: 2006-10-10
forum: General Help
---

### Post by Old Pink on 2006-10-10
Hi,

Just updated to gtkpod 0.99.8 (from 0.99.2) after I was told this includes album artwork functionality. 

I now get this error (and a white flash on my screen) when running it:
```
matt@matt-desktop:~$ gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
matt@matt-desktop:~$
```
Help, please? This is vital!

- Matt

---

### Post by Old Pink on 2006-10-10
Running with sudo allows me to open the application, but clicking things immeaditley brings it to halt. :(

When using sudo, as soon as I click something iPod related I get another error, here's the complete terminal:
```

matt@matt-desktop:~$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
matt@matt-desktop:~$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoin t
matt@matt-desktop:~$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_info_get_ipod_info_t able
matt@matt-desktop:~$ sudo gtkpod -m /media/ipod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoin t
matt@matt-desktop:~$ sudo gtkpod -m /media/ipod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_info_get_ipod_info_t able
```

---

### Post by roob85 on 2006-10-19
ive also just done this and get this erro when ever i try to either have it read my ipod or goto set the mountpoint in the options.....id realy like to see soe updated packages for the newer gtkpod and all that good stuff...cuz for some reason it has stopped letting me add videos to my ipod(even though i have like 20-30 vids i have put there with gtkpod) :/ ....so if anyone knows how to solve either one of these probs your help will be appreciated

---

### Post by Beej on 2006-10-24
anybody solved this yet? I'm having the same trouble.

---

### Post by raffrules on 2006-10-24
so do i...

:(

---

### Post by Beej on 2006-10-25
I restarted my machine and mounted my nano manually before starting gtkppod. GTK pod opened wihout error, but I got permission errors as I tried to save changes. I'm at work at the moment but I'll try and post the terminal output when I get back home.

---

### Post by shizow on 2006-10-31
any news on this error
i have the same problems

---

### Post by Beej on 2006-11-01
I had to revert back to 0.99.2 to get things working

---

### Post by mrhelpman on 2006-11-06
> **Old Pink said:**
> Hi,

Just updated to gtkpod 0.99.8 (from 0.99.2) after I was told this includes album artwork functionality. 

I now get this error (and a white flash on my screen) when running it:
```
matt@matt-desktop:~$ gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
matt@matt-desktop:~$
```
Help, please? This is vital!

- Matt

I have just got the same error - you are not alone

JT

---

### Post by drobvice on 2006-11-11
Same here.

---

### Post by exor|grey on 2006-11-14
This is how I solved this problem:

Uninstall the old version of gtkpod and libgpod0.
Compile from source the new version of libgpod
Compile from source new version of gtkpod.

Fixed the issue. It appears that compiling gtkpod will use the old version of libgpod if it is installed.

---

