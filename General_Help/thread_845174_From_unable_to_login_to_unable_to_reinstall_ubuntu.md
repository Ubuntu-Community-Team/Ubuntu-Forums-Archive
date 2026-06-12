---
title: "From unable to login to unable to reinstall ubuntu!"
date: 2008-06-30
forum: General Help
---

### Post by came2die on 2008-06-30
*I was adding fonts into fonts folders and suddenly I couldn't use the terminal and resource manager. So I restarted X.*
**Here is the interesting part:**

After the restart, the login background showed up, but there was no login box(for user name)and the mouse had a waiting symbol...
I waited for several minutes, the screen has in the meantime gone from previous situation to black screen and back again. Then an error has popped up saying something like: "the x has restarted 6 times, thats not a good thing, you will have to wait for 2 minutes..."

After those 2 minutes previous situation repeated. Then it changed from gui to cli(tty2)..

I restarted(I knew that it won't help:/), tried recovery mode, everything...

I tried to install ubuntu again but no luck...

Here is the screen shot of the error I got when I tried reinstalling ubuntu again :(
[[img]http://shrani.si/t/3g/TK/1ug2M8wi/p6304180.jpg[/img]](http://shrani.si/?3g/TK/1ug2M8wi/p6304180.jpg)

I hope someone can help me because I don't know what to :confused:

---

### Post by t4ggs on 2008-06-30
i dont know why it happened but about reinstalling...r u booting from the cd?

---

### Post by came2die on 2008-06-30
Yes from CD. I tried gutsy gibon and hardy heron(install only and wubi). Also I tested both CDs for errors.

In the meantime I tried win XP(if it gets to select the partitons menu), I didn't do a thing but now the partition table is broken(don't have a clue how this is possible...)

ANY SUGGESTIONS?

---

### Post by damis648 on 2008-06-30
Check the md5sum of the ISO you used. There are guides and windows applications you can find to do this.

---

### Post by came2die on 2008-06-30
I did when I burned those 2 CDs(some weeks ago for hardy and some months for gutsy) and I also checked them for errors in boot menu... So you think I should do it once more :)?

No one knows what does that error mean(screen shot)?

---

### Post by damis648 on 2008-06-30
That BusyBox signifies an error. Busybox is a simplified Unix shell. To diagnose it, when you boot, enter the grub and press "e" on the Ubuntu kernel you want to boot (Usually the top option). Go down one line to the kernel line and press "e" again. In this "editor", scroll the cursor over left and remove the words "quiet" and "splash". Press enter and then "b" and wait for the BusyBox. When you get to the busybox, scroll up and take a screenshot of the last couple error messages.

---

### Post by came2die on 2008-06-30
Ok I will try

---

### Post by came2die on 2008-06-30
*In the meantime I tried win XP(if it gets to select the partitons menu), I didn't do a thing but now the partition table is broken(don't have a clue how this is possible...)*

I can't get into grub. I can remove "silent" and "splash" when installing from cd if it helps...

Is it possible that both CDs are fine but I still can't reinstall ubuntu(to me it sound impossible but...)?

Can I repair partition table(I know its a stupid question but...)

---

