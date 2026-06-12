---
title: "Is .config/autostart gone in 14.04 and beyond?"
date: 2016-08-27
forum: General Help
---

### Post by lou6 on 2016-08-27
I was looking for a good place to put a small script that I need to run at login time and several forum posts suggested .config/autostart. I have a new install of Xubuntu 14.04.4 and that folder does not currently exist. Is that folder still used by the system and, if so, when exactly is it accessed in the startup process?

If this is not a good way to run my script I'm open to other suggestions...

---

### Post by TheFu on 2016-08-27
~/.profile  ???

[https://unix.stackexchange.com/questions/32599/auto-running-bash-script-on-login](https://unix.stackexchange.com/questions/32599/auto-running-bash-script-on-login)

---

### Post by lou6 on 2016-08-27
No ~/.profile folder on Xubuntu 14.04LTS either. Thanks for the link, though. I wish Xubuntu had (as Unity does) an autostart app - would make life easier.

EDIT: I'm really thick sometimes! It's right here...

[http://askubuntu.com/questions/746485/automatically-open-applications-at-start-up-in-xubuntu-14-04-lts](http://askubuntu.com/questions/746485/automatically-open-applications-at-start-up-in-xubuntu-14-04-lts)

I'm marking this thread as closed.

---

### Post by TheFu on 2016-08-27
~/.profile isn't a directory. It is a file.
You know, just because a directory doesn't exist that doesn't mean you can't make it and put stuff inside to use it.

---

