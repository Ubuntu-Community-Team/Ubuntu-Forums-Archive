---
title: "This document cannot be displayed unless you install the Personal Security Manager"
date: 2008-06-05
forum: General Help
---

### Post by felixdzerzhinsky on 2008-06-05
This document cannot be displayed unless you install the Personal Security Manager

I am using Lotus Notes 8.5 on Ubuntu Hardy.

I am getting an error message when trying to get a twawte certificate from this URL:

[https://www.thawte.com/cgi/enroll/personal/step8.exe](https://www.thawte.com/cgi/enroll/personal/step8.exe)

This document cannot be displayed unless you install the Personal Security Manager (PSM). Download and install PSM and try again or contact your system administrator.


Since I am the sysadmin...sorta...what needs to be done. Is this an Ubuntu Issue or a Lotus issue?

What is the PSM?

---

### Post by Xiong Chiamiov on 2008-06-05
Try installing [the mozilla-psm package]("http://ubuntuforums.org/showthread.php?t=4416"):
```

sudo aptitude install mozilla-psm

```

As a side note, did you know that Mark Shuttleworth (the guy founded Canonical) has all the money to do this Ubuntu stuff because he started Thawte and sold it to Verisign?

---

### Post by felixdzerzhinsky on 2008-06-14
I am aware of Marks' background creating Thawte.

when I install > sudo aptitude install mozilla-psm it installs Seamonkey.

 >  seamonkey-browser seamonkey-gnome-support 

However Lotus Notes 8.5 is still borked. Does anybody know how to get PSM into Lotus Notes 8.5?

---

