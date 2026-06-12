---
title: "Ubuntu boots take too long"
date: 2020-03-26
forum: General Help
---

### Post by kaybee19 on 2020-03-26
Hey there, i just recently started using ubuntu so i dont know much about it.
But still my boot time for ubuntu is around 4 minutes and i know it should not be that much.
Im on a lenovo legion y540 with i5 9th gen and 8gb ram. The output for dmesg is as follows

paste.ubuntu.com/p/w6spctvfyb/plain/

sorry im new and dont know much about ubuntu and the forums :(

---

### Post by oldfred on 2020-03-26
Please post clickable links.
Is this correct link?
[http://paste.ubuntu.com/p/w6spctvfyb/](http://paste.ubuntu.com/p/w6spctvfyb/)

That is a log of your boot, you can see several longer times, but not familiar with any issues.

What brand/model system?
What flavor of Ubuntu? Version?

Issues often common across similar models by brand. May be similar?
Lenovo Legion Y530-15ICH
[https://ubuntuforums.org/showthread.php?t=2425907](https://ubuntuforums.org/showthread.php?t=2425907)
Lenovo Gamer Legion Y530
[https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675](https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)


Other threads on slow boot.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by HermanAB on 2020-03-26
Why boot?  Use Suspend.

---

### Post by webaake on 2020-03-26
Run the command (in terminal): ```
systemd-analyze blame
```

Another thing you can do is to disable the default boot screen and enable the old style boot with boot messages.

---

