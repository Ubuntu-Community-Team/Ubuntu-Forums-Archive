---
title: "lxappearance crash"
date: 2013-01-02
forum: General Help
---

### Post by alkalk on 2013-01-02
I ran lxappearance  as root using sudo, this caused my desktop to stop responding (although I was able to switch to other consoles using atrl+alt+f key)
Could anyone please tell me if anything can be done about this? Which logs, if any are likely to contain the cause of the crash?

---

### Post by Pjotr123 on 2013-01-02
lxappearance isn't supposed to be run as root, but simply by users to change their user preferences! Why on earth did you do that? :shock:

This alone may the cause of many problems. User settings may have become completely messed up, with an unhealthy mishmash of user permissions and root permissions.

I advise a clean reinstall:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by alkalk on 2013-01-02
The reason for running it as root was that it wasn't changing my gtk theme, how exactly could running lxappearance as root effect user permissions to the extent that a complete reinstallation is required?

---

### Post by dino99 on 2013-01-02
i also get it crashing each time im loggin, but i does not care much about it.

what you can try:

sudo dpkg-reconfigure lxappearance

and also look at your logs: /var/log/ & .xsession-errors inside your /home , maybe there is some usefull warnings/errors to dig & fix that issue

maybe creating a new user may help too (never tried)

---

### Post by Pjotr123 on 2013-01-02
> **alkalk said:**
> how exactly could running lxappearance as root effect user permissions to the extent that a complete reinstallation is required?

Your home folder contains your user settings. The permissions are set to your user. When you run lxappearance as root, you're likely to change permissions for settings files, to root instead of user. 

Same effect when you would, heaven forbid, run Firefox as root, but then you would "only" mess up Firefox permissions in your home folder. With lxappearance as root, the devastating effect on permissions is likely to be much wider, all over the desktop.

---

### Post by alkalk on 2013-01-02
> **Pjotr123 said:**
> Your home folder contains your user settings. The permissions are set to your user. When you run lxappearance as root, you're likely to change permissions for settings files, to root instead of user. 

Same effect when you would, heaven forbid, run Firefox as root, but then you would "only" mess up Firefox permissions in your home folder. With lxappearance as root, the devastating effect on permissions is likely to be much wider, all over the desktop.
What should I look for? File ownership?

> **dino99 said:**
> i also get it crashing each time im loggin, but i does not care much about it.

what you can try:

sudo dpkg-reconfigure lxappearance

and also look at your logs: /var/log/ & .xsession-errors inside your  /home , maybe there is some usefull warnings/errors to dig & fix  that issue

maybe creating a new user may help too (never tried)
Thanks.

---

