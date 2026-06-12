---
title: "Big problem!!!"
date: 2008-01-30
forum: General Help
---

### Post by Moonfrost on 2008-01-30
I have Gutsy 7.10 and I have had an issue which happened for the second and third time respectively today. I'm running compiz fusion and reading something on my browser (firefox) or watching a youtube video...well, I minimize the window for something and the computer logs out automatically!!! it doesn't show the desktop at all, it just flashes the screen black and shows the normal commands you see when you log out, then it takes me to the login screen!!!! what's wrong with this picture? the first it happened was probably around 2 months ago and then today it happened twice in a matter of 20 minutes!!! does anybody what might be causing it? it's very random and I don't know if it will happen when I'm not running compiz yet.

---

### Post by Masterj15 on 2008-01-31
Lets take a look at this picture. 

1. what graphic card do you have? maybe the graphic card is none to have errors with compiz-fusion.

2. Take off your compiz-fusion and see if that is the problem.

3.What exactly are you doing in Firefox? Do you have the JavaScripts?

4. tell you specs of your hard drive. :)

---

### Post by Moonfrost on 2008-01-31
> **Masterj15 said:**
> Lets take a look at this picture. 

1. what graphic card do you have? maybe the graphic card is none to have errors with compiz-fusion.

2. Take off your compiz-fusion and see if that is the problem.

3.What exactly are you doing in Firefox? Do you have the JavaScripts?

4. tell you specs of your hard drive. :)

I have an Nvidia 6150LE integrated graphics, the card always worked perfectly with both Compiz-fusion and Beryl before even using different Linux distros.

Hasn't happened at all with Compiz with now, and I tried without and hasn't happend at all.

It depends, I'm sometimes reading stuff, watching youtube videos...it doesn't happen with the same thing always.

I have a Seagate SATA hard drive 7200rpm, don't know much more about it because it came with the computer from factory...I've have had this computer for over a year now and haven't upgraded anything yet.

---

### Post by tgalati4 on 2008-01-31
Right after the next occurance, post the output of:

dmesg | tail -50

and

cat /home/moonfrost/.xsession-errors

Sounds like something is taking out the xserver and causing a graphics reboot.  That is why it takes you back to the login screen, wiping out your session.  Java is a suspect as it has memory leaks that can cause crashes after a period of time.

---

