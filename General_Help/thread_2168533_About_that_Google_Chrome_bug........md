---
title: "About that Google Chrome bug......."
date: 2013-08-18
forum: General Help
---

### Post by suomalainen on 2013-08-18
Users installing Google Chrome may find a file in their home folder that was created without their permission or knowledge named "libpeerconnection.log"

Attempting to delete this file will only result in it being recreated upon bootup.

Diverting it to a /tmp folder or similar may result in security issues.

See for example:


[https://code.google.com/p/chromium/issues/detail?id=239048](https://code.google.com/p/chromium/issues/detail?id=239048)

I have the same problem.I hope it can be solved soon.
My OS is Ubuntu 12.04 LTS
$ google-chrome --version
Google Chrome 28.0.1500.71
Maybe,'chflags hidden /libpeerconnection.log' is a good way.

 #37 pk...@google.com

The workaround specified here actually introduces a security vulnerability in multi-user systems if the file is not opened securely. (Think of the file existing as a symlink in /tmp.)


**[COLOR="#FF0000"]So how can this file be made to safely disappear from eyesite????[/COLOR]**

---

### Post by vasa1 on 2013-08-18
There's already a thread on this somewhere here.

---

### Post by ibjsb4 on 2013-08-18
> **[COLOR=#FF0000]So how can this file be made to safely disappear from eyesite????[/COLOR]**

[http://ubuntuforums.org/showthread.php?t=2155442&p=12696841&viewfull=1#post12696841](http://ubuntuforums.org/showthread.php?t=2155442&p=12696841&viewfull=1#post12696841)

---

### Post by suomalainen on 2013-08-18
Opened up gedit and copied the entire name of the file into a document named .hidden

The file .hidden was then saved in my home folder.

When I closed and opened the folder the .log file was gone....

Thanks for offering the link ibjsb4!

---

### Post by OrangeCrate on 2013-08-18
Or, just give it a bowl of water, and a little cat food, and leave it alone. It's not hurting anything, and Google or the Chromium folks will correct it with a near future update...

Edit:

Specifically, Chromium/Chrome 29, I read from the already posted link above.

---

