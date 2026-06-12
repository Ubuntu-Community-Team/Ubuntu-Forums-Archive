---
title: "Please.. I will pay you if you can help me.??"
date: 2008-05-11
forum: General Help
---

### Post by droobuntu on 2008-05-11
Hello Mates, I am Drew, some great info you all have here.. however I am still in a hole...

   I just got Ubuntu 7.10 (gutsy gibbon) installed last night, and had it running perfect for the night. 

I am fairly new to all of this, but learn fairly quick...  and dont have too much hard time , as of yet.... but.... as of this morning.. I went to load up Ubuntu... and it would not work, all I would get is the black "dos" screen and finally figured out I had to type "startx" to make it to my desktop. 
 Wehn I finally got to my desktop... an error pops up saying >> 

"failure to initialize HAL"

I have read through a bunch of things on it... yet still no fix...??

also.......  now.. whenever I try to access anything in admin, I get this.. 

"Failed to run network -administrator as user script, contact your administrator for details"

 I thought I was the Admin?? 

also.. in the terminal...  I type in what I am told elsewhere.. and I just get nothing from it, just another command line.??

 Please , anyone tell me how to fix these "small" yet annoyyying" problems?

If anyone can help.. I would surely pay them if need be. 

Many thanks. 
Drew

---

### Post by droobuntu on 2008-05-11
ohh, also.. I am online right now using the disc, "live session user".. whatever that means.   and I still have windows XP on this machine as well, partitioned. 

uhmm...  Im really just going crazy over here.... thought I was all set after hours and hours yesterday...  and then... poof.... ? lol
:/
Thanks

---

### Post by grannyw on 2008-05-11
Hi

If you have this problem, please follow these steps:
1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. 

Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.

---

### Post by p_quarles on 2008-05-11
First of all, please be patient. This is not real time, live support. People with answers to your questions will undoubtedly answer, if you give it time.

Second, anyone offering their services for payment on this board will be considered a spammer and promptly banned. If you want to pay for support, you should contact a paid support service, and not a public internet forum.

---

### Post by Victormd on 2008-05-11
Drew,
Post you hardware specs so we can have an idea of what we're dealing with. Also, why did you install Gutsy (7.10) and not Hardy (8.04)?
From your description, it seems like you were "playing around" with ubuntu quite a bit (very normal!) and in the process, you may have broken it yourself, but was only reflected today when you restarted the system... The reason I say that is because you're able to run the live CD with no problem so once installed, ubuntu should run the same way... When you have problems with the live CD is usually when you have problems (major) with ubuntu.

My personal advise, try installing Hardy 8.04... it provides a lot more hardware support...

---

### Post by droobuntu on 2008-05-11
Thanks alot guys, quick replies, much appreciated! @ P_quarles~ My apologies, It wont happen again. 

grannyw, ok.. so, I have to exit the live disc and start ubuntu regular to do that right?  and also.. Im not even sure exactly where to find what your talking about? sorry for my ignorance... thanks :)

Victormd~ Ok, I will get them and show you soon... and I installed the 7.10 because I had the disc I got about a month ago... can I just install the 8.04

 one without a disc? from a link or something? 
Thanks soo much guys, I really appreciate everything. :D
Drew

---

### Post by tgalati4 on 2008-05-11
Did you perform any updates after installation?  Sometimes updating the xorg graphics server will cause breakage.

---

### Post by droobuntu on 2008-05-11
I might have, but honestly.. Im not positive... : /

I cannot even get connected to the internet now... (Im back on XP).. so I cant even upgrade to hardy.... 

I also keep getting something that says..  No Sudo, or root access priveleges...?? 

this is really hard switching back and forth and remembering info... sorry if Im not very clear... 
thanks

---

### Post by russo.mic on 2008-05-12
Why don't you just download a hardy cd and reinstall?  There is a great driver for windows XP and vista that will allow you to mount your ext3 partition in windows for backup, and you could easily reinstall to the latest hardy heron.

Here is a link to the ext3 windows driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It's free.  I know it says EXT2, but it works fine for ext3 as well.  I've never had a problem with it.

Good Luck!

Russo

---

