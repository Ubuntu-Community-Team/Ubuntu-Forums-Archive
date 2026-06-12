---
title: "Please Help"
date: 2006-12-05
forum: General Help
---

### Post by pgt on 2006-12-05
5 days in and still no hope for me.
Can't install edgy cause of black screen.

I got dapper running strong but i can't instal beryl xgl, i have tried nearly 30 times i followed every tutorial possible, most links broken, i have beryl downloaded to my desktop still i cant install it.

please someone helpppp im losing my mind over this bloddy thing...

too much time and effort spent ot give up

please helppp

---

### Post by RAOF on 2006-12-05
Black screen where?  When?  With the install CD?  With the live CD?  Have you tried dist-upgrading from Dapper to Edgy?  What colour hair does your dog have? :)

---

### Post by Shatrat on 2006-12-05
Do you get the black screen when booting from the edgy live CD or after the installation?
What kind of video card do you have?  
Some info on whether or not you have graphics drivers installed correctly would be useful, as well as what specific proglems youve been running into when trying to install beryl.

You mentioned downloading the beryl packages, but I think it might be wiser to install from a repository.

---

### Post by pgt on 2006-12-05
the graphic card is ati 9800xt
I have downloaded 8 cd's from all possible installs for my amd 64.

Dapper works, edgy gives me black screen in all 4 cd's either at the beginning of the install or just before the login after the installation.
I tried upgrading same thing happens.

I am fine not having edgy, but beryl is what i want.

P.s. my dogs colour is golden ;)

---

### Post by charlie. on 2006-12-05
Your title asks for help, so I'll help you.

Firstly, change your desktop background to match your dog's hair colour. You'll find that the better colour coordination of your entire life will ease your stress levels, allowing you to concentrate on the real issue: how to ask for help.

If you don't have a dog, go get one. Don't get a pure-breed though, get a REAL dog with character!

Now that you've earned some karma, here's how to ask your question:

Firstly, learn how to write a title. "Please help" is meaningless - nearly EVERY post is asking for help. You should probably say something about a black screen.

Now, think about things logically connected to a black screen - when and where.

When: most of us (me included) cannot really tell one black screen from the next. We could, however, tell the moment BEFORE the black screen from another pre-black-screen moment.

Where: What's your screen connected to? (Hint: ATI and nVidia make them)

You also need to have SOME idea of what's causing it. Examples might be "I hacked my xorg.conf and now it won't load" or "I installed Beryl".

Lastly, don't reply to this thread, it's doomed to either become a flame war or simply cease to exist. Start a new one with a real title and a real question.

---

### Post by Shatrat on 2006-12-05
When in doubt, it's ATIs fault.  They make really bad drivers.
Have you installed the proprietary ATI drivers?  There are plenty of how-tos around if you havent, and it is necessary to have a 3d desktop.
Run this in terminal and it will tell you if you have direct rendering.
```
glxinfo | grep rendering
```

---

### Post by RAOF on 2006-12-05
> **pgt said:**
> the graphic card is ati 9800xt
I have downloaded 8 cd's from all possible installs for my amd 64.

Dapper works, edgy gives me black screen in all 4 cd's either at the beginning of the install or just before the login after the installation.
I tried upgrading same thing happens.

I am fine not having edgy, but beryl is what i want.

P.s. my dogs colour is golden ;)

Those were using the Live/Install CD, presumably.  Not the Alternate install.

Anyway, it's probably the case that your graphics card doesn't play nicely with the ati driver on the live CD.  You should probably check out [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

---

