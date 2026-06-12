---
title: "Automatic Reboot + Send Email?"
date: 2007-08-22
forum: General Help
---

### Post by jlacroix on 2007-08-22
I've never used Cron before, so I am not sure how to accomplish the following.

What I'd like my Ubuntu 7.04 box to do is automatically reboot every night at 03:00, and when it boots up I want it to automatically send me an email to let me know that it started.

This sounds easy to me but I've never messed with Cron. Also, if there is a good tool to automate tasks with cron rather than use the terminal, that would rock.

---

### Post by jlacroix on 2007-08-22
Sorry I figured out how to do the Cron thing.

All I need now is to set up an automatic email from sendmail or whatever.

---

### Post by bernied on 2007-08-22
I'm not sure what the mail command is, but add it to /etc/rc.local to make it run at startup. There are probably some very simple command line mail programs out there that would do the job - we used to use pine, but I don't know if it's still around.

I'm curious as to why you would want to reboot every day though - that's not very linuxish behaviour and should not be at all necessary.

---

### Post by jlacroix on 2007-08-23
Well I'm setting it up to install updates automatically, and Ubuntu usually asks to be restarted after being updated, hence the automated reboot.

---

