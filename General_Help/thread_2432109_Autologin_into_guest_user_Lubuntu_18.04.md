---
title: "Autologin into guest user Lubuntu 18.04"
date: 2019-11-27
forum: General Help
---

### Post by javier-carrillo on 2019-11-27
Is there a way to configure Lubuntu 18.04 to do auto login into a guest user? I have already tried editing some sddm config files with no success. I need this feature for a computer at a high school library.

UPDATE: Actually we are using Lubuntu 18.10.

---

### Post by TheFu on 2019-11-27
Support for 18.10 ended last July.  The system needs to be on an LTS, which means going back to 18.04.  The other option would be to install 19.10, which will lose support next July, but you'll have some months to move to 20.04 LTS after it is released in April.  19.10 has some protective features that would likely be good for a shared computer.
19.10 instructions: [https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en)
18.04 instructions: [https://help.ubuntu.com/lts/ubuntu-help/user-autologin.html.en](https://help.ubuntu.com/lts/ubuntu-help/user-autologin.html.en)

Guest logins had a number of security failures, so I believe they were removed.  However, you could have an account named "guest" that auto logs in, then setup some scripts to wipe it daily overnight or at login or at logout.  Leaving any files around between users is a security nightmare.

---

### Post by Impavidus on 2019-11-27
For a high school library you definitely want an LTS release. You don't want to upgrade twice a year, which would mean upgrading while the pupils are working on some project.

You could also consider creating a separate account for each of them, with a home directory on some file server. Then add a script that the admin (or the user) can run to reset all settings to some safe defaults, so the admin doesn't get called too often to fix a screwed-up user account.

---

### Post by javier-carrillo on 2019-11-28
I was unaware of the security issues. I will try the "guest" solution and wait for an update. Thanks for your answer.

---

### Post by TheFu on 2019-11-28
For a kiosk-type environment, heard on a linux podcast somewhere about this: [http://portal.altispeed.com/kb/faq.php?id=221](http://portal.altispeed.com/kb/faq.php?id=221)
I've not tried it and don't know how well it will work for you.  Think they use a ramdisk for the user HOME directory, so nothing really gets stored on disk.

You could setup a disk overlay using other tools like firejail, I would guess. I've not tried that.

---

