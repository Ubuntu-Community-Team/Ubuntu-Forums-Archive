---
title: "Sublime Text and PyCharm super laggy on 18.04"
date: 2018-09-02
forum: General Help
---

### Post by w1ll1am2 on 2018-09-02
Hello,

I have been running Ubuntu 18.04 for awhile now and have noticed that Sublime Text and PyCharm are very slow when scrolling and typing. This wasn't the case in 16.04. Has anyone else noticed this problem? Anything that I need to change to get things working correctly?

System specs below.

8 gigs ram DDR3
AMD FX-8320e 8 core
Nvidia graphics
128 gig SSD has OS drive and several other spinning disks totaling ~9 TB

Let me know if there is anything I should check. 

Thanks!

---

### Post by w1ll1am2 on 2018-09-05
After searching about this another way I found this [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1773502](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1773502) which references that Xorg takes up tons of memory on applications that redraw frequently. I had a swap partition that I noticed being used so I disabled that and the issue went away.

---

### Post by NM5TF on 2018-09-05
are you using the paid version of Sublime Text or the "trial" version ???

you might want to take a look at Visual Studio Code...it's free & you can import all your Sublime key bindings/customization....

go here   [http://https://code.visualstudio.com]("http://https://code.visualstudio.com")

tommy

---

### Post by 1clue on 2018-09-06
I'm using 18.04 and st3, paid license. It's fast for me. I have 24GB RAM though so maybe that might explain it, if there is a problem with RAM. Don't use swap.

Let me rephrase that. I have a swap partition and it's turned on, but if I find out that the system actually paged something out I upgrade RAM. So swap has been untouched on my desktop system for a few years now.

---

