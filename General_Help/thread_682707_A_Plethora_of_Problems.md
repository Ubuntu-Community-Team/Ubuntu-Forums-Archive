---
title: "A Plethora of Problems"
date: 2008-01-30
forum: General Help
---

### Post by bla687 on 2008-01-30
So, I started my computer this morning, and I got this error message when Ubuntu started:

The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?

I didn't really think much of it, because it seemed like a pretty minor issue, so I picked an option and kept going. Shortly after I wanted to install a program which required installing fakeroot. When I typed sudo apt-get install fakeroot it told me it needed thu gutsy cd, so I put it in. I then realized that my cd drive wasn't working (I tried multiple other disks of other types just to be sure).  I then noticed that I only had two virtual desktops, because compiz-fusion was no longer running.

I'm sure all of these problems are somehow connected, but I don't know how. Last time my computer worked normally I installed qt4 and cmake, so maybe those could be causing something, though I don't know what, or why the problems wouldn't have occurred until the restart.

Any help would be greatly appreciated.

Thanks!

---

### Post by seventhc on 2008-01-30
I had a similar problem once, did you change anything recently?? I think when it happened to me I had changed the computer name and had used characters it didn't want me to use. I used them anyway and then everything went weird, I then changed the name back to the original name and it was fine. For me I think it was b/c of the special character I used.
Did you make any changes recently??

---

### Post by noodleboy on 2008-01-30
I had the same issues yesterday while I was trying to get my cintiq up and running. I wonder if it's related to one of the latest updates?
My computer experienced the US pc101 vs 105 keyboard problem, compiz fusion stopped running, and  when I tried to open nvidia-settings a warning popped up "you are not using the nvidia x driver". I have not yet tried to reconnect my old second monitor and see if I can get back into the nvidia settings.
Other than those things, it has been a fairly good experience running 64 bit Gutsy (other than lack of printer drivers and the odd attempt at force installing some 32 bit software).
Anyone have any thoughts?

Noodleboy.

---

### Post by Technophobia on 2008-01-30
I started to get this when I installed the latest ATI drivers. And I still get it every time I log on and all my hardware does work.

---

### Post by seventhc on 2008-01-30
you might try to reconfigure
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bla687 on 2008-01-30
Actually, I had just run this command:
    sudo dpkg-reconfigure -phigh xserver-xorg
to get my screensaver working correctly yesterday. This had somehow disabled my proprietary drivers, which in turn caused every other problem (How does not having a video card driver make the cd drive stop working?) After accidentally setting my monitor refresh rate out of range doing an xorg reconfigure and restoring my old conf file, it's doing great! I might not have noticed the driver was off if I hadn't run the reconfigure. Thanks!

---

