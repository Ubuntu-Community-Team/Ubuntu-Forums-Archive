---
title: "Very long boot time on Ubuntu 20.04 LTS"
date: 2020-09-14
forum: General Help
---

### Post by linuxboi2 on 2020-09-14
&#65279;I have Ubuntu 20.04 running on an Acer Aspire 7. Everything works fine, except it boots up very slowly. Very rarely it will start in just a few seconds, but most of the time it takes over a minute. The OS is installed on an SSD and the system is quite powerful so there's no reason for it to take so long to start up.

I ran systemd-analyze and here are the results:
Startup finished in 1min 33.9s (firmware) + 4.1s (loader) + 2.5s (kernel) + 4.3s (userspace) = 1min 44.8s
graphical.target reached after 4.2s in userspace

Specifically, after turning on the laptop and before getting to the login screen I see: a blank screen for about 15-20 seconds, then only the Acer logo for over a minute and lastly the Acer logo with the text “Press Ctrl+C to cancel all filesystem checks in progress” + the Ubuntu logo in the bottom for just 2 seconds.

Any ideas what could be causing this?

---

### Post by ajgreeny on 2020-09-14
Sounds as if you may need to update the UEFI firmware, something I've never yet had to do so I'll  have to leave you to do your own search on that, and to read the computer manual, if you have one.

---

### Post by linuxboi2 on 2020-09-14
It's already the latest version

---

### Post by ajgreeny on 2020-09-14
Let's see a bit more detail of your startup with command ```
systemd-analyze blame
``` and we can try to move on from there.

Just another thought.
You do not say what sort of SSD or its make that you have but I believe that firmware for some of those needs to be updated and that will come from the manufacturer.

---

