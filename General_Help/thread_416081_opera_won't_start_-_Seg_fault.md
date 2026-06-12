---
title: "opera won't start - Seg fault"
date: 2007-04-20
forum: General Help
---

### Post by jal on 2007-04-20
Opera will not start. 
It has been running (main browser), was running last time I shut down.
Rest of the system seems fine, I'm using Firefox to post now.

I get "Segmentation fault" when run from a command line, 
I re-installed Opera 9.10-20061214.6ubuntu1 using synaptic, Same symptoms.
/var/log/syslog shows me that I have a problem with gconf but I'm not sure if this is related.

Ubuntu version 2.6-15-28-386

some sample lines from syslog:
Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
GConf server is not in use, shutting down.

Some advice on resolving this please, and thank you.

---

### Post by jiminycricket on 2007-04-20
I think that segmentation fault was fixed a while ago...have you tried upgrading to 9.2?  Opera itself has a .deb repository for the latest version here: [http://www.opera.com/support/search/view/841/](http://www.opera.com/support/search/view/841/)

Or there was a hotfix for 9.1 too I believe [http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2](http://my.opera.com/desktopteam/blog/2007/04/07/hotfix-2)

---

### Post by id_sonic on 2007-04-20
9.20 is ok, becase it have hotfix allready, but 9.10 is not, I need 9.10 but 9.20, 9.20 is very slow for me!!!

help Opera! help us! help me!

---

### Post by jiminycricket on 2007-04-21
My 9.2 is really slow too.  Try following this post to see if it improves at all for you:

I found another (uncomfortable) solution: avoid flicker unset (works w/o restart) and tabs will be immediately created, downside: you'll get flicker and it's not faster anyway. But maybe that (double buffering) is the root of the problem.

[http://my.opera.com/community/forums/topic.dml?id=173674&abc=&page=2&skip=50&show=&perscreen=50](http://my.opera.com/community/forums/topic.dml?id=173674&abc=&page=2&skip=50&show=&perscreen=50)

---

### Post by jal on 2007-04-21
jiminycricket, thank you.
found and installed the deb for opera 9.2 and all is well.

---

