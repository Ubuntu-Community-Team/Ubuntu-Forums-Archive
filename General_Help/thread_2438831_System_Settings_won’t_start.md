---
title: "System Settings won’t start"
date: 2020-03-18
forum: General Help
---

### Post by box02-0 on 2020-03-18
Hi.

I am no longer able to invoke “Settings” (gnome-control-center –overview)  or   “System Settings” (Gear with a wrench icon). When I select either, ubuntu 18.04 appears to be trying to start them, but gives up after 20 seconds or so.

I probably have caused this problem in my desperate effort to try to get the audio working – this on another post - , as they used to work. I wish I could be more specific as to what I did. All else appears to be working fine (except the audio).

Something else I noticed is that when I ShutDown, a trace appears with a slew of messages, one of which says: “Bad RIP Value    RIP: 0033:0x7f2d783bfe06”.

Any help would be greatly appreciated.
Thanks,
M….

---

### Post by lvm on 2020-03-19
When program is misbehaving a good idea is to start it from a terminal and check the output and check syslog.

---

### Post by box02-0 on 2020-03-19
I solved the problem by upgrading the nvidia driver : sudo apt install-nvidia-driver-430.

It is something like this which tells me how little I know. How can updating a video driver allow unity-control-center and gnome-control-center to start???

Thanks for the tip -  start these programs in terminal and see the error messages.
M...

---

