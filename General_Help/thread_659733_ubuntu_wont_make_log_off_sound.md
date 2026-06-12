---
title: "ubuntu wont make log off sound"
date: 2008-01-06
forum: General Help
---

### Post by zigNzag on 2008-01-06
every sound work fine except the logoff sound whats wrong

---

### Post by nick_h on 2008-01-06
There are some threads on this topic already.  Try installing the esound package.
```
sudo apt-get install esound
```

---

### Post by dlegend on 2008-01-06
> **nick_h said:**
> There are some threads on this topic already.  Try installing the esound package.
```
sudo apt-get install esound
```

I had the same problem, installed esound and it worked after logging out, back in, and back out again.

---

### Post by nisarg on 2008-01-25
Hey,

Seems like this is very much the problem I am having. All sounds seem working fine, except the turn off sound. On Fiesty it made a sound when logging off or turn off. That doesnt seem the case on my Gutsy.

I was going to try to install the esound thing that you have suggested. 
Just curious - what is this problem? is it a known bug?
what is this package and what does it do? Is it like a driver package or something? 
Would appreciate more info.

Cheers.

> **nick_h said:**
> There are some threads on this topic already.  Try installing the esound package.
```
sudo apt-get install esound
```

---

### Post by Najmudin on 2008-01-25
> **nisarg said:**
> Hey,

Seems like this is very much the problem I am having. All sounds seem working fine, except the turn off sound. On Fiesty it made a sound when logging off or turn off. That doesnt seem the case on my Gutsy.

I was going to try to install the esound thing that you have suggested. 
Just curious - what is this problem? is it a known bug?
what is this package and what does it do? Is it like a driver package or something? 
Would appreciate more info.

Cheers.

Take a look at this link , it may help you.
[http://ubuntuforums.org/showthread.php?t=656794]("http://ubuntuforums.org/showthread.php?t=656794")

---

### Post by nisarg on 2008-01-25
Thanks. esound seems to have done the trick!!
Cheers

> **Najmudin said:**
> Take a look at this link , it may help you.
[http://ubuntuforums.org/showthread.php?t=656794]("http://ubuntuforums.org/showthread.php?t=656794")

---

