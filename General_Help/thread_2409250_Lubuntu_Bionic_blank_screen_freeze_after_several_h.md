---
title: "Lubuntu Bionic blank screen freeze after several hours of idling"
date: 2018-12-30
forum: General Help
---

### Post by pjboro on 2018-12-30
Hi, everyone!

I have some problems with Lubuntu Bionic: after 5 or 10 hours of being idle, my Toshiba SATELLITE NB10t laptop freezes and I can't do anything: typing on the keyboard, using the touchpad or touchscreen has no visible effect. I can't change to the virtual console using ctrl+alt+fx. Recently I had some problems with my CPU and I think it may be related: a friend said it somehow freed from the socket; he put it there again and everything seems to be working apart from the freezing. System is up to date. I read the logs, but found nothing related: I'm not sure what to look for. Any tips will be appreciated.

I thought that the kernel disables USB to save power and does not wake it up, so I have something like this set up, but to no avail:
```

root@tosh:~# crontab -l
* * * * * bash /root/usb_wakeup.sh
root@tosh:~# cat /root/usb_wakeup.sh 
#!/bin/bash
tee /sys/bus/usb/devices/usb*/power/wakeup <<< 'enabled'
tee /sys/bus/usb/devices/usb*/power/control <<< 'on'

```

Things I didn't try, but I will the next time:
[LIST]
[*]plugging in external keyboard: I need to get a hold of one ;) 
[*]trying the BUSIER trick: this will tell if the kernels panics 
[/LIST]

I'm posting this, because diagnosing problems is usually easier with more experienced users' help: I'm counting on you, guys :)

PS I googled, but I'm not sure what tool should I use to test for hardware CPU problems. Recommendations?

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]pjboro[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115145"),

The first thing I would do is run a memory test just to make sure your RAM is fine.

Please follow the instructions [here]("https://help.ubuntu.com/community/MemoryTest") in order to do so.

Please report back once done.

---

