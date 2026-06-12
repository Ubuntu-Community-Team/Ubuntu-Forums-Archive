---
title: "Ubuntu won't load"
date: 2015-07-20
forum: General Help
---

### Post by nbulischeck on 2015-07-20
I can drop to Tty but every time I start ubuntu it stays on the purple screen with orange and white dots. Is there any log I can check for this or a known solution? I believe the last thing I did was a dist-upgrade. Can I revert that?

---

### Post by dino99 on 2015-07-20
when the boot start, you can hold the Esc key down to get the verbose boot comments and see where/when it really hang. This can be done also permanently by editing:
> sudo gedit /etc/default/grub and remove 'quiet splash' and then run: > sudo update-grub

and it should be usefull to know the ubuntu version you are using, and with which DE session (unity or gnome-shell or else) .
which is the graphic card used ?

---

### Post by nbulischeck on 2015-07-20
Will try that in a second. For the time being, i'm running Ubuntu 14.04, gnome-shell, gdm, with an NVIDIA® GeForceTM GTX 970M. Now starting it in recovery mode to try and fix it there.

---

### Post by nbulischeck on 2015-07-20
I can see it's hanging on "stopping start par bridge for notification of upstart job start/stop"

At one point I saw it say stopping lightdm bit I don't even have lightdm installed?

---

### Post by nbulischeck on 2015-07-20
I fixed it. I guess the dist-upgrade decided to remove gdm? Not a clue. Well I dropped to a command line. X started crashing, so I checked gdm and it says it wasn't even installed. I wouldn't have removed that so I have no clue. Either way, try running your dm for anyone else encountering this problem.

---

### Post by oldfred on 2015-07-20
Your 970 is a new Maxwell nVidia card.
There have been lots of issues and normally newest nVidia driver required. But if you install directly from nVidia, you have to in effect reinstall with every kernel update.
Most older cards can just use Ubuntu repository version of nVidia driver. But you can add a ppa so you get newest version automatically.
If you change method you use to install nVidia you must totally purge old install or you will get conflicts.
       sudo apt-get purge nvidia-*
            Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
Uninstall fixes
[URL="http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/"]http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/

      [/URL]
 Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)

    [       ]("http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/")
  open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014
Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[URL="http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896"]http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896
[/URL]
 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

[URL="http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896"]
[/URL]

    [URL="http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/"]
[/URL]

---

