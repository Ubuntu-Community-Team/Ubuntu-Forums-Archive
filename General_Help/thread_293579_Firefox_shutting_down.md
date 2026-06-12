---
title: "Firefox shutting down"
date: 2006-11-05
forum: General Help
---

### Post by kevin82485 on 2006-11-05
Whenever I visit a site that uses Macromedia flash player, Firefox automatically shuts down on me.  If I try to revisit the site after I open Firefox again it shuts down.  Any suggestions?

---

### Post by taurus on 2006-11-05
Do you have flash install on your machine and what site is it anyway?

[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by kevin82485 on 2006-11-05
Firefox installed it for me, and it happens if I visit any site that uses macromedia such as yahoo.com

---

### Post by taurus on 2006-11-05
Fire up firefox and type in about:plugins to see what kind of plugins do you have and what version of flash you have, if you have it at all!  I don't have any problem opening Yahoo! since I have to check my e-mail there...

---

### Post by kevin82485 on 2006-11-05
where exactly do I type that?

---

### Post by taurus on 2006-11-05
In the address bar where you would normally type in an address if you want to visit a site, "about:plugins"!

p.s.  The smiling face should be a colon...

---

### Post by kevin82485 on 2006-11-05
when I type in what you said (how it should be typed in the address bar) it just takes me to about.com

---

### Post by nikhilk on 2006-11-05
You should type this in the address bar
```
about:plugins
```

---

### Post by taurus on 2006-11-05
It's "about colon (the two ., one above another) plugins" with no space in between...

---

### Post by kevin82485 on 2006-11-05
ok, sorry it worked now...it says I have Shockwave player and FutureSplash player and they are both enabled...what now?  It appears to be version 7.0 r68

---

### Post by taurus on 2006-11-05
Maybe the sites you visit requires flash version 9!!!  Do a search here and look for howto install flash 9 on your machine then...

---

### Post by kevin82485 on 2006-11-05
it still doesn't work...if I delete libflashplayer.so from ~/.mozilla/plugins, then firefox is able to visit yahoo.com or any site that uses flash player, but when I get the yellow drop-down bar, and install flash through that method, the installation doesn't work, and firefox shuts down anytime I visit a site using flash until I delete libflashplayer.so from ~/.mozilla/plugins

---

