---
title: "Missing disk space"
date: 2007-01-19
forum: General Help
---

### Post by kariopto on 2007-01-19
Hello, I'm running out of disk space, and I noticed that when i run df -h, it says
```
Filesystem            Size    Used Avail Use% Mounted on
/dev/hda4             118G  110G  2.3G  99% /home
```
I also noticed that when in have files in the xfce trashcan, they obviously take up space in my hard drive, but they aren't counted by df, causing it to say weird things, like the 6GB missing above (it says i have 2GB available, when I should have 8 ).
So, my xfce trash is empty, and my question is, what could be using those 6GB?, or is there just a bug in df and the size of that partition is really 112.
Thanks in advance!

---

### Post by taurus on 2007-01-19
```
sudo aptitude clean
sudo rm /root/.Trash/*
rm ~/.Trash/*
```

---

### Post by kariopto on 2007-01-19
Nope.. sorry.
Still the same problem.
.Trash/ was empty (I had already checked it), but I deleted it anyway.
and sudo aptitude clean didn't help either..
Any other ideas?

---

### Post by taurus on 2007-01-19
Did you save a bunch of stuff to your $HOME directory?  

```
du /home
```

---

### Post by kariopto on 2007-01-19
Ok.. weird..
du says 114993444... so about 115GB
which is all in /home/kariopto/
but in thunar.. it says /home/kariopto/'s size is 111GB.
So.. where is all that stuff??
Thanks a lot for your replies

---

### Post by taurus on 2007-01-19
The "du /home" will tell you which directories in your $HOME take up what amount of space.  If you've downloaded something and don't need it anymore, delete it.  It just takes up space.

---

### Post by po0f on 2007-01-19
taurus,

I actually prefer `du -h --max-depth=1 ~`.  It will show you how much space directories directly under ~ take up, as well as outputting it in a "human-readable" format (as pertaining to the size, it's easier to look at MBs used as opposed to bytes).


kariopto,

There is no easy way to translate from bytes to GBs.  The output you got from `du` is in bytes, but you wanted GB output.  You can't just move the decimal.  A rough estimate would be to take the byte output and divide it by 1024 to get the MB, then divide again by 1024 to get the GB.

---

### Post by kariopto on 2007-01-19
ok.. thanks for your help..
So in the end, is it just because df adds things up differently than du?

---

### Post by po0f on 2007-01-19
kariopto,

Concerning the "missing" 6 GB, when you created the filesystem, a portion of it (~5% IIRC) is reserved for the superuser.  This is so that the filesystem doesn't get completely full.

---

### Post by kariopto on 2007-01-19
Thanks a lot po0f

---

