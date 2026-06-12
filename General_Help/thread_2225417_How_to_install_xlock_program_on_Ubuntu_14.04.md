---
title: "How to install xlock program on Ubuntu 14.04?"
date: 2014-05-21
forum: General Help
---

### Post by abcuser on 2014-05-21
Hi,
I have installed Ubuntu 14.04 Server with minimal install. I installed icewm desktop environment and I would like to install xlock program to lock the screen with password from terminal. I tried:
sudo apt-get install xlock
but I am getting error that xlock does not exists.

Searching the web and found out: [http://eklausmeier.wordpress.com/2014/04/26/installing-ubuntu-14-04-server-edition/](http://eklausmeier.wordpress.com/2014/04/26/installing-ubuntu-14-04-server-edition/) that "For some strange reasons Ubuntu 14.04 no longer provides xlock ... So I copied the binary from Ubuntu 12.04 to my private bin-directory."
I don't have older version of Ubuntu. How can I download/install xlock program on Ubuntu 14.04?

Is there any other terminal program to lock the screen with password?
Thanks

---

### Post by elmar-klausmeier on 2014-06-03
You find xlock in package xlockmore. This package can be downloaded at [http://packages.ubuntu.com/precise/xlockmore](http://packages.ubuntu.com/precise/xlockmore). Use "dpkg -x" to extract files out of a Debian package. An example usage (for extracting files out of a package) is given here:  [http://eklausmeier.wordpress.com/2014/05/30/installing-missing-debian-packages-for-google-chrome/](http://eklausmeier.wordpress.com/2014/05/30/installing-missing-debian-packages-for-google-chrome/).

There are other lock-screen programs, so xlock is not your sole option. I am used to xlock and wanted to stay with it.

---

### Post by abcuser on 2014-06-04
@elmar-klausmeier, I have downloaded amd64 from page you provided and installed the package with:
```
sudo dpkg -i <package_name>
```
and tried blank screen:
```
xlock -mode blank
```
and it properly starts screensaver and turns off monitors to save energy. But when unlocking the screen I get an error message: xlock: can not find font: -*-helvetica-medium-r-*-*-24-*-*-*-*-*-*, using fixed...
Now I have found out probably some font problem, so I changed the command to use fixed font:
```
xlock -mode blank -font fixed
```

The only problem I see now with 'xlock' is the reason it is not officially available in Ubuntu 14.04 and the reason is 'not secure'. I have read why xlock is no more in Ubuntu (removed from Debian), because it has some security problems that were not fixed for years. So remove insecure programs.

By the way I have also found out another screen locker:
```
sudo apt-get install gnome-screensaver
```
and to turn on screensaver:
```
gnome-screensaver-command -l
```
but the problem is this screen locker does not turn off monitor to save power and also save screen.

Is there any other tool that:
a) locks the screen (password needed to unlock),
b) turns off a monitor to save a power and screen itself,
c) in official repository or at least not declared as unsafe.

---

### Post by grumblebum2 on 2014-06-04
I have autostarted this script as a simple screenlocker in the past. Runs in the background.
It will notify of impending screen lock 10secs before the idle time is up(-time [COLOR="#808080"]<min>[/COLOR]).
Then uses xtrlock to password lock the screen and xset to turn off monitor.
```
#!/bin/bash
xautolock -notify 10 -notifier 'notify-send "Screen will lock in 10 seconds"' -time 5 -locker "xtrlock & xset dpms force suspend"
```

xautolock and xtrlock are in the ubuntu repos.
xset is contained in **x11-xserver-utils** which is installed by default.
May have to configure your own notifier for icewm or not use one.

Test the screen off command (could just use this with gnome-screensaver)...
```
xset dpms force suspend
```

Test xtrlock (will kill it after 30secs if password doesn't work)
```
xtrlock & sleep 30 && pkill xtrlock
```

---

### Post by elmar-klausmeier on 2014-06-05
@grumblebum2: Thanks grumblebum2 for these tips regarding xautolock and xtrlock. I found them very valuable.

@abcuser: You might want to try slock in package suckless-tools. It covers your requirements a)+b)+c). slock does not directly turn off the monitor, nor does xlock. I tested slock and found that the monitor went to standby after some minutes.

---

