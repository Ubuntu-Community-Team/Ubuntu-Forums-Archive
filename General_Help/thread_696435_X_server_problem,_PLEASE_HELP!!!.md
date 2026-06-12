---
title: "X server problem, PLEASE HELP!!!"
date: 2008-02-14
forum: General Help
---

### Post by XziviT on 2008-02-14
Hello, im new in this thing of linux but ive seen it in action and i really want it, i downloaded the 7.10 version of wubi and i already installed it but when i reboot the system into ubuntu a window appears saying i dont have the graphics to run correctly ubuntu, and i dont think thats possible cuz i have a gaming laptop dell xps m1730 and it has one of the best graphic cards in existance, now after i "configure" the graphic settings a list comes up and in one of the Starting Ubiquity, it says that it failed because a "fatal IO error 104 (connetion reset by peer) on X server: 0.0"
and this also happened to me in the 7.04 version. I went to this site wiki.x.org to try to download a newest version of the x thing but when i click in the dowload thing on the newest version a lot of stuff appears and i dont know hat to download and i guess this error is because of that.
PLEASE if you know what can i do tell me and if i need to go and download something somewere please put a link, im not a pc genius so i dont understand some stuff of the errors and stuff i need to do.

Thank you.

---

### Post by ago on 2008-02-14
8.04 alpha 5 should be avaliable within days, might have better support for newer cards which might help in your case.

You can start in vesa mode though and figure out driver issues later on

sudo dpkg-reconfigure xserver-xorg

select vesa. leave other options

---

### Post by XziviT on 2008-02-14
I just installed the 7.10 version, i logged in to ubuntu and it looked pretty good but when i logged off and i tried to log in again the image to put the pass looks warped and when i type my pass a message appears also warped and i dont know what it says and now what im stucked again, is this because of the x server? because when i press esc a message in the black screen says something about the x server.

And the alpha 5 will accept the newest graphic cards so i wont have the x thing problem?

Thanx

---

### Post by syn4k on 2008-02-14
Ago, your solution does not work. I'd quit suggesting it personally

---

### Post by ago on 2008-02-15
Wubi 8.04 should work with the new ISO, but the ISO releases have been blocked by other packages since the 9th of february. See last post in [http://ubuntuforums.org/showthread.php?t=685926](http://ubuntuforums.org/showthread.php?t=685926) for a workaround.

---

### Post by syn4k on 2008-02-15
Nope. Doesn't work. I'm pretty sure that I'm tired of screwing with it too. After 80 hours of this BS...I fricken' quit. pft

---

