---
title: "kstartupconfig unable to run"
date: 2008-06-12
forum: General Help
---

### Post by xt828 on 2008-06-12
Hello

I've been running Kubuntu 8.04 AMD64 since it was released, and today when i rebooted it after installing a new HDD it refused to let me log in, giving me an error box talking about lstartupconfig being unable to run.  I asked for help in the Kubuntu IRC channel, and the people I spoke to there thought it to be a permissions issue.

I attempted to go in in recovery mode to run startx and check the user manager settings, but when I entered the command startx I was told that /usr/bin couldn't be found.  I then, after further consultation in IRC, went in to recovery mode and entered the command chown -R xt828:users /home/xt828 but was told that /home/xt828 couldn't be found.

I dual boot this machine with a Ubuntu AMD64 install, and have a seperate drive for /home/xt828 that is used by both Kubuntu and Ubuntu.  There are presently five physical disks attached to the system, following the configuration noted [here](http://paste.ubuntu.com/19662/).

I am at a loss as to what is wrong, and my knowledge of Linux is quite limited - any and all help would be greatly appreciated.

Thanks.

---

