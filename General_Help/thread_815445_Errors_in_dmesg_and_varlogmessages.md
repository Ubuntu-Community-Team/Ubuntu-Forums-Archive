---
title: "Errors in dmesg and /var/log/messages"
date: 2008-06-01
forum: General Help
---

### Post by civic_si on 2008-06-01
I am getting this continuously in my log files. Its irritating and from what I found by searching you have to remove setkeycodes e02a 256 from 
/usr/share/hotkey-setup/generic.hk but that file is empty on my machine.

So I ran  find . -type f | xargs grep 'e02a' |grep 'setkeycodes' in the /usr/share/hotkey-setup/ directory and it finds an instance of this in the atkbd.hk file but its commented out. 

Is there another way to get rid of this. I hate my log files filling up with crap.

---

### Post by civic_si on 2008-06-01
Here is the post that I found to fix this but as posted above it did not work.

[http://ubuntuforums.org/showthread.php?t=119499](http://ubuntuforums.org/showthread.php?t=119499)

---

### Post by civic_si on 2008-06-01
After a little more searching I found this.

[https://bugs.launchpad.net/ubuntu/+source/console-data/+bug/70317](https://bugs.launchpad.net/ubuntu/+source/console-data/+bug/70317)

It appears that my Microsoft wireless keyboard and mouse is the culprit. Which is irritating I like this keyboard and mouse.

---

