---
title: "Not being to login as root"
date: 2012-12-09
forum: General Help
---

### Post by Silvernail on 2012-12-09
Ubuntu 12.04
Gnome3
Chromium

I am confused about not being able to log on as root.
My applications menu has Software Center listed. I go there and can not install because I can not log on as root. I must goto a terminal and:
```
 sudo software-center
```

Doing a Google search and I find an appt I want to down load and install: Down load it, click on folder to open, am sent to software-center but can not install be cause I was not logged on as root.

I can not:
```
sudo chromium-browser
``` because chromium can not be run as root. I have quit using Firefox because it crashes so easily.

Is there something I missed when I set 'chromium' up? A preference maybe? What is the workaround if there is one.

Thanks.

---

### Post by lisati on 2012-12-09
I'm not sure why you would want to run your browser as root. You'd normally only use sudo as part of the installation process, not for actually starting the browser.

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by papibe on 2012-12-09
Hi Silvernail.

You don't need to log as root to install software. You only need to be an user with admin privileges.

Take a look at this [tutorial]("https://help.ubuntu.com/community/RootSudo") to see if it clarifies things a bit.

Let us know how it goes.
Regards.

---

