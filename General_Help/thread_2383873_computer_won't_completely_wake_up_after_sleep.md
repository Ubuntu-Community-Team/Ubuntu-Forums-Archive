---
title: "computer won't completely wake up after sleep"
date: 2018-01-30
forum: General Help
---

### Post by Buntu Bunny on 2018-01-30
Dell Inspiron 700m
Lubuntu 17.10 

Computer appears to wake up after I've been away for awhile, until I try to go online. Then it can't connect. When I try to restart, the logout screen tells me

> GDBus.Error: org.freedesktop.login1. Operation in Progress; There's already a shutdown or sleep operation in progress

It won't restart, it won't shutdown. I have no idea how to cancel whatever shutdown or sleep operation is in progress. If I choose "suspend" from the logout menu it suspends and won't wake up at all. 

I've made changes in Power Settings Manager, but it doesn't change anything. Nor does it matter if I'm connecting wireless or with an ethernet cable.

The only other clue I have is that the system suspends itself twice while booting: once at the splash screen and again while loading the desktop. I have to push the power button again to wake it up to resume to process.  

Any ideas what the problem is and how to correct it?

---

### Post by cruzer001 on 2018-01-30
Hello

I wonder if wifi power savings has anything to do with it.  The wifi has a sleep mode (3) to conserve power.  To shut off sleep mode it needs to be change to 2 (wifi.powersave = 2).
```

cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by Buntu Bunny on 2018-01-31
cruzer001, thank you! I will try this and let you know.

---

### Post by cruzer001 on 2018-01-31
I have spent some time googling this error, got many hits and came up with several suggestions, but few solutions  :(  Systemd made the most sense to me.

This is a tough one

[https://bbs.archlinux.org/viewtopic.php?id=204346](https://bbs.archlinux.org/viewtopic.php?id=204346)

[https://bbs.archlinux.org/viewtopic.php?id=181666](https://bbs.archlinux.org/viewtopic.php?id=181666)

---

### Post by Buntu Bunny on 2018-01-31
I spent some time researching as well, and it seems to be a fairly common problem, especially with various flavors of Ubuntu on laptops. Not all of the answers or solutions are terribly clear, however.

This site,[ https://www.debugpoint.com/2016/05/quick-fix-no-wireless-connection-after-sleep-suspend-in-ubuntu-16-04-xenial-xerus/]("https://www.debugpoint.com/2016/05/quick-fix-no-wireless-connection-after-sleep-suspend-in-ubuntu-16-04-xenial-xerus/"), has a "quick fix" code I thought I'd try, but today I haven't had the problem! Laptop wakes right up and behaves fine. I'm not going to say it's fixed yet, but it's certainly curious.

---

### Post by Buntu Bunny on 2018-02-04
I haven't had the original problem again until today, but once again I woke up the computer but couldn't get online. This is the code to that fixed it.

```
sudo service network-manager restart
```

Or at least it's a workaround rather than a cold restart.

---

### Post by cruzer001 on 2018-02-04
I had a quirk with network-manager in the past and I used the same fix, created a launcher and placed it in the panel.

):P

---

### Post by Buntu Bunny on 2018-02-04
What an excellent idea! Thanks cruzer001!

---

### Post by Buntu Bunny on 2018-02-14
This is an update. I thought my workaround was sufficient but have continued to have this problem and have continued to look for solutions. Apparently quite a few people have this problem with Ubuntu 17.10 because the question pops up in quite a few places around the internet. Finally found that it is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1740175"), so no quick and easy fix. Now it's up to the developers. If you are having this problem too and reading this thread in hopes of finding an answer, please follow the link and add yourself to the list.

---

