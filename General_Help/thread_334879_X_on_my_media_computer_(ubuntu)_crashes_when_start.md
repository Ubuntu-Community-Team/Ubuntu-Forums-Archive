---
title: "X on my media computer (ubuntu) crashes when started and freezes compuer!"
date: 2007-01-09
forum: General Help
---

### Post by zeltak on 2007-01-09
Hi again

I am not a new linux user yet i have a computer a friend of mine help setup when i just started using linux which acts of a server/storage for all my media. It comes up by default in a non graphic login. today after using ubuntu on my main desktop for a bit i decided to look into that media computer and maybe play with some settings. problem is that after ubuntu loads ok and i login in text mode, when i enter startx to start X up everything freezes and is grey and the computer is locked solid, i cant use mouse,keyboard etc..i cant get to a terminal and i am left with only a forced restart. i really dont know where to start looking for whats wrong, can anyone give me ideas?

thx alot

Zeltak

---

### Post by floke on 2007-01-09
you could try...

sudo -dpkg reconfigure -phigh xserver-xorg

and follow the onscreen instructions to set it up

hope it helps

---

### Post by zeltak on 2007-01-09
thx for the answer

i tried the command but i get this:

sudo: please use single character options
sudo: illegal option `-dpkg'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }


anything i should change in the command?

thx 

Zeltak

---

### Post by zeltak on 2007-01-10
hi !

just to add that i looked in the logs and found this around the time of the crash:

Jan 10 10:37:47 localhost kernel: [92797.438916] [drm] Initialized drm 1.0.1 20051102
Jan 10 10:37:48 localhost kernel: [92797.477411] [drm] Initialized savage 2.4.1 20050313 on m
inor 0
Jan 10 10:37:48 localhost kernel: [92797.479267] mtrr: base(0xe2000000) is not aligned on a s
ize(0x5000000) boundary
Jan 10 10:37:48 localhost kernel: [92797.481281] agpgart: Found an AGP 1.0 compliant device a
t 0000:00:00.0.
Jan 10 10:37:48 localhost kernel: [92797.481322] agpgart: Putting AGP V2 device at 0000:00:00
.0 into 1x mode
Jan 10 10:37:48 localhost kernel: [92797.481365] agpgart: Putting AGP V2 device at 0000:01:00
.0 into 1x mode
Jan 10 10:37:52 localhost gconfd (zeltak-9619): starting (version 2.14.0), pid 9619 user 'zel
tak'
Jan 10 10:37:52 localhost gconfd (zeltak-9619): Resolved address "xml:readonly:/etc/gconf/gco
nf.xml.mandatory" to a read-only configuration source at position 0
Jan 10 10:37:52 localhost gconfd (zeltak-9619): Resolved address "xml:readwrite:/home/zeltak/
.gconf" to a writable configuration source at position 1
Jan 10 10:37:52 localhost gconfd (zeltak-9619): Resolved address "xml:readonly:/etc/gconf/gco
nf.xml.defaults" to a read-only configuration source at position 2
Jan 10 10:37:52 localhost gconfd (zeltak-9619): Resolved address "xml:readonly:/var/lib/gconf
/debian.defaults" to a read-only configuration source at position 3
Jan 10 10:37:52 localhost gconfd (zeltak-9619): Resolved address "xml:readonly:/var/lib/gconf
/defaults" to a read-only configuration source at position 4
Jan 10 10:38:09 localhost gconfd (zeltak-9619): Resolved address "xml:readwrite:/home/zeltak/
.gconf" to a writable configuration source at position 0

i dont know but maybe it helps

Zeltak

---

### Post by nikhilk on 2007-01-10
The command Steve mentioned has a typo
You should instead run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by zeltak on 2007-01-10
thx

the config worked unfortunately i still get the freeze. it seems like it comes on in grey and then i see the mouse and then nothing. is there specific logs i should look into? is there anything else i can do?

thx

Zeltak

---

