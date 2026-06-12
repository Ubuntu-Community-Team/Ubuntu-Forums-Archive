---
title: "Ubuntu 8.04 LTS Occasionally Boots to Blank Screen"
date: 2008-06-07
forum: General Help
---

### Post by ethanklein on 2008-06-07
This is really starting to annoy me. Occasionally I start up my ML3109 Gateway Laptop it boots past the splash screen but then the login screen is just a blank screen. I've been hearing news about this problem occuring from various other forums and Im wondering will their be a fix or is there already a fix.

Laptop Specs
RAM: 2 GB
CPU: Celeron M 1.6ghz
GFX: ATI Radeon Xpress 200m
Harddrive: Seagate 80GB

-Please let me know if you find more information on this issue.
Thanks

---

### Post by ethanklein on 2008-06-07
Bump

---

### Post by ethanklein on 2008-06-07
Buuuuuuuuuuump

---

### Post by ethanklein on 2008-06-07
Anyone?

---

### Post by ethanklein on 2008-06-07
Lawl

---

### Post by ethanklein on 2008-06-07
help

---

### Post by ethanklein on 2008-06-07
Rawr!

---

### Post by Bubba64 on 2008-06-07
1st thing it is common courtesy to not bump in less than 24hr cycles. 2nd are you dual booting, I have never seen this problem in the 6 months of cruising this forum.

---

### Post by ethanklein on 2008-06-07
Sorry bout the bumping. I am not dual booting. Im seriously confused on what keeps happening. I hit ctrl+alt+f1 at splash screen and it appears everyting is booting correctly. I also have no greeting sound. IE: the drums.

---

### Post by Bubba64 on 2008-06-07
> **ethanklein said:**
> Sorry bout the bumping. I am not dual booting. Im seriously confused on what keeps happening. I hit ctrl+alt+f1 at splash screen and it appears everything is booting correctly. I also have no greeting sound. IE: the drums.

Since nobody has commented, although if you wait to bump when another time zone is going to see your thread you might get an answer. If it was me and I had nothing to lose on the computer I would probably do a daily alternative install. Does ctrl-alt-backspace bring up your login window, this is a way of shutting down the x and starting another desktop. Personally I have the stock Hardy and xubuntu installed and once in a while I want to use xubuntu and run this to get back to login. It is here that when I change desktops that I get a blank screen so I just run crtl-alt-backspace to get back to login and go for xubuntu which opens fine. It may be that you desktop portion is broken have you looked in synaptic in broken packages.

---

### Post by ethanklein on 2008-06-08
How do I look for broken packages? I'll try ctrl+alt+backspace.

---

### Post by ethanklein on 2008-06-08
Well that worked! Still I feel that 8.04 isnt stable enough. I initially started with 8.04 LTS how do I downgrde to 7.10 I've been hearing its more stable.

---

### Post by avtolle on 2008-06-08
The only way to downgrade is to do a fresh install of 7.10.

---

### Post by Bubba64 on 2008-06-08
> **ethanklein said:**
> How do I look for broken packages? I'll try ctrl+alt+backspace.

In synaptic is a section for broken packages.

---

### Post by ethanklein on 2008-06-08
Is their anyway I can downgrade to 7.10 without reformatting.

---

### Post by damispyderbyte on 2008-06-08
It's cuz the Radon 200 had same problem upgarded to geforce. The ait drivers are not great on some machines. On mine the ati 3D drivers wouldn't even work. Stick with nvidia. But it's a laptop so... theres not much u can do unless ATI fixes the drivers

Good Luck!!!

---

### Post by ethanklein on 2008-06-08
well compiz and everything works when I login. No lag in prformance. It just must be a glitch in the bootup. Good news is I havent had this problem for 6 boots so Im keeping my fingers crossed :0
thanks for everyone's input.

---

### Post by ethanklein on 2008-06-18
The latest Kernel 2.6.24-19 update fixed it! But now suspend doesn't work. Oh well. Hopefully Ibex will be what I've been searching for.

---

