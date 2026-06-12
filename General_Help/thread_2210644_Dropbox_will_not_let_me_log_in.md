---
title: "Dropbox will not let me log in"
date: 2014-03-11
forum: General Help
---

### Post by Zachary_Wolfgang on 2014-03-11
Hello,
I've tried many fixes for this issue including reinstalling dropbox and nautilus, purging the installations, etc.
I even installed a fresh copy of ubuntu and installed dropbox. In the tray it says it is connecting but I cannot put in my credentials or anything to log in to my account.

---

### Post by bapoumba on 2014-03-12
How did you install dropbox ?
Are you behind a proxy ?

---

### Post by Zachary_Wolfgang on 2014-03-12
I installed dropbox via the instructions on dropbox's website, and I am not behind a proxy.

---

### Post by bapoumba on 2014-03-12
Please **run dropbox** start from the terminal. Any errors ? It should bring you to the dropbox page to link your computer (you can alos do it from the dropbox site directly).
I installed it from the software center, which installs nautilus-dropbox and allows integration.

---

### Post by buzzingrobot on 2014-03-12
Have you been to the Dropbox site to see if your account is in order?

---

### Post by oxsyn on 2014-03-12
I am having this same issue on Ubuntu 14.04. I've installed several versions of dropbox all with the same outcome - unable to link account (the box is grayed out). It is not a problem with my dropbox account.

---

### Post by buzzingrobot on 2014-03-12
Not that it helps you, but I just installed using the deb from their site on 14.04. Everything went per normal. Not that long ago nautilus-dropbox from the repos never worked for me, but that has not been the case lately.

Have you tried the command-line install, posted at their site?

---

### Post by oxsyn on 2014-03-25
This issue seems to be resolved, installing dropbox from software center works as expected now.
While the issue was occurring, installing using the command line process did work for me, though the autostart command didn't work correctly and I had to bootstrap dropboxd manually.

---

