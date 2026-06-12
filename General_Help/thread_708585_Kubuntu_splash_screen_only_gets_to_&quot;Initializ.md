---
title: "Kubuntu splash screen only gets to &quot;Initializing system services&quot;"
date: 2008-02-26
forum: General Help
---

### Post by clk99 on 2008-02-26
I've been running Kubuntu for a while now and just allowed Adept package manager to update my system this morning, then rebooted.  I have it set to bypass the graphical login screen and automatically log me in, so everything seemed fine until I hung at "Initializing system services" on the splash screen for a few seconds then the screen went black for a couple more and I was sent back to the login screen after that.    If I try to log in again, the same thing happens.  

I'm pretty sure the only updates were some language packages, so I'm not sure how the update could have caused this.  The only other cause I can see is that I just installed Windows XP on another partition, but I was able to boot into Kubuntu yesterday even after installing Windows so that doesn't really make sense either.

Anyway, maybe someone can help me figure this one out.  Kubuntu is my main o/s so it's pretty important to me to fix it.  Thanks.

---

### Post by xeth_delta on 2008-02-26
Can you start in recovery mode? First check how much free disk space you have:
```
df -h
```
If you have enough space, then there might be an update problem, try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
```

---

### Post by dimethroxy on 2008-02-26
exact same problem here...

this happened after today update!

this is the THRID TIME an update broke my kubuntu...

are they even testing those damn updates?! i'm tired of that ****.

---

### Post by iPirates on 2008-02-26
yeah the exact same thing just happened to me :( except I was doing a fresh install of kubuntu, and updated the system... and now i can't get back in. :(

---

### Post by Crafty Kisses on 2008-02-26
> **iPirates said:**
> yeah the exact same thing just happened to me :( except I was doing a fresh install of kubuntu, and updated the system... and now i can't get back in. :(

One of my friends that use Kubuntu has the same problem, I'm sure the KDE team will release a patch fairly soon. :)

---

### Post by clk99 on 2008-02-26
> **xeth_delta said:**
> Can you start in recovery mode? First check how much free disk space you have:
```
df -h
```
If you have enough space, then there might be an update problem, try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
```

I tried this.  I do have plenty of free space, but the commands didn't help any.

---

### Post by xeth_delta on 2008-02-26
[EDIT] Before trying this, please have a look at posts starting from #8

This might be related: [http://kubuntuforums.net/forums/index.php?topic=3090771.0](http://kubuntuforums.net/forums/index.php?topic=3090771.0)
There might indeed be a file in "~/.kde" causing the crashes. If you are going to do anything to ".kde" I suggest that you make first a backup of it. After that you could try emtyiing the directories:
```
~/.kde/cache-<your hostname>
~/.kde/socket-<your hostname>
~/.kde/tmp-<your hostname>
```
and restarting

---

### Post by mgl on 2008-02-26
This problem has been discussed under desktop issues and relates to a bug in the new releases of the kde language packages. If you go to the login screen and change the default language for Canadian English to US english, the problem goes away (for now) Once they fix the problem in these new packages, you should be able to go back to your original language.

I did this change and everything works fine.

Good luck.

---

### Post by xeth_delta on 2008-02-26
mgl is most likely right. To the OP, please let me know if mgl's suggestion worked for you. That way I place a little note on my previous post telling people to go directly to his/her post.

---

### Post by tgilbert328 on 2008-02-26
Found this solution on another thread:

sudo apt-get remove language-pack-kde-en

and it worked.

Man, I nearly had a stroke when KDE wouldn't start this morning.  

Tim

---

### Post by Crafty Kisses on 2008-02-26
> **tgilbert328 said:**
> Found this solution on another thread:

sudo apt-get remove language-pack-kde-en

and it worked.

Man, I nearly had a stroke when KDE wouldn't start this morning.  

Tim

Nice, thanks for that. :)

---

### Post by clk99 on 2008-02-27
Thx.  That did the trick.

---

### Post by xeth_delta on 2008-02-27
> **clk99 said:**
> Thx.  That did the trick.

Great you found a solution. Please remember to mark the thread as solved.

---

### Post by iPirates on 2008-02-27
Yeah, I'm running KDE 4 as well, so I'm still able to log in with that, and removed the lang packages, and its all good.

---

