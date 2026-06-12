---
title: "Installing Java on Ubuntu 7.04/Firefox 2.0"
date: 2007-05-20
forum: General Help
---

### Post by bdemers on 2007-05-20
I want to create a web page or 2 and an open source app called aptana.  Aptana reqires Java and so I installed jre 6.0 to /usr/share/java/jre6.0_01.  Firefox requires a manual install of java plugin and this is done by a link from the firefox plugin directory to the location of java. Firefox is at /usr/share/firefox.   Problem is, there wasn't a plugin directory for firefox, so I created one and then proceeded on from there. (there was a seachplugins directory however).  A checkbox inside of firefox preferences is used to enable java.

Naturally, I wouldn't be writing all this if it worked!  So what might I do to troubleshoot?  I might be wrong on rights.  May be wrong on plugin subdir name.  

If I can locate a firefox forum, I'll pose same question there.

Thanks

---

### Post by taurus on 2007-05-20
There is also a plugins and font for java from the repos.

```
sudo aptitude update
sudo aptitude install sun-java6-plugin sun-java6-font
```

---

### Post by bdemers on 2007-05-20
Well, That excites me.  Went to add/delete programs and searched for java, jre, j2se.  Nothing.  So So  now, to geneterate  aweb page I need to load aptana, which means I load java, which means I learn how to search!  I sheepishly ask for a phrase that will hook me up with the plugin and font as I am too darn stupid to find them by myself.

Thanks Taurus

---

### Post by bdemers on 2007-05-20
So, I found what you were talking about.  I learned howtosearch.  Thanks for the point.  I fearlessly move on!

---

### Post by pittly on 2007-06-18
I thought java was already installed in ubuntu 7.4?
If so how do I get java to work?
Newbee

---

