---
title: "Is there a new bug in Evolution? Keeps prompting for calendar password"
date: 2014-08-02
forum: General Help
---

### Post by Rev2010 on 2014-08-02
Just recently, within the past week both my home Ubuntu machine and my Ubuntu machine at work are now prompting to enter my calendar password upon every login. It's absolutely maddening. First, it has my password already entered in the field. Second, doesn't matter if I click OK or Cancel my calendar still functions and synchs. I've tried deleting the keyring and recreating it, setting the blank password to unlock the keyring, deleting and recreating the calendar, uninstalling and reinstalling Evolution, adding Google in system settings -> online accounts, going to the Google disable captcha page, etc and nothing has worked. I'm speculating it must be a bug that occured with a recent update being it's happening on two completely separate machines. Can anyone confirm this?


Rev.

---

### Post by grier-devon on 2014-08-02
Go to /var/log/apt/history.log and look at what updates have been installed, if you have one for evolution or gnome keyring that I would file a bug report if one has not been filed yet.

---

