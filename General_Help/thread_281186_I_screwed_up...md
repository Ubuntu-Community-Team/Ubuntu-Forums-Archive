---
title: "I screwed up.."
date: 2006-10-20
forum: General Help
---

### Post by pkslot on 2006-10-20
As always, i belive in learning by doing, but this time.... i think i screwed up, big time.

I removed Synaptic. I had some problems, couldn't get to my reposetory list, so i kinda decided that maybe it was time to remove it, and then install it again. I figured that it would take care of things for me, but i think i just made a bigger mess ](*,) 

In the terminal nothing happends, when i "sudo apt-get install synaptic" it.



......Help.... anyone...:-k

---

### Post by meng on 2006-10-20
How did you "remove" it? by apt-get?
Did you change your repository list at all?

---

### Post by pkslot on 2006-10-20
Yup, i did it by "sudo apt-get remove synaptic" in the terminal.

I didn't touch my list at all, that was the problem in the first place, when i tried to resch it, either through synaptic or by System>Adninistration>Softwareyadayada (my ubuntu is a danish version ;) ) i couldn't get to it.

---

### Post by Old Pink on 2006-10-20
> **pkslot said:**
> In the terminal nothing happends, when i "sudo apt-get install synaptic" it.

[B]Why:
[/B]apt-get relies on Synaptic, so apt-get won't work without it.

[B]How to fix:
[/B]Find a copy of Synaptic on sourceforge or something, and compile it from source.

---

### Post by pkslot on 2006-10-20
> **Old Pink said:**
> [B]Why:
[/B]apt-get relies on Synaptic, so apt-get won't work without it.

[B]How to fix:
[/B]Find a copy of Synaptic on sourceforge or something, and compile it from source.



Hehe, i knew i made a mess :mrgreen: 

Well to sourceforge i go. but how do i compile it?

---

### Post by Old Pink on 2006-10-20
If you download a .deb, just open the .deb with GDebi. 

If you download a compressed file (.zip/.tar.**) then you need to extract it somewhere, find the "README" file and read that for further instructions. :) 

Or, if you give me a link I'll make you a .deb installer. :D

**EDIT: **[http://packages.debian.org/unstable/admin/synaptic.html](http://packages.debian.org/unstable/admin/synaptic.html) - Scroll down for the installation files.

---

### Post by skymt on 2006-10-20
> **Old Pink said:**
> [B]Why:
[/B]apt-get relies on Synaptic, so apt-get won't work without it.

Um... no it doesn't. Synaptic is a graphical front-end for apt. So, Synaptic relies on apt, not the other way around. In fact, the server version of Ubuntu installs apt-get and (I think) aptitude, but not Synaptic.

apt only relies on libc, libgcc, and libc++.

---

### Post by pkslot on 2006-10-20
> **Old Pink said:**
> If you download a .deb, just open the .deb with GDebi. 

If you download a compressed file (.zip/.tar.**) then you need to extract it somewhere, find the "README" file and read that for further instructions. :) 

Or, if you give me a link I'll make you a .deb installer. :D

**EDIT: **[http://packages.debian.org/unstable/admin/synaptic.html](http://packages.debian.org/unstable/admin/synaptic.html) - Scroll down for the installation files.

Well i found the same one, but when i write "./configure" ... well i'll copy/paste it

> pkslot@tipan-pk:~/Desktop/synaptic-0.57.11$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


---

### Post by bsussman on 2006-10-20
> **Old Pink said:**
> [B]Why:
[/B]apt-get relies on Synaptic, so apt-get won't work without it.



apt suggests but does not depend on synaptic - synaptic is a graphical front end, apt-get a wrapper for dpkg.

---

### Post by CatKiller on 2006-10-20
> **pkslot said:**
> Well i found the same one, but when i write "./configure" ... well i'll copy/paste it

That will be because you don't have a compiler :rolleyes: If you've still managed to keep hold of apt-get or aptitude, then you can do ```
sudo aptitude install build-essential
``` but if you can do that then I don't see why you can't ```
sudo aptitude install synaptic
```Otherwise, if your package management **is** completely screwed then I don't see many easy ways to get it working again. Other than copying your Home folder somewhere, reinstalling, and not removing apt in the future.

EDIT: It **is** possible to compile a compiler. But I don't think it's pretty.

---

### Post by pkslot on 2006-10-21
Thanks man, i'll give it a try..... or a day to figure out, but nothing of value is on my drives. Funny, but it was a new, clean install so i don't understand that i had any problem at all.

In the end, i bought a new HD the day before yesterday (haven't installed it yet), the old one makes scary noises sometimes :-#  so i thought that it maybe was time to do something about it. I've had this one for about six years by now, and maybe it has a little to do with it :mrgreen: 

But all the trouble started, cause i was running BUMPS (great little thing) and realyzed that i had to turn all my reposetorys on, to install it.

Before that, i ran a complete update on Dapper, no fiddling, no fuzz, but it still gave me a lot of problems and it just acted weird when i tried to ad the multiverse and universe lists.

Strange.. :-k

---

