---
title: "Startup Applications Not Starting (14.04)"
date: 2014-11-04
forum: General Help
---

### Post by i4ybrid on 2014-11-04
I have a startup script to launch LeapCast when I log into Ubuntu. I'm trying to use the Startup Applications, I've also tried using ~/.profile, still no luck.
/home/user/LeapCast.sh
I've verified the script runs from command line fine if I run /home/i4ybrid/LeapCast.sh from anywhere


This works fine on another Ubuntu machine, so I assume I have a configuration wrong somewhere here. Any idea where I can start looking?

In the script is:
cd /home/user/Downloads/leapcast
leapcast --name IntelNUC --chrome /usr/bin/google-chrome --fullscreen


Thanks in advanced for any help!

---

### Post by Petro Dawg on 2014-11-05
You might try adding a delay using something like...

```
Sleep 10
```

before the rest of the script.  Sometimes commands get "lost" at start up as everything else is starting, adding a delay sometimes helps.

---

### Post by i4ybrid on 2014-11-05
> **Petro Dawg said:**
> You might try adding a delay using something like...

```
Sleep 10
```

before the rest of the script.  Sometimes commands get "lost" at start up as everything else is starting, adding a delay sometimes helps.


Hey Petro, thanks for the reply, but this didn't work. Would you happen to know what could block the normal startup process from happening? My rc.local, .profile are clear, and I've removed every other startup application from the Ubuntu UI configurator. If maybe another script is set up, but crashing, causing the rest of the scripts to fail to start? Any other place to look?

---

### Post by Petro Dawg on 2014-11-05
Sorry, you've hit the bottom of my well of knowledge.  Hopefully someone else can shine a light in another direction.  I've always been able to get my troublesome scripts to run by adding a delay.  Have you tried lengthing the delay time to 20 or 30 seconds and see if will work then?  Perhaps there is a dependancy that is taking a while to load :-?

---

### Post by papibe on 2014-11-05
Hi i4ybrid.

A few ideas:

Make sure the script has executing permissions:
```
chmod a+x /home/user/LeapCast.sh
```
Use absolute paths:
```
/home/user/Downloads/leapcast/leapcast --name IntelNUC --chrome /usr/bin/google-chrome --fullscreen
```
Add a redirection to a log file to see if you can get any error message:
```
/home/user/Downloads/leapcast/leapcast --name IntelNUC --chrome /usr/bin/google-chrome --fullscreen &> /path/to/file.log
```
Hope it helps. Let us know if that makes a difference.
Regards.

---

