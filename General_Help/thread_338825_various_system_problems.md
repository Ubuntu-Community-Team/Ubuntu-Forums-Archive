---
title: "various system problems"
date: 2007-01-15
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-15
xgutsandgloryx@xgutsandgloryx:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
xgutsandgloryx@xgutsandgloryx:~$ sudo dpkg --configure -a
Password:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 21:
missing package name
xgutsandgloryx@xgutsandgloryx:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
xgutsandgloryx@xgutsandgloryx:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
xgutsandgloryx@xgutsandgloryx:~$ sudo su
root@xgutsandgloryx:/home/xgutsandgloryx# apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
root@xgutsandgloryx:/home/xgutsandgloryx#



help me! i'm having several system problems?

---

### Post by meng on 2007-01-15
Firstly, just try once more:
sudo apt-get update
sudo apt-get upgrade

If still getting errors, please post your sources.list

cat /etc/apt/sources.list

---

### Post by NeoLithium on 2007-01-15
You have to use sudo before apt-get commands:
```

sudo apt-get update

```

---

### Post by xGutsAndGloryx on 2007-01-15
> **meng said:**
> Firstly, just try once more:
sudo apt-get update
sudo apt-get upgrade

If still getting errors, please post your sources.list

cat /etc/apt/sources.list

i am trying to find a good list of reliable source.list



can you help me out?

---

### Post by ~LoKe on 2007-01-15
Your source list should be fine as is.

In addition to your /var/lig/dpkg/status, go back to your original thread and follow the last steps I mentioned, or just do this..

> sudo cp /var/lib/dpkg/status~ /var/lib/dpkg/status && sudo cp /var/lib/dpkg/status /var/lib/dpkg/status_back && sudo gedit /var/lib/dpkg/status
Remove ONLY the wpa_supplicant section.

---

