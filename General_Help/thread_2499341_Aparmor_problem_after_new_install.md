---
title: "Aparmor problem after new install"
date: 2024-07-23
forum: General Help
---

### Post by msknight on 2024-07-23
I had to create a new install and did 24.04 LTS.

I have the MySQL Worbench snap and in order for it to use network shares, I need to set aparmor to complain. However, I've got problems...

sudo aa-complain snap.mysql-workbench-community.mysql-workbench-community -d /var/lib/snapd/apparmor/profiles
...gives...
ERROR: Include file /var/lib/snapd/apparmor/profiles/tunables/global not found

Making a symlink and attempting...
sudo aa-complain snap.mysql-workbench-community.mysql-workbench-community
...gives...
ERROR: Path doesn't start with / or variable: "/var/snap/firefox/common/host-hunspell{,/}"

I've tried the usual internet searches and given myself a headache with older posts on older versions of snap, which have recommended all sorts including the obvious removing and reinstalling snap, which left me in a bit of a mess... but that's neither here or there. 

My version of snapd is 2.62.

At least I'm back to my original problem.

Grateful for any thoughts please.

---

### Post by currentshaft on 2024-07-23
What exact files did you symlink?

Why do you need to set apparmor to complain?

Do you need to use a snap for this, or can you use the native Linux package?

---

### Post by msknight on 2024-07-23
cd /etc/apparmor.d/
sudo cp /var/lib/snapd/apparmor/profiles/snap.mysql-workbench-community.mysql-workbench-community .

I need to put it into complain so that it can work on files that are on a network mapped share... otherwise aparmor stops it. It also stops others, like Leafpad, etc.

There is no candidate for the workbench in the repos, I beleive.

---

### Post by currentshaft on 2024-07-23
Try this symlink instead:

sudo ln -s /etc/apparmor.d/tunables/global /var/lib/snapd/apparmor/profiles/tunables/global

---

### Post by msknight on 2024-07-23
The directory "tunables" doesn't exist under profiles.

---

### Post by currentshaft on 2024-07-23
You might need to "sudo mkdir -p /var/lib/snapd/apparmor/profiles/tunables" first to create it.

---

### Post by #&amp;thj^% on 2024-07-23
> **msknight said:**
> 
There is no candidate for the workbench in the repos, I beleive.

You believe correct, but there is .deb version "mysql-workbench-community_8.0.38-1ubuntu24.04_amd64.deb"
Please continue with what currentshaft has suggested. Before I chime in.

---

### Post by msknight on 2024-07-23
Thank you for your help. Still hit a problem.

The folder was created - (I had read accounts of making that directory, then creating a file and copy/pasting content into it, but I held back from that)

  385  sudo ln -s /etc/apparmor.d/tunables/global /var/lib/snapd/apparmor/profiles/tunables/global
  386  sudo mkdir -p /var/lib/snapd/apparmor/profiles/tunables
  387  sudo ln -s /etc/apparmor.d/tunables/global /var/lib/snapd/apparmor/profiles/tunables/global
  388  cd /etc/apparmor.d/
  389  sudo cp /var/lib/snapd/apparmor/profiles/snap.mysql-workbench-community.mysql-workbench-community .
  390  sudo aa-complain snap.mysql-workbench-community.mysql-workbench-community

The result was...

ERROR: Path doesn't start with / or variable: "/var/snap/firefox/common/host-hunspell{,/}"

---

### Post by msknight on 2024-07-24
Removing firefox allows the complain to change. Putting firefox back in, causes the problem again.

Wondering where I go from here.

---

### Post by currentshaft on 2024-07-24
I recommend installing the non-snap version of Firefox. OMGUbuntu has a great article on how to do it.

---

### Post by msknight on 2024-07-24
Thanks. I'll do that.

---

