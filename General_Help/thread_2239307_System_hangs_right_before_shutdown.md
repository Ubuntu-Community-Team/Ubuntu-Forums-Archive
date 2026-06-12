---
title: "System hangs right before shutdown"
date: 2014-08-13
forum: General Help
---

### Post by daGrevis on 2014-08-13
Whenever I request a shutdown, system hangs at the moment when Xubuntu logo is spinning. It happens when I try to shutdown it using GUI and it also happens when I execute **shutdown -P now**. I thought that i might be because of hybrid graphics [so I disabled discrete card]("http://askubuntu.com/questions/89205/how-to-permanently-switch-off-discrete-graphic-card"). It didn't help though.

Where should I look next? Any help much appreciated.

---

### Post by daGrevis on 2014-08-13
Maybe this can somehow help. [https://gist.github.com/2468487701e2762d36c8](https://gist.github.com/2468487701e2762d36c8)

---

### Post by daGrevis on 2014-08-15
I read that other people have experienced this issue with the same laptop I have &#8212; Lenovo Z570. The thing is that it's not always been Linux &#8212; people have had the issue on Windows too. So I assume it's some kind of hardware problem. Never the less, there might be a better workaround than to shutdown the computer by holding the shutdown button for several seconds.

I have gathered logs from **/var/log/syslog**, maybe there's something useful in them. [https://gist.github.com/anonymous/800fee31cce687c135b5](https://gist.github.com/anonymous/800fee31cce687c135b5)

---

### Post by daGrevis on 2014-11-07
Still relevant. Just did a full upgrade, but the problem remains.

---

### Post by daGrevis on 2015-04-22
Problem is still there.

---

### Post by dino99 on 2015-04-22
Syslog might help you find a possible reason. If not, then try with an other user account (create one for testing in case)

---

### Post by matt_symes on 2015-04-22
Hi

Boot to the grub menu, select your kernel and press the e key to edit the grub command line.

Edit the grub command line to change the init system to

```
init=/bin/bash
```

Press ctrl + x or F10 or whatever the key is to continue booting directly to the bash shell. This will bypass the init system.

When the system has booted to bash, type (no need for sudo)

```
shutdown -h now
```

or 

```
shutdown -P now
```

Does it shutdown and poweroff with either of the above commands ?

Kind regards

---

