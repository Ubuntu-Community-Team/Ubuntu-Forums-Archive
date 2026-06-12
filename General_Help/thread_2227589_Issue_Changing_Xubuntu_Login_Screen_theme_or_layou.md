---
title: "Issue Changing Xubuntu Login Screen theme or layout"
date: 2014-06-03
forum: General Help
---

### Post by dolomite7922 on 2014-06-03
Good Evening

I just setup Xubuntu 14.04 for a public computer and I am using the guest account for everyone to log-in to use.  However it seems that its no where near intuitive at the login screen for guests to click that little arrow to reveal that there is a guest account that they would need to switch to in order to use the computer.  People aren't technically savvy enough at all to know how to do this and so to make things much easier for them is there a way to change the theme or layout so that both accounts could be displayed like it used to be in previous versions of ubuntu?  I have search and tried everything that I can think of and none of the old tutorials that I can find will work for Xubuntu 14.04 as everything has changed and is different.

Any assistance would be greatly appreciated

Gordon

---

### Post by Toz on 2014-06-03
Hello and welcome to the forums.

I don't think that's possible. See this [question and answer]("https://answers.launchpad.net/lightdm-gtk-greeter/+question/242410").

If everyone is going to be using the guest account to log in, one option would be to autologin as guest. To do so, add:
```
autologin-guest=true
```
...to /etc/lightdm/lightdm.conf.d/10-xubuntu.conf.

There is one issue with this, if you log out of the session you end up back at the login screen. A way to work around this can be to use the session-cleanup-script as noted [here]("http://unix.stackexchange.com/questions/68389/need-to-auto-login-after-logout-on-ubuntu"). This will auto-login in again as guest on every logout.

EDIT: Just poking around this set up (I'm looking to do something like this myself - a kiosk-like setup using the guest account) and find that if I'm constantly auto-re-loging in as guest, it makes it difficult to be able to login as my admin account. To get around this, from within the guest account, run:
```
dm-tool switch-to-user USERNAME
```
...where USERNAME is your system admin account. This will create another X session (usually on tty8) that you can log into and make admin changes.

---

