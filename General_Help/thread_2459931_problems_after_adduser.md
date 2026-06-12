---
title: "problems after adduser"
date: 2021-03-29
forum: General Help
---

### Post by coley9225 on 2021-03-29
I added a new user using terminal. I ran 'sudo adduser marilyn', and enter a password and other needed info. I then ran 'sudo usermod -aG sudo marilyn' to add her to the sudoers file. I loggged out and logged in on the new user to set up conf settings. The whole process seemed to go well, untill I logged back into my account. Any GUI app that requires a password no longer works. They either shut down after I enter my password, or say I'm not authorized to run said app. This applies to all apps, discover, gparted, timeshift, etc. I can run whatever I want from command line with sudo,but the GUI apps won't accept my password. Is this an easy fix or will I have to restore my last backup from terminal. Thanks in advance for any help.

---

### Post by GhX6GZMB on 2021-03-29
I don't know how often this has to be said:
DO NOT MIX CLI AND GUI WHEN DOING THIS KIND OF THING! Either 100% the one, or 100% the other.
Now you have the pain. I've no idea how to help you, sorry.

But at least you have a backup :)

---

### Post by coley9225 on 2021-03-29
I used cli to do all of the add user and grant sudo. I didn' add user in gui, then grant sudo with cli, I used cli for all. The problem is after the new user was added, I can no longer use any of the gui apps, I am forced to use cli now for those. A lot of them I can do with cli, but others I'm not yest familiar with enough to use cli, so I still use gui( like partition manager).

---

### Post by rsteinmetz70112 on 2021-03-29
Have you checked the files needed for a user to run /etc/passed /etc/group /etc/shadow and /home/marilyn? Make sure all of the right stuff is in there and with the correct permissions? 
Check the hidden files in /home/marilyn and make sure the ownership is correct, one common problem with setting up as sudo is that some of them get owned by root. Most of the time you can simply delete the hidden files and they will get recreated next time you log in.

---

### Post by guiverc on 2021-03-29
I will endevour to look at this a little later, it reminds me of [https://bugs.launchpad.net/ubuntu/+source/lxqt-policykit/+bug/1875774](https://bugs.launchpad.net/ubuntu/+source/lxqt-policykit/+bug/1875774) (raised after [https://discourse.lubuntu.me/t/no-authorization-after-adding-user/1033](https://discourse.lubuntu.me/t/no-authorization-after-adding-user/1033)) though that could not be re-created by users created at terminal so maybe it's another.

I'd look in /var/crash/ for crash files, also look at your logs (`dmesg` or `journalctl`) as I'd expect a crash message to tell you what program is having trouble (ie. crashing, like the `lxqt-policykit` of my paste); if for no other reason than giving more detail to look up history & fixes of others who've reported or explored the issue.

As I recall, I just used `vim` to edit (correct) files to resolve, but I can't recall what was wrong & thus what the issue was (*GID was set incorrectly by calamares but that was fixed*).  If you have a working account, contrast its settings with the non-working one (*I may have kept a working account on my box, or used a box besides the 'test' box I experimented on for comparisons*)

---

### Post by coley9225 on 2021-03-30
Thanks so much for all the tips. I have located( and fixed) the issue. After reading the bug report offered to me, I continued to research the issue. Apparently in lubuntu 20.04, having more than 1 user with sudo rights is a problem. I removed  marilyn from sudoers using 'sudo deluser mariln sudo' and now my gui apps work as before. Thanks again for the help. I'm marking this issue as solved.

---

