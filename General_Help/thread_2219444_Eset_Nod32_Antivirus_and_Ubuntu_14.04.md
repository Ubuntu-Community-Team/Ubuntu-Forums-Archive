---
title: "Eset Nod32 Antivirus and Ubuntu 14.04"
date: 2014-04-24
forum: General Help
---

### Post by alarik82 on 2014-04-24
I use linux installed on USB drive for Windows scanning, previously i have been using Mint 11 though to the current version 16 with Eset Nod32 Antivirus installed without much issues. 

Now i have been wanting to try Xubuntu 14.04 LTS but, after i install Eset and go to activate the product, it seems to go through the activation process, but fails to update and eventually says incorrect username or password, same thing happens if i try to activate a trial licence.

I have tried this on 2 separate installs of Xubuntu on USB and on 1 desktop with Ubuntu 14.04 LTS each having the same issue. I have also verified that the keys still works on another version of linux Mint.

To me it seems as though it may be a permissions problem which stops it from actually activating but i'm not too sure, has anyone else come across this problem?

---

### Post by alarik82 on 2014-04-29
This problem occurs on two fresh installs of Xubuntu 14.04 and two installs of Ubuntu 14.04 (one fresh and one upgrade from 13.10)

Run file, asks for "Run as Root" password. Enter password and click ok. Error message "su: Authentication failure"
Run file with sudo command in terminal and installer starts normally. install with defaults and enable detection of potentially unwanted programs. Restart pc.
Activate with username or Password only will return invalid username/password using a valid username password, trying to activate a trial version after entering information does not appear to do anything.

---

### Post by alarik82 on 2014-05-02
Finally worked it out, had to enable root user before installing [URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo

[https://forum.eset.com/topic/2363-eset-on-ubuntu-1404-and-xubuntu-1404/](https://forum.eset.com/topic/2363-eset-on-ubuntu-1404-and-xubuntu-1404/)
[/URL]

---

