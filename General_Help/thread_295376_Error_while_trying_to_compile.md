---
title: "Error while trying to compile"
date: 2006-11-08
forum: General Help
---

### Post by marianom on 2006-11-08
I'm trying to compile from source the newest version of "Mail Notification" ([http://www.nongnu.org/mailnotify/)](http://www.nongnu.org/mailnotify/)).

However:

```
mariano@mishima:~/downloads/mail-notification-3.0$ ./configure
... lots of code ....
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.8.20)
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... configure: error: unable to find the GNOME libraries

```

So I cannot continue due to that GNOME error. Can somebody suggest a workaround for it?

Thanks in advance

---

### Post by skunkydog on 2006-11-08
Did you try  ```
sudo apt-get install libgnome2-dev
```

---

### Post by wastrel on 2006-11-08
Use checkinstall to install your custom-compiled software:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by marianom on 2006-11-08
Hi, thanks for your replies.

skunkydog, yes,libgnome2-dev was already installed.

wastrel, looks interesting but the warning message really freaks me out. Do you consider it safe to try? What's your experience with it?

---

### Post by taurus on 2006-11-08
The error message only means that it can't find certain libraries to build the package from source.  There is nothing to be alarm about.  Just install whatever it needs and build it again.

---

### Post by marianom on 2006-11-08
Hi taurus. Thanks for your answer. 
I agree (I guess there might be path hardcoded in the script, I looked there with no luck).

The problem is that I'm pretty sure I installed every library required that I'm aware of (I used the repos version of this same package yesterday and it was installed without errors). Can't find which is missing.

---

### Post by marianom on 2006-11-08
Gotcha! libeel2-dev was missing. Installed.

---

