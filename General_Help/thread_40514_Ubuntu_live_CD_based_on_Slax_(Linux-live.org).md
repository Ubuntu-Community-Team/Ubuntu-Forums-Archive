---
title: "Ubuntu live CD based on Slax (Linux-live.org)"
date: 2005-06-09
forum: General Help
---

### Post by fabinho on 2005-06-09
I am studing a way to do an Ubuntu Live CD with an alternative method: using [www.linux-live.org](www.linux-live.org) scripts.

They are the same scripts used by Slax, Gnox and Xarnoppix3.

It is simple:

1) You need a normal HD Hoary install

2) Compact it with mksquash to an file: "hoary.mo"

3) Create a master directory

4) Copy all CDROM files from Xarnoppix to master

5) Replace all *.mo files from master/base/  with hoary.mo

6) There are some adjusts to be done... But it is basically it.

Note: it is completelly experimental!!!!!


[B]Please: is there anyone doing something like that? 
I would like to now your results!
Thanks![/B]


.

---

### Post by angrykeyboarder on 2005-06-09
[QUOTE=fabinho]I am studing a way to do an Ubuntu Live CD with an alternative method: using [www.linux-live.org]("http://www.linux-live.org") scripts.

They are the same scripts used by Slax, Gnox and Xarnoppix3.

It is simple:

1) You need a normal HD Hoary install

2) Compact it with mksquash to an file: "hoary.mo"

3) Create a master directory

4) Copy all CDROM files from Xarnoppix to master

5) Replace all *.mo files from master/base/  with hoary.mo

6) There are some ajusts to be done... But it is basically it.

Note: it is completelly experimental!!!!!


[b]Please: is there anyone doing something like that? 
I would like to now your results!
Thanks![/b]


.[/QUOTE]

What were your results?

---

### Post by fabinho on 2005-06-09
Yes, it works! But I need to solve some problems that remain (my USB stick isn't working, for exemple)... The central idea is to use unionfs to do Hoary believes that it is working on an HD install.

I have to do little changes on Slax/Xarnoppix scripts and on Ubuntu too. And I did everything "by hand".

Basically, I have to merge Slax's kernel modules to hoary.mo (unionfs merges hoary.mo with 2.6.11.8.mo). Note that I am using the 2.6.11.8 Slax Kernel. And merge them with another diretory with some Xorg configurators (my x.mo module) that are among the Xarnoppix tools (mdetect, x-detect).

Now I have to refine it.

I call it Ubuntix.

.

---

### Post by fabinho on 2005-07-29
[http://ubuntix-en.blogspot.com/](http://ubuntix-en.blogspot.com/)

---

### Post by 1c3d0g on 2005-07-31
Looks like a great project. But now someone needs to do "Kubuntix" too... ;)

---

### Post by DecIRC on 2005-09-05
[QUOTE=fabinho][http://ubuntix-en.blogspot.com/](http://ubuntix-en.blogspot.com/)[/QUOTE]
 Hmmm I left the first comment on this site... but not many activities... Are you ok with your project ?

---

### Post by fabinho on 2005-09-05
I am still work on it. As soon as possible a beta version will be released.

---

### Post by DecIRC on 2005-09-07
[QUOTE=fabinho]I am still work on it. As soon as possible a beta version will be released.[/QUOTE]
 Could you leave somewhere a "workbook" ? I'm working exactly on the same thing, (just beginning) and I think it could be smart if I can avoid to make the same research you did....
A kind of tuto who explained what to do until now...

dEc

---

