---
title: "[SOLVED] Help with X server!"
date: 2008-04-06
forum: General Help
---

### Post by neodude237 on 2008-04-06
I am having major problems with my ubuntu installation. I just installed 7.04 with Wubi and it says my X server can not start, and I have no idea how to get to my desktop, and I need a lot of help. Please make sure a newbie can understand the answers ;)

---

### Post by Crafty Kisses on 2008-04-06
> **neodude237 said:**
> I am having major problems with my ubuntu installation. I just installed 7.04 with Wubi and it says my X server can not start, and I have no idea how to get to my desktop, and I need a lot of help. Please make sure a newbie can understand the answers ;)

Try this:
```
startx
```

---

### Post by Rocket2DMn on 2008-04-06
If startx doesn't work, try following this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you need further help, let us know what kind of video card you have, please.

---

### Post by neodude237 on 2008-04-06
Trying the guide now, my card is an ATI Radeon X1200

---

### Post by Rocket2DMn on 2008-04-06
OK, you will want to install the restricted drivers when you get back into the GUI.

---

### Post by neodude237 on 2008-04-06
I just selected Vesa as my driver, and it said it started "ok" I am rebooting now...
edit: didn't work :(
When I try startx, it gives me:
Fatal Server error:
Caught signal 11. Server Aborting
X1OL fatal error 10 error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
Xauth: error in locking authority file /home/myname/.Xauthority

---

### Post by Rocket2DMn on 2008-04-07
OK, I'm thinking this is because you installed with Wubi.  This is not an official installation method.  I would suggest uninstalling (however that is done with a Wubi install), then installing normally by burning the Ubuntu .iso LiveCD image file to a cd-r.  With that you can install Ubuntu normally by resizing your hard drive to make room for Ubuntu.
Have a look here - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by neodude237 on 2008-04-07
The reason I was using feisty was because hardy was giving me problems with Wubi also, so Wubi is out for me, should I just try a Hardy ISO, or should I get Gutsy?

---

### Post by Rocket2DMn on 2008-04-07
You should go with Gutsy since Hardy is still in Beta development stages and is not stable for normal use.  Do a regular install for a dual boot, Wubi tends to create problems for some people.

---

### Post by neodude237 on 2008-04-07
Will I be able to easily upgrade to Hardy later?

---

### Post by Rocket2DMn on 2008-04-07
Yes, the Update Manager will let you know when Hardy is released, otherwise you can have it check manually. It will then notice the update and prompt you if you want to do the upgrade to Hardy, then it will download all the update stuff (could take awhile if the servers are clogged, which they will be when Hardy first gets released), then you will have Hardy after you reboot.

---

### Post by neodude237 on 2008-04-07
Thanks, I was curious if I would have to download a whole other iso, which I really do not want to do.

---

### Post by neodude237 on 2008-04-07
Ok, I am installing now, I used Vista to make unallocated space, and told Ubuntu to use the largest amount of free space in the install. The graphics loaded on the live CD, but my wifi is not working @_@ so I may need some more help, thanks in advance!

---

### Post by Rocket2DMn on 2008-04-07
You should start a new thread for your wireless problem, I'm no pro with wireless, sorry.

---

### Post by neodude237 on 2008-04-07
Thanks so much for all the info so far, the install should be done soon, and I will post, thanks etc when I solve all my graphics problems if there are any when I am done.

---

### Post by neodude237 on 2008-04-07
THANK YOU!!! IT WORKED! NO X SERVER OR ANYTHING! I finally dual booted, thank you so much! Now for my wireless card, but at least I can boot into Linux!

---

