---
title: "[SOLVED] Command to return to default, and to upgrade all packages?"
date: 2007-12-02
forum: General Help
---

### Post by TidusBlade on 2007-12-02
Okay I am kind of in a screwed up situation here :( Can anyone please tell me the command to upgrade ALL packages, and if it exists, a command to make Ubuntu return to default, like how everything was after installation of Ubuntu if you dont have the CD?
And I am using Dapper Drake.
Any help would be appreciated :)

---

### Post by MrFSL on 2007-12-02
> an anyone please tell me the command to upgrade ALL packages,

Sure:
```
sudo apt-get update
sudo apt-get upgrade
```

> a command to make Ubuntu return to default, like how everything was after installation of Ubuntu if you dont have the CD?

Sure again **IF and ONLY IF there is no application settings you need to save -- I.E. no bookmarks or emails etc.** -- You could accomplish this by deleting he configuration files in your home directory.

***_**Do Not Do This unless you are sure you understand what you are doing!!!!!!!!_*** 

1) Press Ctrl + Alt + F1 to drop to a terminal

2) Become root using: sudo su

3) Kill a good amount of services including X using: init 1

4) Remove all the hidden files and folders from your home folder. ***_AGAIN ONLY IF YOU KNOW WHAT YOU ARE DOING_*** This can be done by removing all the files that start with a "."

5) Copy the contents of the /etc/skel directory using: cp /etc/skel/* /home/username/

6) Change owner of all files in your home: chown -R username:groupname /home/username/

7) Restart machine: init 6

---

### Post by TidusBlade on 2007-12-02
Thanks! But when upgrading I get this:
```
root@89-149-240-61:~/test# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  rtorrent: Depends: libc6 (>= 2.6) but 2.3.6-0ubuntu20.5 is installed
            Depends: libcurl3 (>= 7.16.2-1) but it is not installed
            Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.0.3-1ubuntu5 is installed
            Depends: libkrb53 (>= 1.6.dfsg.1) but 1.4.3-5ubuntu0.6 is installed
            Depends: libssl0.9.8 (>= 0.9.8e-1) but 0.9.8a-7ubuntu0.5 is installed
            Depends: libstdc++6 (>= 4.2-20070516) but 4.0.3-1ubuntu5 is installed
            Depends: libtorrent10 but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by MrFSL on 2007-12-02
To easy looks like package management is broken so through a fix in the middle:

```
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade

```

---

### Post by TidusBlade on 2007-12-02
Thanks! Didnt really put it in the right place, upgraded correctly :)

---

