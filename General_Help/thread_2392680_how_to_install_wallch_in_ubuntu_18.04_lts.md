---
title: "how to install wallch in ubuntu 18.04 lts"
date: 2018-05-23
forum: General Help
---

### Post by seekertom on 2018-05-23
I just installed ubuntu 18.04 lts for 64 bit amd. i have previously installed wallch on 16.04 from terminal and had no problems. following same steps in 18 i'm told package not found.

would appreciate some steps to follow, or at least find out if wallch isnt available for 18.04.

I tried two packages, wallch_4.0-Oubuntu5.debian.tar.xz and wallch_4.0-Oubuntu5_amd64.deb
both are in my downloads folder.

for amd64 version, I got it to show the app's install dialog, but after clicking install, then entering authenticate, it just returns to the install window, no thanksfornuttinhoney or anything...

help???
thanks, st:confused:

after following y'alls advice, I got wallch installed, and after a few random reboots, it started working. Thanks for that.

5/28/18, after getting 16.04 installed on sep ssd hdd, I can compare wallch on 18 and 16. I am finding 16 much snappier, screens change quickly, while in 18, things get bogged down... screen changes hesitate between images, and while wallch is running, anything else I try to do gets really bogged down. In short, running wallch in 18 acts like a real memory hawg, but in 16 it's great. Doing all these tests on the same pc eliminates a lot of potential hardware issues in my results. Glad it works, n e how. thanks to all!
st

now I'm a happy camper, at least for the moment. Thanks for your help.
st

---

### Post by again? on 2018-05-23
wallch(4.0-0ubuntu5) is installable in 18.04 from the universe reository.
[https://packages.ubuntu.com/search?keywords=wallch&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=wallch&searchon=names&suite=bionic&section=all)

```
sudo apt update
sudo apt install wallch
```

Whether or not wallch works...I don't know.
If not start from terminal to see errors.

For deb files install with apt.
eg
```
sudo apt install [COLOR="#696969"]/full/path/to/deb[/COLOR]
```

P.S. Are you using the xorg or wayland session?

---

### Post by seekertom on 2018-05-24
[COLOR=#000000]Are you using the xorg or wayland session? 
dunno. I start ubuntu, see my name, click, enter my pw like i did in 16, im there. [/COLOR]

---

### Post by again? on 2018-05-24
You can choose the wayland session at the greeter.
Wayland is the replacement for xorg but I think xorg is the default session.
[What&#8217;s New in 18.04]("https://www.omgubuntu.co.uk/2018/04/ubuntu-18-04-download-release-features")
I have changed to xfce so not sure.

So.... did wallch install?

---

### Post by seekertom on 2018-05-27
Thanks, guber2. life progresses slowly for me these days, but I finally got back to the issue at hand, wallch. 

today i reinstalled 18.04, got it working and did the sudo thing. wallch was installed as you suggested, and acted pretty much like it did for me in 16.04, except it wont actually start the slideshow. I set up the path to my images, set up 10 sec interval etc, but clicking on start just gets me a dumb look. nothing happens.

As for which startup I follow, I now understand your question about wayland. thanks for that insight. I will continue to persuit my wallch, or hunt for another app that works like it and is compat w 18.04.. I guess I just like my pretty pictures!
thanks, st

---

### Post by #&amp;thj^% on 2018-05-27
As another solution have you considered Variety :[http://peterlevi.com/variety/](http://peterlevi.com/variety/)
I gave up on suggesting "wallch" due to what you now see. (Too many problems with DE's)

---

### Post by again? on 2018-05-27
> **seekertom said:**
> Thanks, guber2. life progresses slowly for me these days, but I finally got back to the issue at hand, wallch. 

today i reinstalled 18.04, got it working and did the sudo thing. wallch was installed as you suggested, and acted pretty much like it did for me in 16.04, except it wont actually start the slideshow. I set up the path to my images, set up 10 sec interval etc, but clicking on start just gets me a dumb look. nothing happens.

As for which startup I follow, I now understand your question about wayland. thanks for that insight. I will continue to persuit my wallch, or hunt for another app that works like it and is compat w 18.04.. I guess I just like my pretty pictures!
thanks, st
Try double clicking on one of your images in wallch above the slideshow then hit the start button.

---

