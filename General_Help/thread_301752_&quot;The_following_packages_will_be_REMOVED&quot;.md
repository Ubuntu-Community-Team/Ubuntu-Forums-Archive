---
title: "&quot;The following packages will be REMOVED&quot;"
date: 2006-11-17
forum: General Help
---

### Post by EugeneK on 2006-11-17
apt-get dist-upgrade gives the following:

```
[b]The following packages will be REMOVED:
  initscripts startup-tasks system-services ubuntu-minimal upstart
upstart-compat-sysv upstart-logd[/b]
The following NEW packages will be installed:
  libdbus-1-2 libglitz1 libgnutls12 libtasn1-2
The following packages have been kept back:
  libgl1-mesa-dri
The following packages will be upgraded:
  gnome-main-menu
```
Going through with that list of removals wouldn't be a very good idea, right?

---

### Post by dbott67 on 2006-11-17
What are you upgrading to?  If you're going from Dapper to Edgy the [official method]("https://help.ubuntu.com/community/EdgyUpgrades") is:
```
gksu "update-manager -c"
```

-Dave

---

### Post by EugeneK on 2006-11-17
No, I've running Edgy already. Just dist-upgrading.

---

### Post by markuslaker on 2006-11-25
I had the same problem.  NoNo_231 provided the solution here: [http://www.ubuntuforums.org/showthread.php?t=294924]("http://www.ubuntuforums.org/showthread.php?t=294924").

As root, edit /etc/apt/sources.list and either remove or comment out (by prefixing it with '#') the line that looks like this:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

Now run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and the problem should be gone.

Markus

---

### Post by EugeneK on 2006-11-27
I'd already fixed it, but thanks anyway for dredging this up and trying to help me out. And yeah, that's basically what the problem was -- all the repositories in my sources.list were dapper, not edgy. Duh.

---

