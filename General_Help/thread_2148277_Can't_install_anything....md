---
title: "Can't install anything..."
date: 2013-05-24
forum: General Help
---

### Post by 25tom on 2013-05-24
Hi,
I need to install some software on Xubuntu Quantal. As I'm relatively comfortable with the command line, I tried to use apt-get, but it returned an error. The software centre just hangs on a loading window when I open it. I have been able to install software before, but the last time I tried on this system was a while ago.

The error from apt-get:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


```

Also I want to install Google Earth; I have the .deb file from the Google Earth website, but I can't install it using either the software centre or dpkg, with similar errors returned.

Help? Thanks in advance...

---

### Post by ajgreeny on 2013-05-24
The commands ```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
sudo apt-get update
sudo apt-get upgrade
``` should help out here

---

### Post by 25tom on 2013-05-24
That threw up this error:

```
Reading package lists... Error!
W: GPG error: http://gb.archive.ubuntu.com quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.


```

What should I do? It seems to me that the problems lie with many if not all of the files in the /var/lib/apt/lists directory. Is it safe to delete all of them? And should I try to? And I don't know what the GPG error is at all...

EDIT: Software Updater just popped up with the same errors as in my first post and said that it was an 'unresolvable error'... I hope that it can be resolved somehow!

---

### Post by ajgreeny on 2013-05-24
I think you can remove all the list files in that folder and then run the update and upgrade command again.  Try
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by 25tom on 2013-05-26
That fixed it, thank you very much!

:)

---

