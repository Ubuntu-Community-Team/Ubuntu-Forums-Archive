---
title: "Automatic Updates"
date: 2008-06-18
forum: General Help
---

### Post by keenboy on 2008-06-18
I have recently installed a network of 25 Kubuntu Edgy boxes for an organisation. I need to somehow keep these machines up to date automatically.

I have tried issuing the 'apt-get update && apt-get upgrade' command as a cron job however some users have their machines off at the times of this update taking place and some users are in and out of the office all of the time which means they could potentially power off their machine whilst it's updating etc etc.

The simplest thing to do would be to keep these boxes powered up. I have been told this cannot happen!

Is there a start up script of some description that could keep the machines up to date when they are powered on or a login script that takes care of it at login?

Any help would be appreciated.

Many Thanks

---

### Post by ibutho on 2008-06-18
Hi. Something like [anacron]("http://anacron.sourceforge.net/") may help. It should be available in the Ubuntu repositories.

---

