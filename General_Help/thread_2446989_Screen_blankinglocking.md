---
title: "Screen blanking/locking"
date: 2020-07-10
forum: General Help
---

### Post by makem2 on 2020-07-10
I have a little annoyance which I cannot placate. I wonder if someone can assist?

My screen lock/blanking seems to have a mind of it's own. Using the Xfce Power Manager, I cannot set a time between 0 & 60 seconds after which the screen will blank. In my situation I am not concerned about it locking.

The best I can achieve is randomly between 4 min 40sec and just under 6 minutes when I set a time.

If I set it to 'Never' it does stay on in excess of 9 minutes at which point I use the machine as there is no point in having it run forever unless I have a manual way of turning off the screen should I need to leave for a while..

I most notice this annoyance when watching a movie/video and the screen keeps turning off, forcing my to log in again at the most interesting place!

```

makem@XPS-13-9300:~$ hostnamectl
   Static hostname: XPS-13-9300
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 3894274f52ad4021aacc66ef1e0062dd
           Boot ID: a02dd88876e24c1dbe9fb8c9cc952a16
  Operating System: Ubuntu 20.04 LTS
            Kernel: Linux 5.4.0-40-generic
      Architecture: x86-64
makem@XPS-13-9300:~$ 

```

I have tried:

```

makem@XPS-13-9300:~$ gsettings set org.gnome.desktop.session idle-delay <seconds> (0 to disable)

and

makem@XPS-13-9300:~$ gsettings set org.gnome.desktop.screensaver lock-enabled false

```

---

### Post by QIII on 2020-07-10
Hello!

Please use the default font and size when making posts unless you have some compelling reason to draw attention to a particular part of your post or to make some detail clear.

Thanks!

---

### Post by &amp;KyT$0P# on 2020-07-10
How have you configured Settings > Screensaver?  See my post in [this thread]("https://ubuntuforums.org/showthread.php?t=2443777").  If that doesn't resolve this, maybe one of the other suggestions in that thread will?

---

### Post by makem2 on 2020-07-10
Problem solved, thanks  				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=2034672"][B][COLOR=#000000]halogen2
[/COLOR][/B][/URL]
Apologies for the font, my eyesight is not brilliant and I forget to set it back to default.

---

