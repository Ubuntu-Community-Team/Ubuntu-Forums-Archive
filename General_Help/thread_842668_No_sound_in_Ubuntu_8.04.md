---
title: "No sound in Ubuntu 8.04"
date: 2008-06-27
forum: General Help
---

### Post by slyscafe on 2008-06-27
I have tried everything that the other posts have said, but to no avail.

Basically, I realize what the problem is: The only place I GET sound is from Pidgin...everything else seems to have no sound what-so-ever.

I know the sound driver which works, but I don't know how to set it as the default sound driver.

---

### Post by ajmorris on 2008-06-30
hi there
run sudo alsaconf in a terminal, choose your sound driver from what it picks up, then set your volume, and see if sound now works.

if it doesnt work, can you please post the output of sudo lspci

AJ

---

### Post by danwood76 on 2008-06-30
Sounds like a pulse audio issue.
There is a very good guide to setting this up correctly:
[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup)

It sorted my issues where firefox (actually flash) would stop VLC from being able to produce sound.
Now all apps work beutifully together.

---

