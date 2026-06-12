---
title: "Ubuntu: Blank screen with waiting cursor"
date: 2007-04-26
forum: General Help
---

### Post by acheton on 2007-04-26
Hi all,

I'm a newbie at Ubuntu and have been running Feisty for the last six or seven days. Everything was going fine until this evening, when after installing Basket GDM appears not to load. Basically when I restart after the Ubuntu logo I get a blank screen with a cursor indicating that it is waiting. In order to try and remedy this I've tried using the VESA driver when running the following from recovery mode:

```
dpkg-reconfigure xserver-xorg
```

However this doesn't solve the problem. Guessing that the basket package could be at fault I also ran the following:

```
sudo apt-get remove basket
```

which ran successfully but didn't solve the problem. Does anyone have any suggestions as to what I can do to solve this? I'm currently posting this from Windows - but I'd quite like my Ubuntu back!

Thanks,


Ach

---

### Post by m.musashi on 2007-04-27
I have had really bad luck reconfiguring the xserver. Things are usually worse after I do that than before - probably because I don't ansswer all the questions right. You can try to replace it with the backup. There should be one in the same dir with a name ending in a date (lots of numbers for year, month, day, time and so on) created by the reconfigure. You might want to back up the current one just in case too.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo mv /etc/X11/xorg.conf.xxx /etc/X11/xorg.conf
```
replace all the xxxx with the actual file name (or press tab to auto complete).

That should get your original xorg.conf back but it may or may not solve the problem. I am not familar with the basket package so I don't know what else might have changed.

For what's it's worth, when I mess things up I usually just end up reinstalling. It only takes 15-20 mins and is usually faster than solving the problem - of course you learn less that way.

---

### Post by strabes on 2007-04-27
You have to run the dpkg-reconfigure command as root. To do this run:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by m.musashi on 2007-04-27
I'm not sure about the OP, but when run dpkg-reconfigure (as root) things are usually more broken than before. I think the install process does a better job than I can with this as a reinstall usually fixes it.

Is there a way to reconfigure the xserver without human intervention - basically rerunning whatever happens during install? Obviously if X doesn't work right after an install this won't help but if it did and you manage to mess it up (or some package does), an easy way of getting back to the original setup would be nice.

---

