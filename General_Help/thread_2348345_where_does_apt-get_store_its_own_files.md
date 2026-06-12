---
title: "where does apt-get store its own files?"
date: 2017-01-02
forum: General Help
---

### Post by Sentinel_Warren on 2017-01-02
[COLOR=#111111][FONT=Ubuntu]I was asking which file(s) should i back up first in case [/FONT][/COLOR]apt-get[COLOR=#111111][FONT=Ubuntu] database gets corrupted. Where exactly do apt-get store it's own files?
I want to do a backup of `apt-get` [/FONT][/COLOR][FONT=Ubuntu][COLOR=#111111]before doing something that might break it.[/COLOR][/FONT]

---

### Post by Keith_Helms on 2017-01-03
/var/cache/apt is where the packages you have installed go.  /etc/apt is where config and preferences go.

Why are you worried about the database getting corrupted?  Are you going to do "something that might break it"?

---

### Post by vasa1 on 2017-01-03
> **Keith_Helms said:**
> ... Are you going to do "something that might break it"?
[http://askubuntu.com/questions/867285/i-need-to-run-a-script-that-might-break-apt-get-what-should-i-copy-to-usb-firs](http://askubuntu.com/questions/867285/i-need-to-run-a-script-that-might-break-apt-get-what-should-i-copy-to-usb-firs) may offer a hint of intent.

---

### Post by Sentinel_Warren on 2017-01-03
Ok!i know that is where the packages installed by apt are located,the questions is about apt its self, thanks

---

### Post by Keith_Helms on 2017-01-03
I think it may be /var/lib/dpkg/status, but I wouldn't swear to it.

---

### Post by yetimon_64 on 2017-01-03
> **Keith_Helms said:**
> I think it may be /var/lib/dpkg/status, but I wouldn't swear to it.

I think you are pretty much right by a bit of reading on Unix and Linux Stack Exchange I just did :).  

@ OP, you may want to have a read of [[COLOR=#0000ff]--this link--[/COLOR]]("http://unix.stackexchange.com/questions/161866/how-to-recreate-var-lib-dpkg-status")

The question and first few answers look like they may be of use to your question here. 
It specifically mentions debian; I'm not sure on Ubuntu if dpkg is exactly the same or not, may pay for you to check that a bit further. 

Regards, yeti

---

### Post by Sentinel_Warren on 2017-01-03
Thanks @yetimon_64 and @Keith_Helms for some helpful hints.After going through [https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html) and [http://manpages.ubuntu.com/manpages/trusty/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/dpkg.1.html) i got very clear answers i needed to know!! without forgetting the stack exchange question ;)!

---

