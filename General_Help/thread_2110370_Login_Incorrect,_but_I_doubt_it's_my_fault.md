---
title: "Login Incorrect, but I doubt it's my fault?"
date: 2013-01-30
forum: General Help
---

### Post by TheNerdAL on 2013-01-30
Hello Ubuntu users! I am back on Ubuntu again after missing it so much, only to have troubles with this. 

So, I want to install the nVidia drivers, but I read that the previous way of installing them (The Additional Drivers Software) was not good anymore, so I'm trying to use the current method, seen here: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

Well, When i go into console mode, I think that's what it's called, I login but it says "Login Incorrect"

But how can that be? I typed my password in the Gnome-Terminal already and that worked. Are there different passwords for both? 

Is it my username that's the problem? I checked my Home Folder and it's "adrian" and I typed that in and it still doesn't work. 

Is this a bug? I need help. :(

Edit: Woah, old pic, old pic, that's an old pic. >_>

---

### Post by sudodus on 2013-01-30
Did you login as usual and then pressed something like
***ctrl + alt + F3***

to get to a text screen? In that case it should work to log in as you described:

type user name
press ENTER key
type password
press ENTER key

Do you have some special character in the password, that might be treated in different ways at the graphical log in screen and at the text screen?

---

### Post by TheNerdAL on 2013-01-30
I pressed alt+ctrl+f1 

And no, it's the same password I use for mostly everything. It also works when I run sudo commands. 

Why is that? Are there two different passwords? I just checked my username in Recovery mode. Should I change my password?

---

### Post by TheNerdAL on 2013-01-30
Well that's weird, I changed my password and it worked. Why is it that my original password worked in the gnome-terminal when running sudo commands, but not in the console?

---

### Post by sudodus on 2013-01-30
> **TheNerdAL said:**
> I pressed alt+ctrl+f1 

And no, it's the same password I use for mostly everything. It also works when I run sudo commands. 

Why is that? Are there two different passwords? I just checked my username in Recovery mode. Should I change my password?
I tested in my system, Ubuntu 12.04 with some other desktops installed too, and it works with the same user id and password. Could there be different keyboard settings, so that non-alphabetic characters reside of different keys? This could happen, if you set the keyboard in .bashrc, because there are different commands for text screens and graphic screens. 

> A quick fix for temporary changes in text screens (not x terminal windows)

```
sudo loadkeys se
sudo loadkeys us
```

but in x terminal windows

```
setxkbmap se
setxkbmap us
```


Edit: Anyway, I'm glad you 'fixed' the problem with a new password :-)

---

### Post by TheNerdAL on 2013-01-30
Got it working. Now I have one problem. How do I paste in the console? I don't want to type it all out.

---

### Post by sudodus on 2013-01-30
> **TheNerdAL said:**
> Got it working. Now I have one problem. How do I paste in the console? I don't want to type it all out.
Some text screens have the same cut and paste as gnome-terminal (for example Clonezilla), but I don't know a way to do it in Ubuntu's text screen. But you can use tab completion: type a few characters and then TAB.

---

### Post by TheNerdAL on 2013-01-30
Alrighty. Guess I gotta do it the long way. Thanks!

---

### Post by TheNerdAL on 2013-01-30
Welp, it happened again. Login is incorrect, but it worked last time. 

I'm having a problem like this: [http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10](http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10)

---

### Post by Frogs Hair on 2013-01-30
Additional drivers on 12.10 has moved to software sources > additional drivers. Excuse me if you knew this already.

---

### Post by TheNerdAL on 2013-01-30
> **Frogs Hair said:**
> Additional drivers on 12.10 has moved to software sources > additional drivers. Excuse me if you knew this already.

I read that i should install drivers some other way because it won't work like that.

---

### Post by grahammechanical on 2013-01-30
> **TheNerdAL said:**
> I read that i should install drivers some other way because it won't work like that.

Where did you read that? It is not said in the link that you provided. The problems that a lot of people have had over the last few months are due to faulty proprietary drivers.

When we do a fresh install and tick install Third Party Software the proprietary drivers are installed as well. Which is all very nice if those drivers do not break the install when we reboot. But not so nice when the driver is bugged. And that is the problem.

I install development versions for testing purposes. I never tick to install third party software. I install Restricted Extras after installation and I then use Additional Drivers to put in a proprietary driver. It is not the Additional Drivers utility that is causing the problems but the drivers themselves.

In 13.04 development version we have a choice of 8 drivers to select as a way of getting around this issue. I am using 13.04 right now and it worked fine with Nouveau, the open source driver but at the moment I am running with Nvidia-310 (proprietary, tested). I installed it through the Additional Drivers tab in Software Sources. No problem.

A few months ago in a fresh install of 12.10 I tried to get Nvidia-current (recommended) installed and it broke the desktop. Nouveau worked fine.

You may have been confused with Ubuntu no longer using Jockey to install video drivers.

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html")

Regards.

---

### Post by TheNerdAL on 2013-01-30
Yeah, that's it. I'm installing 12.04 because I'm frustrated. Thanks though.

---

