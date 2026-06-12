---
title: "Flash 9 causes Firefox to close"
date: 2007-04-26
forum: General Help
---

### Post by nemesisrobot on 2007-04-26
I've noticed that over the past couple of days, Firefox has been closing unexpectedly while i'm in the middle of watching a flash video.

I've tried adding the following to my firefoxrc file but it doesn't seem to be working
```
export XLIB_SKIP_ARGB_VISUALS=1
```

Are there any other solutions that I can try?

---

### Post by CocoAUS on 2007-04-26
I had this problem, as well.  I uninstalled all the Java stuff, restarted, and Firefox/Epiphany no longer crashed during Flash videos.

sudo aptitude remove sun-java6-jre sun-java6-plugin

---

### Post by angryfirelord on 2007-05-05
It's a strange error involving flash and java. I'm not sure why it crashes because under Debian, it never happens.

---

### Post by greenstar on 2007-05-16
I just confirmed a similar problem with other browsers on feisty. Same problem occurs when I install & use epiphany browser from the repos.

I also tested using a site that has java, not flash and both firefox & epiphany crashed there also.


Greenstar

Edit: Just noticed that epiphany is built upon firefox... Doh!!

---

