---
title: "Automatic Software Updates"
date: 2014-05-18
forum: General Help
---

### Post by Romeu_Tristo on 2014-05-18
I'm using Lubuntu 14.04 and I've noticed that my Software Updater is not automaticaly telling me when there's new uptades to install, although I have it set to "Display Immediately" to any kind of updates and I also have the Update Notifier set to autostart.
If I manually run the Software Updater, it will find updates, but I would like it to tell me every time there's a new update. What can I do?
Thanks for any help.

---

### Post by claracc on 2014-05-18
I don't know for sure, but it seems there is a known bug in lubuntu 14.04 where nm-applet indicator don't start at login and automatic updates can be affected by the same bug:

```
[CODE]Network indicator on the panel may not start at login. You can start it manually by launching "nm-applet" in a terminal. Some others autostarted applications may also be affected (such as automatic updates). See 1308348 for the details and the ETA for the fix. To turn on nm-applet in autostart, follow these instructions It may need two reboots to fully wor
```[/CODE]

Here, [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348) you have discussion about problem and various workarounds.

---

### Post by vasa1 on 2014-05-18
See [http://ubuntuforums.org/showthread.php?t=2222325](http://ubuntuforums.org/showthread.php?t=2222325)
and [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007490.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007490.html)

---

