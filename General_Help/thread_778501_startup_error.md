---
title: "startup error"
date: 2008-05-02
forum: General Help
---

### Post by sunaruni on 2008-05-02
I've partitioned off a 30 gig area seperate from my Windows XP Home edition to install ubuntu. As it starts up, I get a message that says "failed to start x server. I enter to view details and it gives me this message:

failed to start x server
/etc/gdm/failsafe x server:
line 47:
[:too many arguments
Warning: could not retrieve EDID because get-edid is not installed (1)


Right now I'm running it off the disc, but I can't do that forever, obviously. Help me out? What can I do to fix this?

---

### Post by TeoBigusGeekus on 2008-05-02
Have you checked the integrity of the live cd before installing?

---

### Post by sunaruni on 2008-05-02
Yes, I have. It came up clear. Is there a way I can manually add the file to the registry from my disc?

---

### Post by TeoBigusGeekus on 2008-05-02
Boot into recovery mode and try
```
sudo apt-get install get-edit
```

EDIT:
I hope you have an internet connection...

---

### Post by sunaruni on 2008-05-02
Of course I have an internet connection.. how do you think I'm here?

I'll give that a shot, though, thanks.

---

### Post by sunaruni on 2008-05-02
No, after getting there, I remembered that I tried that already. Read it in another thread. It's not working. Still getting the "failed to start xserver" message.

---

### Post by sunaruni on 2008-05-02
*bump*

---

### Post by danwood76 on 2008-05-02
It could be that your graphics drivers arent installed/setup.
What graphics card do you have?
Which drivers are you using?

---

### Post by sunaruni on 2008-05-02
ATI Radeon x1600 Pro. How can I install the drivers for ubuntu to use?

---

### Post by TeoBigusGeekus on 2008-05-02
Try to type
```
sudo dkpg-reconfigure -phigh xserver-xorg
```

---

### Post by sunaruni on 2008-05-02
Tried that too.. Don't remember what happened, though. I'll do it again, and let you know what I get.

---

### Post by danwood76 on 2008-05-02
You may need to install the proprietry drivers if the free ones arent working.

```

sudo apt-get install xorg-driver-fglrx

```
you then need to set this up:
```

sudo aticonfig --initial -f

```

---

### Post by sunaruni on 2008-05-02
I'll give that one a shot. Thanks.


The other one gave me a dkpg-reconfigure command not found message.

---

### Post by TeoBigusGeekus on 2008-05-02
Sorry, mea culpa, etc. It should be
```
sudo [COLOR="Red"]dpkg[/COLOR]-reconfigure -phigh xserver-xorg
```

---

### Post by sunaruni on 2008-05-02
The install driver command seemed to work, but the second like, the aticonfig part, just said "this driver is not installed" and referred me back to type in the first command I already used. Let me go re-try that command with the typo fixed.

I swear, my hard drive is going to burn out with all this re-starting haha...

---

### Post by sunaruni on 2008-05-02
No, absolutely nothing has changed. It's like it's completely ignoring everything I enter in when it comes to ACTUALLY starting up. Might have to just get rid of it, if I can't get it. The partition has slowed down my XP quite a bit.

---

### Post by sunaruni on 2008-05-02
Anyone know anything yet? I'd really like to get this installed.

---

### Post by yuminig on 2008-08-14
maybe it wasn't install properly
try this, maybe it will reinstall

"sudo apt-get install xserver-xorg"

---

