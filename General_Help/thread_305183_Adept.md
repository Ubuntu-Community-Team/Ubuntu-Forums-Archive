---
title: "Adept"
date: 2006-11-22
forum: General Help
---

### Post by phil1024 on 2006-11-22
Ok, so I ran Kubuntu from cd a few times, sometimes in adept it would have a category for games, sometimes it would not, it didn't make sense why... So tonight I finally was ready to install, installation completed with no errors but in adept there is no category for games. Why won't that show up?

I'm a total newbie to linux... so any help would be greatly appreciated!!! :)

---

### Post by aysiu on 2006-11-23
Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo aptitude update
aptitude search games
```

---

### Post by phil1024 on 2006-11-23
Here is what I god

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
cat: sudo: No such file or directory
cat: aptitude: No such file or directory
cat: update: No such file or directory
cat: aptitude: No such file or directory
cat: search: No such file or directory
cat: games: No such file or directory
philip@kde:~$

---

### Post by aysiu on 2006-11-23
Do you see all those # signs in your /etc/apt/sources.list?

It means you have no repositories enabled, which means there's nowhere for Adept to get the software from.

Paste this command in the terminal: ```
sudo nano -B /etc/apt/sources.list
``` Then remove all the # signs from lines beginning with *deb* or *deb-src*. Finally, save (Control-X, Y, Enter) and paste this final command in: ```
sudo aptitude update
```

---

