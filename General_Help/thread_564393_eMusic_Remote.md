---
title: "eMusic Remote"
date: 2007-10-01
forum: General Help
---

### Post by TheScrutinist on 2007-10-01
Hello. I'm relatively new to Ubuntu (and Linux), and I'm definitely coming from a Windows background. I'm pretty unfamiliar with working in the terminal, but I'm not completely averted to getting things done via command line.

Anyway, I'm trying to install the new eMusic download application, eMusic remote, and I've hit a roadblock. I've downloaded both the [.bin file and the archive](http://www.emusic.com/dlm/download.html), but I'm not exactly sure how to install either. Does anyone have any suggestions?

Thank you in advanced.

---

### Post by zacinaction on 2007-10-02
Hey there,

the .bin file is an executable installer program.  To use it:

1.  Type "sudo ./nameofthefile.bin" to run the .bin file.

2.  When the installer asks where to install  - A good place is in /usr/local/bin so that it doesn't get mixed in with stuff installed by apt and you'll know where it is.

3.  After installing, you'll want to make a link to the executable in /usr/bin - type ```
sudo ln /usr/local/bin/emusicremote/emusicremote /usr/bin/emusicremote
``` (provided you installed it in /usr/local/bin/

That should normally be it, but there is a bug in the installer - here's the work around:

4.  Run emusicremote as root - type ```
sudo emusicremote
``` then quit

5.  Type ```
sudo chown -R YOURUSERNAME ~/.emusic
```

Refer to [this post]("http://ubuntuforums.org/showthread.php?p=3416310#post3416310") if you have any more problems

---

### Post by wayne040576 on 2007-10-06
Been trying to get this thing working today. I tried both a home directory install and also tried it in /usr/local ...  both with the same result. The app crashes on startup. When I run from the command line it gives the following error:


INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

Looks like a problem with the jre plugin? It seems to be installed correctly though. Has anyone had this issue?

---

### Post by wayne040576 on 2007-10-06
I managed to get this working. So I thought I'd post the details in case anybody comes across the same issue. Seems there was a bug in firefox a while back that caused a crash in the jave plugin if the browser user agent string was too big (> 128 characters) It has been fixed in firefox but still seems to be present in the emusic app. 

I was able to get it to load if I hit the stop button before it loaded the emusic webpage. 

But it would crash if I tried to load any page that uses java. 

Doing some research, I came across this:

[https://launchpad.net/ubuntu/+source/galeon/+bug/3747](https://launchpad.net/ubuntu/+source/galeon/+bug/3747)

Using the info from this bug report I was able to check my user agent string in emusic remote by  typing the string javascript:navigator.userAgent.length into the browser bar. 
This returned a length of 135. 

I then just went into the config (typing about:config) into the browser bar and changed the size of general.useragent.extra.notfox (or any of the settings that make up the user agent string) so that the total size of the user agent string is less than 128. Now it works fine

---

