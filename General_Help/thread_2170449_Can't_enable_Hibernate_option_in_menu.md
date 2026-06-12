---
title: "Can't enable Hibernate option in menu"
date: 2013-08-26
forum: General Help
---

### Post by sgage on 2013-08-26
I'm running Ubuntu 13.04, all up to date. After testing my system with pm-hibernate (it worked perfectly), I created the policy file 'hibernate.pkla' in /var/lib/polkit-1/localauthority/50-local.d/ as described on several websites. Steill no hibernate item in the menu. Any ideas?

---

### Post by mc4man on 2013-08-26
Works ok here though instead of creating a new .pkla just edited the one where it's disabled by default.
```
sudo nano  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```
There are 2 overrides there, don't think the 2nd one matters much (logind) though wouldn't hurt to also enable

Otherwise it wouldn't show up if it didn't see an active swap or maybe active swap of a min. size? (your fstab is correct?

---

### Post by sgage on 2013-08-26
I tried your suggestion, but still no joy. I've got plenty of swap - actually a tinch more than my 4GB of RAM, and it is activated. Like I said, pm-hibernate works fine.

Strange. Any other ideas?

---

### Post by mc4man on 2013-08-26
Forgot that you likely are using gnome-shell which doesn't have hibernate available in the session menu.
Maybe an extension such as 
[https://extensions.gnome.org/extension/5/alternative-status-menu/](https://extensions.gnome.org/extension/5/alternative-status-menu/)

---

### Post by sgage on 2013-08-26
Indeed I'm using Gnome Shell, and I've tried Alternative Status Menu, which purports to put Suspend and Hibernate on the status menu. It puts Suspend there, but not Hibernate. Oh well, typing 'pm-hibernate' once or twice a week is not such a big deal ;-)

---

