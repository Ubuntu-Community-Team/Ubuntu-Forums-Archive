---
title: "start upstart service before init.d service"
date: 2015-12-14
forum: General Help
---

### Post by romdisc on 2015-12-14
Hi,

I have an upstart service which starts on startup and a reverse proxy with apache which starts as init.d service.
when I reboot the system I get an error accessing the web page.
I need to restart my service manually then I get a positive response in the browser.

What shall I do to overcome this situation?

Cheers!

---

### Post by ian-weisser on 2015-12-14
Well, one way is to use Upstart (on 12.04 and 14.04) or systemd (on 15.04 and later) to control *both* services so you can easily sequence them.

One major reason distros moved away from sysvinit (/etc/init/d) was to improve your ability to control services in precisely this situation.

If you want some help learning how to create Upstart jobs to replace init.d scripts, start at [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

