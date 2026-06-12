---
title: "Standard user is notified of updates every day, I want them to be notified never."
date: 2016-05-11
forum: General Help
---

### Post by unflavored on 2016-05-11
Ubuntu 16.04. These are the update settings.

Automatically check for updates: Daily
When there are security updates: Download and install automatically
When there are other updates: Display every two weeks

Despite the "every two weeks" setting, I get the pop up notification, in the upper right corner of the screen, every day that there are any updates, security or non-security.

Ideally I'd like to *never* get these notifications. Is that possible with some config file editing? If not, how can I get them every two weeks at most?

---

### Post by grahammechanical on 2016-05-11
Change the setting. There is a drop down menu. The settings are

Daily
Every two days
Weekly
Every fortnight
Never

Regards.

---

### Post by unflavored on 2016-05-11
> **grahammechanical said:**
> Change the setting. There is a drop down menu. The settings are

Daily
Every two days
Weekly
Every fortnight
Never

Regards.

Unfortunately, those are not the options available.  The only possible settings (from the GUI) for "When there are other updates:" are

Display immediately
Display weekly
Display every two weeks

---

### Post by unflavored on 2016-05-11
This seems to be a bug in gnome-software / Ubuntu Software. I created a [bug report.]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1580836")

---

### Post by vasa1 on 2016-05-12
> **unflavored said:**
> ...
Ideally I'd like to *never* get these notifications. Is that possible with some config file editing? ...
Not at all advisable but I have *pkill update-notifier* in my autostart [-X

---

### Post by deadflowr on 2016-05-12
Does this work anymore?
```
gsettings get com.ubuntu.update-notifier no-show-notifications
```
which will show as false, and
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```
should change it to true, meaning no show updates.
this can be applied to each users settings, individually.

---

### Post by ian-weisser on 2016-05-12
One option is to remove update-manager and update-notifier, and use unattended-upgrades instead.
U-m and u-n assume the human wants to be involved with the update/upgrade process. u-u assumes the opposite.

---

### Post by unflavored on 2016-05-12
> **deadflowr said:**
> Does this work anymore?
```
gsettings get com.ubuntu.update-notifier no-show-notifications
```
which will show as false, and
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```
should change it to true, meaning no show updates.
this can be applied to each users settings, individually.

This looks perfect. It turns out the problem I had was due to a bug in gnome-software, but I'll do this in addition to uninstalling gnome-software.

---

