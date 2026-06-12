---
title: "Extreme newbie; need help with terminal command"
date: 2007-07-15
forum: General Help
---

### Post by Rovdjur on 2007-07-15
So I have downloaded the source for Rocklight, the plugin for XMMS, and I do not know how to compile it or whatever to have it install as a plugin.

What is the command I use in Terminal to make it work? The README and TODO files do not tell me how to do it.

--->[Link of screenshot of source files]("http://pics.krasch.org/albums/userpics/rocklight.png").<---

---

### Post by Mr. C. on 2007-07-15
You need the build tools to build the source.  If you have not already installed them, do :

```
sudo apt-get install build-essentials
```

Then, in the rocklight directory, type:

```
sudo make install
```

MrC

---

### Post by kevinlyfellow on 2007-07-15
In the terminal cd into the directory
```
cd ~/Applikationer/rocklight-0.1
```
and then compile it
```
make
sudo make install
```

---

### Post by aysiu on 2007-07-15
*rocklight* is in the Universe repositories.

If you [have the Universe repositories enabled](http://psychocats.net/ubuntu/sources#simple), why not just paste this command into the terminal? ```
sudo apt-get update && sudo apt-get install rocklight
```

---

### Post by Rovdjur on 2007-07-15
Well, I tried to get the build essentials, and I got the error "Could not find packet build-essentials," so I just cd'd to the directory and tried to build it anyway, and got the error messages "Files or folders not found," among other things :-/

[Link to Terminal pic, though I do not think it will help]("http://pics.krasch.org/albums/userpics/terminal.png").

---

### Post by Rovdjur on 2007-07-15
> **aysiu said:**
> *rocklight* is in the Universe repositories.

If you [have the Universe repositories enabled](http://psychocats.net/ubuntu/sources#simple), why not just paste this command into the terminal? ```
sudo apt-get update && sudo apt-get install rocklight
```

Well nevermind my last post, that worked :D

Now I just need to figure out how to use XMMS and enable it in there :-P

---

### Post by Rovdjur on 2007-07-15
Ok, so Rocklight works, but only when I am logged in as root, not as a regular user.

Any suggestions? Maybe some permissions I need to set somewhere?

---

### Post by MRCeltic on 2007-12-25
Just curious did anyone figure out how to enable Rocklight for regular user's the only way i could find to get it to work was to open xmms from within terminal using sudo xmms

---

