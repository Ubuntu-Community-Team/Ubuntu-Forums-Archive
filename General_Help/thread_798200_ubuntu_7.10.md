---
title: "ubuntu 7.10"
date: 2008-05-18
forum: General Help
---

### Post by AznPat on 2008-05-18
i m really new to ubuntu i just installed it this morning i got rid of my xp for it.so all i go is ubuntu.i had some problems and just wanted to get some advice from some people.when i boot up it stay in a black screen for a long time maybe like 5mins then it goes the sign on screen,is it possible to make it go faster?another question, is they're anyway i can make my font smaller when i login,bcoz the font is like really big i cant even see what i am typing..if anybody can help me i would nice..thank you

---

### Post by HunterThomson on 2008-05-18
Hum that is real strange?

What video card do you have? I hope someone that has had this problem before can help you.

---

### Post by tamoneya on 2008-05-18
There is a pretty in depth thread here: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491).  However I do not recommend you do this at the moment since it isnt recommened for a newbie.  It makes a nice read.  What you should do however is [http://ubuntuforums.org/showthread.php?t=531453](http://ubuntuforums.org/showthread.php?t=531453) look at post #3.```
sudo apt-get install bootchart
```Then post the chart here.  This will tell us what is going slowly and what we need to fix.

---

### Post by NightwishFan on 2008-05-18
Odd issues. Is your screen resolution correct? If not then go to System -> Administration -> Restricted Drivers Manager, and see if there is any to install.

---

### Post by empthollow on 2008-05-18
there is a bug in gutsy at boot that the splash screen wants to show at 1280x1024, if your monitor does not support this resolution it takes forever to get to the login screen.  the fix is to edit the file /etc/usplash.conf to look like this:
```
# Usplash configuration file
xres=800
yres=600

```
this will cause the splash screen to show and it will boot much faster.  As for the problem with the large text, see if it still persists after the boot fix, it may be part of the same problem.

---

### Post by AznPat on 2008-05-18
[http://var/log/bootchart]("http://var/log/bootchart")

---

### Post by tamoneya on 2008-05-18
you have to upload the file from your filesystem.  Upload it as an attachement.

---

### Post by ugm6hr on 2008-05-18
> **empthollow said:**
> there is a bug in gutsy at boot that the splash screen wants to show at 1280x1024, if your monitor does not support this resolution it takes forever to get to the login screen.  the fix is to edit the file /etc/usplash.conf to look like this:
```
# Usplash configuration file
xres=800
yres=600

```
this will cause the splash screen to show and it will boot much faster.  As for the problem with the large text, see if it still persists after the boot fix, it may be part of the same problem.

I agree this is the most likely problem.

See here to edit: [http://ubuntuforums.org/showpost.php?p=4218621&postcount=106](http://ubuntuforums.org/showpost.php?p=4218621&postcount=106)

---

