---
title: "Startup script to reset compiz scale plugin does not start reliably."
date: 2014-11-05
forum: General Help
---

### Post by monkeybrain20122 on 2014-11-05
OK, this is very frustrating. After some upgrades in Ubuntu 14.04 the hot corner for the scale plugin has stopped working on every reboot. It is an ongoing problem since 12.04 and there are numerous bug reports that affect a lot of people but they seem to be just forgotten. e.gs [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1305438](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1305438) [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/986208](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/986208) and  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845)

Since I am not holding my breath for a fix I am trying to use a bash script to disable and enable the hot corner at start up.

```
#!/bin/bash
#work around scale hot corner
sleep 10
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"Disabled"'
sleep 1
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"TopLeft"'
exit 0

```

I have made it executable and tested that it worked by clicking it and running it on the terminal.  I add it to startup applications but 8 out of 10 times it doesn't seem to execute on reboot. If boot up, log in and then log out and log in again it works. I am wondering if there is a way to make sure that it runs reliably at start up.

Thanks.

---

### Post by monkeybrain20122 on 2014-11-05
Ok, it seems that by increasing delay from 10 to 20 it works now. Since updates a few days ago desktop takes longer to load after login. I think this has to do with scale stops working.

---

### Post by monkeybrain20122 on 2014-11-07
Turns out sleep 12 would work reliably too. I can't figure out which upgrade has caused the corner to stop working but this workaround works quite seamlessly (much better than having a script to restart unity where all hell may break loose) I am marking this thread as solved.

---

### Post by CantankRus on 2014-11-08
I use a script to load conky after compiz is running because of different load
times between a boot and a logout/back in.
Maybe something like this...
```
#!/bin/bash

until (pidof compiz); do
	echo "waiting for compiz to load..."
    	sleep 2
done
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"TopLeft"'
exit 0
```

**PS** Don't seem to have the problem here. Up to date Trusty.

---

### Post by monkeybrain20122 on 2014-11-13
Epilogue: Following the updates today it seems that it is back to normal again: hot corner for scale works automatically at login without having to use the script and initial login time (from initial login screen after boot to loading of desktop) has noticeably sped up to what it was before.

These have been upgraded:


```

gir1.2-gudev-1.0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libgudev-1.0-0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libgudev-1.0-dev (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libpam-systemd (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-daemon0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-journal0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-login0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libudev-dev (204-5ubuntu20.7) to 204-5ubuntu20.8
libudev1 (204-5ubuntu20.7) to 204-5ubuntu20.8
libudev1:i386 (204-5ubuntu20.7) to 204-5ubuntu20.8
systemd-services (204-5ubuntu20.7) to 204-5ubuntu20.8
udev (204-5ubuntu20.7) to 204-5ubuntu20.8

```

So one or more of these was responsible for scale's hot corner not working and slow login I  experienced since a little more than a week ago, perhaps someone knowledgeable would have an idea about what was going on.

---

### Post by mc4man on 2014-11-22
I did notice this option in compiz I don't remember seeing before, disabled by default. Wonder what it does & maybe it could be helpful in not losing settings?

---

