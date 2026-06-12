---
title: "Mod Ubuntu/Chromium to be kid-safe?"
date: 2012-12-10
forum: General Help
---

### Post by malenkylizards on 2012-12-10
Hey all,

This sucks. I wish I didn't have to do this, but our 13-year-old has repeatedly not shown good judgment with respect to internet usage, and I've decided it's time to take a more active role in policing internet usage.  I haven't found any off-the-shelf solutions that would really work, so I'd like to use my tools of the trade to keep an eye on her activities in a more creative way.

It's a laptop running 12.04 64-bit Ubuntu.

I gave her admin privileges at first, because my thinking went, if she broke her computer, she'd at least be learning some computer skills on the way, but it's obviously not a good idea right now; hopefully I'll be able to interest her in learning about computers in some other way.

Anyway, there are a few things I'd like to do. The first is making sure we can keep tabs on her.  I have a strategy, but don't know exactly how to carry it out.  I'd like to disable incognito mode in Chromium, for starters, and then I'd like to somehow copy her browser history off the computer periodically, maybe hour by hour.

I have not found any extensions or anything similar to disable incognito, so I'm thinking the next best thing is to somehow check to see if incognito is running, and then use pkill to close the whole browser.  So, I could have a script set to run on a crontab that repeatedly checks this.  I just don't know how to check.  Do you know if this can this be done?

As far as sending the history elsewhere, I can scp it to my home folder on my office's server.  The only problem is, I don't know exactly what I should copy.  It would be nice to get something I can look at in the same way one would look at chromium's own history page.  The other thing I could do is write a script that will just copy the history to another file ON her computer and just make sure she doesn't have write privileges.  Either way, do you know what that file would be?

I'm open to other suggestions about how to monitor her computer usage. I'm also open to being told this is the wrong forum for this sort of discussion. Just let me know where I should go instead!

---

### Post by jim_deadlock on 2012-12-10
Have you considered [http://www.opendns.com]("http://www.opendns.com")? It allows you to set up your home's router with built-in filters - many sites are already included but you can add your own as well. It would be a lot less work for you than constantly monitoring her.

---

### Post by lykwydchykyn on 2012-12-11
This can be a bit tricky to set up, and you may have to google around for all the steps, but basically I'd suggest this:

 - Configure a proxy (tinyproxy or squid, e.g.) on her system
 - Set up the proxy to log all requests (I think squid does this by default)
 - Use iptables to force all web traffic through the proxy
 - periodically scp the appropriate log to your server

If your daughter is very clever, you might also need to:

 - take away root privileges
 - lock down GRUB with a password
 - disable alternate boot devices and lock the BIOS with a password.

---

### Post by mastablasta on 2012-12-11
there is also gnome nanny: [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)
 
i am not sure if it does what you need it to do.

---

