---
title: "Help fixing grub or partitions...not sure which..."
date: 2008-01-26
forum: General Help
---

### Post by big dizzle on 2008-01-26
Anyway, here is the situation.  This post is kind of long, but I wanted to make suer I didn't leave out anything important.  Here we go...

My hardware:

ASUS K8V mobo w/AMD 64 3000+,  2gb RAM, nVidia 6200 AGP, dvd drive, primary hd is 30 gb and slave is 60gb

OSes:

On a 20 gb partition of the primary drive I have Windows XP installed
On the slave drive I have Ubuntu 7.10

The problem:

My computer was working perfect, and I did a normal restart from the shutdown menu of Ubuntu, when the computer restarted, every thing looked normal (bios screen came up like normal) then when it got to the screen where it plays a message saying that it is going to load grub, I get Error 17.

So I put in the Live cd (same cd that has given me three successful ubuntu installs) and changed the boot device priority in the bios to the dvd drive so it would boot from the live cd.  it did, and it displayed the menu you get when you first install ubuntu (start or install...yadayadayada...boot from first partition) I chose start or install (the first option on the menu) and the ubuntu loading screen comes up like normal, but then I get the following error:

buffer i/o error on device hdb5, logical block x (the line keeps on repeating and the value of x incriments in a wierd pattern)

Possible cause:

I recently installed virtualbox to run xp while I was in Ubuntu, I had it working fairly well, but one thing I noticed is that after I changed some of the user settings (commonly listed on howto's concerning installing xp on virtualbox) and restarted my computer, i noticed that the boot menu had been changed.  to the top it had added ubuntu server, and then it listed the ubuntu generic and my xp like normal.  no clue why this happenned...i know i'm new to ubuntu, but i'm 100 percent positive i didn't instal the server OS by mistake :)

anyway, ive looked around on the forums for possible fixes, and they all involve editing the boot menu (the menu.lst file in the grub folder) and this won't work for me b/c i don't even get the boot menu to try and go to the rescue mode and fix it from the terminal, i don't get the option to bring up the grub terminal, and when i try and use the live cd I get that pesky buffer i/o error.  some other posts also suggested going into the bios and changing some of the settings of my hard drives from there, but my settings were already what was being recommended, and both of the hard drives were detected.

any ideas on how to fix this would be much appreciated...

---

### Post by big dizzle on 2008-01-26
while i was typing this thread, the live cd eventually loaded into the desktop and the option to install is there.  since i need my computer running, i am just going to reinstall, unless someone posts a fix w/in the 24 hrs or so...

ps if you come across this post after i've already reinstalled, plz feel free to explain the problem and suggest how i could have fixed it so anyone who has the same problem as me can search it, or if it happens to me again i will know how to fix it.

THNX :)

---

### Post by big dizzle on 2008-01-26
ok, so i completely reinstalled linux on my primary hd.  i tried to reformat the slave, but it didn't work.  i think that the slave drive might have just died on me, but i'm not sure how to check.  

can anyone tell me how to test a hd to see if it still works?

---

### Post by louieb on 2008-01-26
Go to the manufactures website. Most have a disk checking utility  you can download. I know WD and Maxtor do.

---

