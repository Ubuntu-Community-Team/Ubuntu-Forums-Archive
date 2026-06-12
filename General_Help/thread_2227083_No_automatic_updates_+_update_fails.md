---
title: "No automatic updates + update fails"
date: 2014-05-30
forum: General Help
---

### Post by Totolanio on 2014-05-30
Hello,

With Lubuntu 14.04, in one month I never seen any update prompt automatically showing up.
I didn't change anything, and used the iso to install it.

It's well set up, (default) saying it will automatically update every day.

Also I tried to update by clicking on the update thing in the menu and it ALWAYS fail to connect to the internet unless i click on "configuration" and change nothing and close the window and after that it says "new updates".


Can someone help me plz ?

---

### Post by bapoumba on 2014-05-30
There is a bug with autostart applications in lubuntu. You need to add update-notifier to Preferences > Default Applications > Autostart tab.
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118)

I cannot find the thread where we discussed this right now, will edit this post when I find it.

Edit : here [http://ubuntuforums.org/showthread.php?t=2222325](http://ubuntuforums.org/showthread.php?t=2222325)

---

### Post by Totolanio on 2014-06-02
> **bapoumba said:**
> There is a bug with autostart applications in lubuntu. You need to add update-notifier to Preferences > Default Applications > Autostart tab.
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118)

I cannot find the thread where we discussed this right now, will edit this post when I find it.

Edit : here [http://ubuntuforums.org/showthread.php?t=2222325](http://ubuntuforums.org/showthread.php?t=2222325)

It's already checked in the box below but I added "update-notifier" to manually start.

Do I have to add "nm-applet" too ?

(anyway thank you I'll reboot to see)

---

### Post by bapoumba on 2014-06-03
> **Totolanio said:**
> It's already checked in the box below but I added "update-notifier" to manually start.

Do I have to add "nm-applet" too ?

(anyway thank you I'll reboot to see)

Yes, you have to manually add update-notifier even though the box below is checked. Same here.

I also have the nm-applet because network manager would not auto start for me either, same for light-locker.

---

### Post by Totolanio on 2014-06-05
It works, thank you very much.

---

### Post by mörgæs on 2014-06-05
Good, please mark the thread 'solved'.

---

