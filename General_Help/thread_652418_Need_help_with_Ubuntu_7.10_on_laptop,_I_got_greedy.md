---
title: "Need help with Ubuntu 7.10 on laptop, I got greedy and now have no graphics"
date: 2007-12-28
forum: General Help
---

### Post by pappy97 on 2007-12-28
I installed Ubuntu 7.10 (And turned it into Kubuntu) on my Toshiba laptop a few months ago without much problems.

But a few nights ago, I got greedy.  I have an HDTV that accepts PC input and when I hook up my Macbook Pro to it, it works great.  I can use the TV as a display.

I connected the Toshiba laptop while it was running to the PC input.  Nothing.

So I rebooted the laptop, at first I got a picture on the TV, but when it came to the login screen, nothing.  The TV didn't support the resolution being output.

Fine I thought.  I went into KDE and looked to see if I could change the resolution being outputted to the TV.

Couldn't find anything.  Then I found an option to make my TV the primary screen, the laptop the secondary screen.

Big mistake on my part.  When I did this, I still couldn't get the login screen the TV, so I disconnected the TV from the laptop.

Now on the laptop I get the text login screen and when I log in and try the command "startx,"  I get some "No screen found" error or something.

I realize that what I did in KDE screwed it up, but how do I get my laptop back to normal again.  I don't know what I need to do via text to fix it.  I don't care about the TV output anymore, I just want that laptop the way it was before, using it's own screen for graphics.  Thanks!

---

### Post by taurus on 2007-12-28
You just need to reconfigure your X server again.  Run this command from a prompt after you've logged in.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, see if X works.

```
startx
```

---

### Post by pappy97 on 2007-12-28
> **taurus said:**
> You just need to reconfigure your X server again.  Run this command from a prompt after you've logged in.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, see if X works.

```
startx
```

That worked perfectly, thanks!!!

---

### Post by solarwind on 2007-12-28
What's the -phigh option do? Just curious.

---

### Post by taurus on 2007-12-28
Reconfigure graphic card and monitor, leaving everything else untouch.

---

