---
title: "login is messed up help!"
date: 2007-09-02
forum: General Help
---

### Post by bam1234567 on 2007-09-02
Using ubuntu 7.04

Hi i enabled the "Enable Accessible Login" and screwed up my login. now when i went to the recovery mode and did
su alan
then press enter you are now logged in at the prompt as alan.
startx
it said x was already running... problem... type
sudo startx
enter your password
Now you should get to your desktop... go straight to that option you enabled and uncheck the box!
Subsequent logins should be back to normal.

But when i went to disable it it says GDM not enabled! so i went to the terminal and when i typed in "start gdm" it said Job: gdm not found.
What should i do????

---

### Post by por100pre1 on 2007-09-02
Try:

```
/etc/init.d/gdm start
```

---

### Post by banewman on 2007-09-02
According to this site - [http://library.gnome.org/users/gdm/stable/controlling.html.en](http://library.gnome.org/users/gdm/stable/controlling.html.en) - the command is gdm-restart.

---

### Post by bam1234567 on 2007-09-02
Thank You So Much!!!!!
you are going to heaven O:)

---

