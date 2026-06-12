---
title: "Prevent user to disable the screen lock or modify timeout settings"
date: 2013-11-12
forum: General Help
---

### Post by support2 on 2013-11-12
Hello together,

iam building a 12.04 LTS kickstart installation and want to prevent a user to disable or modify the lock screen or its settings/timeout.
After some research iam wondering that this kind of policy is not configurable somewere.

I have found a specification but this seems to be for the future/working state. [https://wiki.ubuntu.com/Specification/ConfigurationLockdown](https://wiki.ubuntu.com/Specification/ConfigurationLockdown)

Has someone made some experience with this kind of lockdown/policy stuff or have a solution/idea for achiving this?

thank you

Greetings,

---

### Post by support2 on 2013-11-15
Hi again,

the problem was solved by using dconf (dconf-tools) and editing gnome policy.

A good startup is the gnome documentation. But we had to make some more investigation for locking and making it work.

[https://wiki.gnome.org/dconf/SystemAdministrators](https://wiki.gnome.org/dconf/SystemAdministrators)
[https://help.gnome.org/admin/system-admin-guide/stable/](https://help.gnome.org/admin/system-admin-guide/stable/)
[https://help.gnome.org/admin/system-admin-guide/stable/screen-locking.html.en](https://help.gnome.org/admin/system-admin-guide/stable/screen-locking.html.en)

cat 00-screensaver
> 
[org/gnome/desktop/session]
# Set the lock time out to 180 seconds before the session is considered idle.
idle-delay=uint32 600

[org/gnome/desktop/screensaver]
# Set this to true to lock the screen when the screensaver activates
lock-enabled=true
# Set the lock timeout to 180 seconds after the screensaver has been activated
lock-delay=uint32 0
# Set this to TRUE to lock the screen when the system suspends
ubuntu-lock-on-suspend=true
# Set this to TRUE to activate the screensaver when the session is idle
idle-activation-enabled=true


cat screensaver
> 
# Lock desktop screensaver settings
/org/gnome/desktop/session/idle-delay
/org/gnome/desktop/screensaver/lock-enabled
/org/gnome/desktop/screensaver/lock-delay
/org/gnome/desktop/screensaver/ubuntu-lock-on-suspend
/org/gnome/desktop/screensaver/idle-activation-enabled


cat user 
> 
user-db:user
system-db:local


Script for automated change:
> 
#create a dconf profile
sudo mkdir -p /etc/dconf/profile
sudo cp -p user /etc/dconf/profile

#As root, create a local database for system-wide settings in /etc/dconf/db/local.d/00-screensaver
sudo mkdir -p /etc/dconf/db/local.d
sudo cp -p 00-screensaver /etc/dconf/db/local.d

#Override the user's setting and prevent the user from changing it in the /etc/dconf/db/local.d/locks/screensaver file
sudo mkdir /etc/dconf/db/local.d/locks/
sudo cp -p screensaver /etc/dconf/db/local.d/locks/

sudo chown -R root:root /etc/dconf/

sudo dconf update


Greetings,

---

