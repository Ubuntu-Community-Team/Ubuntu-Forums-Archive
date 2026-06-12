---
title: "Issue installing, removing, or...doing just about anything with programs."
date: 2013-12-31
forum: General Help
---

### Post by Karasawa7 on 2013-12-31
```
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'ttf-dejavu-extra' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


I tried to install wine, got this error.
I tried to remove java7 (Computer died during install, wanted to remove and try again), got this error.

I tried removing the package, didn't work. I tried re-installing the package and it too didn't work.

I'm not quite sure where to go with it at this point. Anyone have any ideas? What would you do if you saw this error. I'm kinda bad at troubleshooting errors like this haha.

P.S.
Ubuntu 12.04.

---

### Post by Tristan_Williams on 2013-12-31
Which version of Ubuntu are you running?
Also, (it's not directly related, just good to know) what is your kernel version? You can find out by typing the following command:
```
uname -r
```

---

### Post by Tristan_Williams on 2013-12-31
My firt suggestion would be to check your broken packages.

1. Open synaptic
2. Go to Custom Filters -> Broken

If anything shows up as "broken" do the following:
Go to edit -> Fix Broken Packages
Follow through with the prompt.

If the problem persists after that, refer to [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)
Reply #8 explains another way to (possibly) fix your issue.

I will add this:
I have ALWAYS had problems with anything java related ubder Ubuntu. This may not be the case for many people, but it has always given me problems.

---

### Post by Karasawa7 on 2013-12-31
3.8.0-34-generic

And I mentioned 12.04 up top but It was kinda hidden away :p

---

### Post by Karasawa7 on 2013-12-31
Also, I can't install the package manager....installing or removing ANY program it seems gives the same error message.

---

### Post by Tristan_Williams on 2013-12-31
I'm not sure how to help then. 3.8.0 is kinda outdated, although LTS releases tend to have outdated packages all around from what i've experienced.
Sorry that I can't be of more help. I would just backup anything I wanted to keep and do a fresh install... Maybe not the best idea for everyone though

---

### Post by Karasawa7 on 2013-12-31
But....it is a fresh install lol. And I want to try and reduce formats of my SSD as much as possible.

---

### Post by steeldriver on 2013-12-31
Those 'list' files are a PITA when they get corrupted - it *is* possible to rebuild them from the .deb file, see here for example --> [http://ubuntuforums.org/showthread.php?t=2193011&page=2&p=12875012#post12875012](http://ubuntuforums.org/showthread.php?t=2193011&page=2&p=12875012#post12875012)

If you no longer have the .deb file in your cache, you can download a copy from packages.ubuntu.com (or maybe try 'apt-get download ttf-dejavu-extra')

---

### Post by Karasawa7 on 2013-12-31
Ahh, I'll play around with this. This might be a bit above my head, but we'll find out.

Can't believe some dumb fonts are holding me up.

---

### Post by Karasawa7 on 2013-12-31
Holy crap that friggin worked.
I love you.

---

