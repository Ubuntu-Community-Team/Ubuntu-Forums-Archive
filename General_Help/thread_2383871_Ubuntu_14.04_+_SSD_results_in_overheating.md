---
title: "Ubuntu 14.04 + SSD results in overheating"
date: 2018-01-30
forum: General Help
---

### Post by SnuKies on 2018-01-30
Since I installed Ubuntu 14.04 LTS on my SSD, I've observed that my laptop is heating too much.
If before I could hardly hear the cooler while having Evince, Audacious and Mozzila opened, not it is spinning like crazy!

I did what Sergiy said [here]("https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version") and nothing.

My `/etc/fstab` looks like this: [https://pastebin.com/Z1sW2Txg](https://pastebin.com/Z1sW2Txg)

Also, I used `iotop` to scan for writings on disk and this is the result  [ATTACH=CONFIG]278389[/ATTACH]
(the gnome-shell process sometimes reaches 30% )

The temperature reaches +72C only with the above programs running.


What else should I do?

---

### Post by oldfred on 2018-01-31
Generally with desktops you do not need a separate /boot. It just becomes another partition you have to manage space on. When in / (root) the space is shared so only one partition to manage space on.

Your entries in fstab are not correct. I do not understand how you can even boot with those?
You do not use nodiratime as that is included if you use noatime.

But you cannot just add those as lines in fstab. You have to add parameters to each line/mount that you want those parameters to apply to.

This is my entry for /:

```
# / was on /dev/sda2 during installation
UUID=5c1e1a3f-261f-4da5-a0c2-8f479b3039de /               ext4    noatime,errors=remount-ro 0       1

```

Anytime you manually edit fstab, you run this and if no errors then it is ok. If errors you must fix before rebooting or it may not boot.
 sudo mount -a 

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

