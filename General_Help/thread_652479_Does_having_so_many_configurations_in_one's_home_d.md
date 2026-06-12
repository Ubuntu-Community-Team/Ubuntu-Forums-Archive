---
title: "Does having so many configurations in one's home dir slow a desktop down?"
date: 2007-12-28
forum: General Help
---

### Post by wersdaluv on 2007-12-28
I have been tweaking Ubuntu (GNOME) for speed (please don't suggest lighter DEs). I noticed that when I created a fresh user account, that account runs much faster than mine even if it has more apps running. My old configuration used xfwm4 and the Crux theme so I expected it to be really fast but it was too slow for me. I decided to delete my home dir and just preserve my important files including important configuration files. 

With this fresh home dir where I just added my important old files and some configuration files, my desktop is much faster even if it uses Metacity and the Nodoka theme with the same number of running applications. Actually, this fresh account runs faster even with more running apps than my old home account. 

Maybe, there are other factors, but it seems to me that too many configuration files slows down desktop. Do you think that the amount of configuration files slowed down my desktop or it was something else? What could it be? :)

:KS

---

### Post by p_quarles on 2007-12-28
Configuration files themselves aren't executable, so they can't directly use any system resources. You can find out what processes are eating up the most resources by running this from the terminal:
```
ps aux
```
Look for the processors using the most CPU time and memory, and you'll likely find your culprit. And, yes, if those programs are using complicated or broken config files, then they could be using more than they need to.

---

### Post by forestpixie on 2007-12-28
have to say don't really notice a difference- being a bit of an app monster I use whatever  I need - if it turns out to be kde - then I just carry on :)

not got much of a beast- an oldish celeron and 1Gb RAM and it all flies by

so being that I have a penchant for trying things out my /home configs are fairly bulging

---

### Post by wersdaluv on 2007-12-29
> **p_quarles said:**
> Configuration files themselves aren't executable, so they can't directly use any system resources. You can find out what processes are eating up the most resources by running this from the terminal:
```
ps aux
```
Look for the processors using the most CPU time and memory, and you'll likely find your culprit. And, yes, if those programs are using complicated or broken config files, then they could be using more than they need to.

The weird thing is that I am running the same apps that I was running before. Mmmmmm.

Thanks anyway. :)

:KS

---

### Post by wersdaluv on 2007-12-29
> **forestpixie said:**
> have to say don't really notice a difference- being a bit of an app monster I use whatever  I need - if it turns out to be kde - then I just carry on :)

not got much of a beast- an oldish celeron and 1Gb RAM and it all flies by

so being that I have a penchant for trying things out my /home configs are fairly bulging
penchant
You mean, you do not notice the difference between a fresh user account and an old one? :)

---

