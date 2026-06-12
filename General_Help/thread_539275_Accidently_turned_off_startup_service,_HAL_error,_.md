---
title: "Accidently turned off startup service, HAL error, can't run administrative programs"
date: 2007-08-31
forum: General Help
---

### Post by scrapnon on 2007-08-31
Whoops! I was turning off printer start up services in the System->Administration->Services menu, when I accidently un-checked a service ( I think it was the one below the HP printing box. As soon as i unchecked it an error window popped up and said something about not having priveledges to run an administrative program (or something like that). Now When I log in (I have it set to automatic login) I get a HAL error, the network manager applet doesn't start, and I can't re-enable whichever service I turned off, But I can still browse files, play games and music, etc. Please help!

---

### Post by gtdaqua on 2007-08-31
run "rcconf" on command line to see what startup services have been disabled. You can enable/disable things here.

There is also another utility to find that out (not sure what is that - if anybody know pleas post - we can even set priorities or runlevels - not sure)

if rcconf is not installed, get it this way:

#sudo apt-get install rcconf

---

### Post by scrapnon on 2007-08-31
Thanks! I'll try that.

---

