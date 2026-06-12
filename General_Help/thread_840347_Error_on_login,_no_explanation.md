---
title: "Error on login, no explanation"
date: 2008-06-25
forum: General Help
---

### Post by Crypty on 2008-06-25
When I login to hardy, right after hitting enter after my password, I get a little window that simply says "Error" and has an "Ok" button. This also happens when I lock my screen and log back in: I type my password and hit enter, the word "error" pops up right after it says "checking" 

I don't know what causes this, or what this error causes, but I'd like to find out and get rid of it. Any help is appreciated.

---

### Post by Zulu-Zeffir on 2008-06-25
Take a look at your gdm logs to see if you can get any insight from there.

cat /var/log/gdm/:0.log (or whatever the most recent log is)

---

### Post by avtolle on 2008-06-25
When you get the error message, does it again ask you for your password? 

Something I've noticed, and this may not be on point to your problem, is that if I type in my user name and password too quickly, or my password too quickly when returning from a locked screen, I get an error. Fix is to type the password more slowly (for me).

---

### Post by Crypty on 2008-06-25
It doesn't seem to matter when or how fast I type it. 

Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: pam_lwidentity(gnome-screensaver:account): PAM config: global:krb5_ccache_type 'FILE'
Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: pam_lwidentity(gnome-screensaver:account): cannot contact daemon
Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: pam_lwidentity(gnome-screensaver:account): PAM config: global:krb5_ccache_type 'FILE'
Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: pam_lwidentity(gnome-screensaver:account): cannot contact daemon
Jun 25 10:51:33 steve-laptop gnome-screensaver-dialog: pam_lwidentity(gnome-screensaver:setcred): PAM config: global:krb5_ccache_type 'FILE'

---

