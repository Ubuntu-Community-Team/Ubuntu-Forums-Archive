---
title: "Unable to start update-manager (Python error: undefined symbol XML_SetHashSalt)"
date: 2012-12-12
forum: General Help
---

### Post by ChoneZone on 2012-12-12
Hello,

I upgraded to 12.10 recently, and am now experiencing problems with Software Updater. It flashes for a second then crashes. When I try running it from the command line (update-manager), I get the following error message:

/usr/bin/python3: symbol lookup error: /usr/bin/python3: undefined symbol: XML_SetHashSalt

I updated everything manually by way of apt-get update / upgrade, and I am still getting the same behavior.

---

### Post by ChoneZone on 2013-01-03
I think I found a solution to this after digging through these threads:
[https://bugzilla.redhat.com/show_bug.cgi?id=821337](https://bugzilla.redhat.com/show_bug.cgi?id=821337)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=665346](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=665346)
[https://bbs.archlinux.org/viewtopic.php?id=140916](https://bbs.archlinux.org/viewtopic.php?id=140916)

It seems that this is caused by library conflicts with libexpat. I did "ldd /usr/lib/python2.7/lib-dynload/pyexpat.so" and realized that my libexpat.so.1 was pointing to /usr/local/lib/libexpat.so.1 rather than /lib/x86_64-linux-gnu/libexpat.so.1 (the former referencing an outdated version, 1.5.2 instead of 1.6.0). I don't know where the libexpat in /usr/local/lib came from.

I hid my libexpat files in /usr/local/lib (renamed with .backup appended) and now running "ldd /usr/lib/python2.7/lib-dynload/pyexpat.so" displays the line "libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1" and update-manager works correctly.

I don't know very much at all about python or how these library dependencies work, so it's very possible that this clumsy fix might have broken something else, but so far so good.

---

### Post by ibjsb4 on 2013-01-03
Got some hits here

[http://www.google.com/search?client=ubuntu&channel=fs&q=symbol+lookup+error%3A+%2Fusr%2Fbin%2Fpython3%3A+undefined+symbol%3A+XML_SetHashSalt&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=symbol+lookup+error%3A+%2Fusr%2Fbin%2Fpython3%3A+undefined+symbol%3A+XML_SetHashSalt&ie=utf-8&oe=utf-8)

---

