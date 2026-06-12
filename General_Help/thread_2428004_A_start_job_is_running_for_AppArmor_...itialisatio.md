---
title: "A start job is running for AppArmor ...itialisation (Xmin Xs / no limit)"
date: 2019-09-28
forum: General Help
---

### Post by hellsbells2 on 2019-09-28
I posted earlier about trouble I was having getting the keyboard to work properly. It seems this may have just been the first sign of a bigger problem.
I tried booting in recovery mode a couple of times, but it didn't solve my keyboard problem so I tried to boot into normal mode again. Now every time I try to boot it hangs on "A start job is running for AppArmor ...itialization (Xmin Xs / no limit)" and pretty much stays that way until I hold the power button to force a shutdown. Now I can't boot in either recovery mode or normal mode. 
Is my computer fried???

---

### Post by mc4man on 2019-09-28
Maybe try temporarily disabling apparmor and see if you can boot up. You wouldn't want to do so permanently but may be a chance to fix your issues.
You can do that either thru a tty after leaving grub or thru the recovery mode, commands would be the same.

For tty after leaving grub, before or during hang see if going Ctrl+Alt+F3  brings you to a console. If so log in with your user name & password
For recovery mode, 1st  use the fsck, when done you can then open the root prompt .

Commands are 
```
sudo systemctl stop apparmor
```
```
sudo systemctl disable apparmor
```
```
reboot
```

To (re)enable apparmor - 
```
sudo systemctl enable apparmor && sudo systemctl start apparmor
```

Reference pages
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

Maybe your keyboard issue is from xserver,  if getting back up see if you're on the release or hwe version, probably later
This will describe - 
```
sudo X -version
```

---

### Post by hellsbells2 on 2019-09-28
Many thanks for your reply mc4man, although you might have to simplify it even more if that's possible?
I've tried Ctl+Alt+F3 both while trying to boot in recovery and normal modes (before and during hang) and nothing seems to happen, it ends up stuck at the same point.
I don't know what fsck is or how to open a root prompt.
In the GRUB boot menu I do have the option to hit c to open a command line?

---

### Post by hellsbells2 on 2019-09-28
I have now found a solution to this on the AskUbuntu forum, in case anyone's having similar problems here's what worked:<br>https://askubuntu.com/a/1177335/1000446<br>Note the reboot still hung for about an hour the first time I tried this, but eventually got to the second boot menu and was able to disable AppArmor, after which I'm able to boot normally again :D <br>

---

