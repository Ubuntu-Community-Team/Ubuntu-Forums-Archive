---
title: "Can't click on anything and keyboard barely works..."
date: 2014-04-30
forum: General Help
---

### Post by altjx on 2014-04-30
I've been dual booting Ubuntu 14.04 and Windows 8.1 for about 14 hours now, and I've only had to switch back to Windows about two times for random things.

However, now that I've booted back up to my Ubuntu 14.04 installation, I've noticed that I literally can't click on anything most of the time.

For example, when I booted up just a moment ago, I was able to click on things such as Chrome, open up pidgin, etc. But then seconds later, my mouse clicks are no longer registering. I'm not quite sure what's causing the issue but this is the first time it started. 

The only recent system changes I've made was switched to another graphics card driver. And that was about 2 reboots ago. 

Anyone have any suggestions? This is very frustrating...

---

### Post by bapoumba on 2014-04-30
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
May be this bug (seen here too). ```
ibus-exit
``` works here, but you have to do it every time you log out/in or reboot.

If it fixes it for you too, you can subscribe to the bug and add yourself as affected.

---

