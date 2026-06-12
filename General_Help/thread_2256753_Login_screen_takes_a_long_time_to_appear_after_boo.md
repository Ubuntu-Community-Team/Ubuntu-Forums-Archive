---
title: "Login screen takes a long time to appear after boot"
date: 2014-12-14
forum: General Help
---

### Post by billsmugs on 2014-12-14
I'm using Xubuntu 14.10. After a recent update the login screen (lightdm-greeter) takes a long time (around 1 minute) to appear after the computer boots, during which I simply get a blank screen. Once it appears, I can log in/out as normal and the problem doesn't occur again until I restart the computer.

During the blank screen phase (beginning a few seconds after selecting the OS to boot) I'm able to switch to a terminal with Ctrl+Alt+F1 and log in, which works, but prints the following errors:
```

[  102.765171] systemd-logind[1585]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[  102.765171] systemd-logind[1585]: Failed to start user service: Unknown unit: user@1000.service

```
If I run 
```
sudo service lightdm start
```
Then the display switches back to the GUI right away and I can log in as normal.

I did have some trouble with incorrect permissions on .Xauthority and .ICEauthority after the update (which I think occurred while reinstalling the latest Nvidia graphics drivers), so I wouldn't be surprised if this is an issue with file permissions somewhere, but if that's the case then it seems odd that the greeter does eventually appear if I wait long enough.

Thanks in advance for any assistance!

---

### Post by ibjsb4 on 2014-12-16
Sounds like this bug.

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)

---

### Post by billsmugs on 2014-12-16
That bug seems to date back to before I started using Xubuntu, but my issue only started after systemd was last updated (systemd-shim wasn't included in that update and was last updated at the start of November). Is it possible (and safe) to revert the updates to systemd features until a fix is released, to see if that prevents the issue? Or is there any way I can force a script to run at startup (to start the lightdm service - it would have to run as root or prompt for a password) separately from the current systemd/init services?

EDIT: I've set "service lightdm start" to run at startup using cron (with @reboot) and that brings up the login screen right away. Is there likely to be any downside to doing this? I'll try removing the cron job after the next update to see if it's fixed properly.

---

