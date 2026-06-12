---
title: "Wine"
date: 2006-07-07
forum: General Help
---

### Post by Ruben123 on 2006-07-07
???? I instaled somthing with wine, but i can't find the file, do somboddy know where wine installed the program???

thank you

---

### Post by mcman42 on 2006-07-07
Easy way:
1) Open Nautilus
2) hit CTRL+L
3) in adress bar type: ~/.wine/drive_c/Program\ Files/ and hit ENTER
4) Then look in the folders for whatever you installed.

gl

---

### Post by Ruben123 on 2006-07-07
ok, that was working, now that stupid program can't find the cd, pff, it's always the same

---

### Post by jethro10 on 2006-07-07
I've found with some wine progs, if you put in the CD and let it mount. Then run the Windows program, the CD is usually available.

I find CD's non existent sometimes if I put it in after the program is running.

J

---

### Post by mcman42 on 2006-07-07
> **Ruben123 said:**
> ok, that was working, now that stupid program can't find the cd, pff, it's always the same

- open terminal
- type "winecfg"
- in the drivers tab make sure that your cd drive is correctly setup and the type is set to CD-Rom
- save and close
- try running your program

If above doesnt help try looking for instructions at [applications database]("http://appdb.winehq.org/").
Hope this will help you.

/mc

---

### Post by Ruben123 on 2006-07-07
nope, the last thing wasn't working, and monting a cd, i don't know how, i only now how to unmount :p

---

### Post by mcman42 on 2006-07-07
In most cases it should automount. Try rebooting. If the CD wont appear use this command: "sudo mount -t udf,iso9660 -o user,noauto /dev/hdd /media/cdrom0"

where hdd is your CD-rom device
and cdrom0 - your mount foulder for this device

---

### Post by Ruben123 on 2006-07-07
mmm, when i am using winecfg, and i set up the drivers, wine always del D:  /media/cdrom0

so i can't configure the cd

---

### Post by mcman42 on 2006-07-07
> **Ruben123 said:**
> mmm, when i am using winecfg, and i set up the drivers, wine always del D:  /media/cdrom0

so i can't configure the cd

Sorry, didnt' quite understand you. What did you mean by that?

---

### Post by Ruben123 on 2006-07-07
> **mcman42 said:**
> Sorry, didnt' quite understand you. What did you mean by that?

whele, when i run winecfg, and i set up the drivers, than i aply and guit, when i go back, the cd drive is away, than i need to set that up again, and again, and again ...

---

### Post by Ruben123 on 2006-07-07
those will stay

c:   ../drive_c
h:   /home/ruben
z:   /

this wil always go away

d:   /media/cdrom0

---

### Post by mcman42 on 2006-07-07
Sounds really weird. What version of wine are you running? It probbly wony change anything, but try "sudo winecfg" and apply the changes.

---

### Post by Ruben123 on 2006-07-07
I use wine 0.9.9

and no, sudo is also not working :s

---

### Post by mcman42 on 2006-07-07
Well, maybe some of the cool guys out here will help, but I am all out of ideas. The last thing I can advise you is to update your wine (mine is ..16) you can do that eiher on your own or throgh automatix.

---

### Post by Ruben123 on 2006-07-07
> **mcman42 said:**
> Well, maybe some of the cool guys out here will help, but I am all out of ideas. The last thing I can advise you is to update your wine (mine is ..16) you can do that eiher on your own or throgh automatix.

I thank you

---

### Post by mcman42 on 2006-07-07
You are welcome. Too bad I didnt succed at helping you to resolve your problem.

---

