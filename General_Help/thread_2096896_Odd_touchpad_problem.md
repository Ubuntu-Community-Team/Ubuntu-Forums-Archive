---
title: "Odd touchpad problem"
date: 2012-12-21
forum: General Help
---

### Post by Andorianmonami on 2012-12-21
Running Ubuntu 12.04 LTS
ASUS netbook acquired in ~March 2010

My touchpad doesn't work in my main administrator profile.  It works in guest mode, it works in another account, and I created a new profile to see if it worked there (it does), it's just this one profile.  A USB mouse works fine in the profile in question, just not the touchpad, which stopped working yesterday in the middle of using firefox.

---

### Post by slickymaster on 2012-12-21
Try this at a terminal window:

```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

---

### Post by Andorianmonami on 2012-12-21
That did it!  Thanks!  What happened there?  Any way I can avoid this in the future?

---

### Post by slickymaster on 2012-12-21
There's a bug report that reports this:

[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727"]Touchpad stops working after login
Ubuntu &#8220;xserver-xorg-input-synaptics&#8221; package Bugs Bug #549727[/URL]

One thing I forget to told you in my previous post is that to make it permanent include the last line of the code in **/etc/modprobe.d/options**

---

### Post by Andorianmonami on 2012-12-22
I'm not seeing any files called "options" in /etc/modprobe.d/.  Should I create one?

---

### Post by slickymaster on 2012-12-22
Apparently, that file has been judged obsolete and been removed. There's probably a file which does the same.

I'm attaching  an .sh file, and I changed 'sudo' to 'gksudo' so you'll get a graphical interface question for the root password instead of a commandline version. You can download it in your **/home** directory, and make it run every boot by going to System -> Preferences -> Startup Applications and click on 'Add'. Type anything in the name section, and type this command in the command section: ```
sh ~/workaround.sh
```

I don't know whether this works though. I don't have this bug, so I can't test it... _**And again, I'm reporting to the workaround for the bug, in Launchpad, mentioned in my previous post**_.

---

### Post by Andorianmonami on 2012-12-22
Thanks, I have since shut down the computer and rebooted it and run into the problem again, using the same fix you mentioned above.  I'll let you know if this works next time I shut down and start up again.

---

### Post by Andorianmonami on 2012-12-24
Doesn't seem to be working, oh well.  The command line fix still works.

---

### Post by Andorianmonami on 2012-12-24
Solved it!

Found a fix on a Debian wiki that I figured I'd try, and it worked! 

Created file with the following command:

options psmouse proto=imps

(options instead of sudo)

named it touchpad.conf and put it in /etc/modprobe.d/

Just shut down and powered up the laptop again, touchpad worked great.  Thanks again for your help!

---

