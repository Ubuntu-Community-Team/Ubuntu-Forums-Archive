---
title: "Evolution hangs on startup with camel-exception error"
date: 2006-10-19
forum: General Help
---

### Post by willo8allthepies on 2006-10-19
Yesterday Evolution stopped completing the startup sequence.  It gets most of the way there, but freezes just after the new email count updates, sometimes after the email messages have appeared and sometimes not.

I tried restarting the app, then restarting Ubuntu.  Then I tried leaving it a day in case it automagically sorted itself out.  And today I tried all the above again.  I then tried reinstalling the application and its dependencies from synaptic.

This has made no change whatsoever.  I was considering doing an application remove and then reinstall, but I stupidly haven't backed up my emails and calender, which I assume will be deleted if I 'Remove' Evolution.

I then started the application from the terminal and got the following messages...

> CalDAV Eplugin starting up ...

(evolution-2.6:9239): evolution-mail-WARNING **: ignored this junk plugin: not e nabled or we have already loaded one

(evolution-2.6:9239): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed  to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:9239): camel-WARNING **: camel_exception_get_id called with NULL parameter.

Any ideas how I get Evolution back up and running anyone?

---

### Post by ramonthomas on 2006-12-05
I also have this problem. Evolution worked fine and now it just hangs. I must admit I'm new to Evolution and only been on Ubuntu a short while. I'm sure there is a work around but its pissing me off because I can see new emails were downloaded. It just does not want to display any of them.

cheers
Ramon

---

