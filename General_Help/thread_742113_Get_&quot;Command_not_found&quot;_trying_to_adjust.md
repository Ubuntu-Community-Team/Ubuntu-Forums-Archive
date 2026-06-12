---
title: "Get &quot;Command not found&quot; trying to adjust date &amp; time"
date: 2008-04-01
forum: General Help
---

### Post by scottws on 2008-04-01
I wanted to enable syncing time to an NTP server on my Kubuntu 7.10 laptop.  I right click the clock on the desktop, and select "Adjust Date & Time."  KdeSudo pops up telling me to enter the root password.  I enter it and I am presented with the error (thrown by KdeSudo) "Command not found!"

I tried going into System Settings | Adjust Date & Time.  I can get there, but in order for me to actually change anything, I need to press the Administrator Mode button and when I do that, again I get the "Command not found!" error.

According to the KdeSudo login box, the command it wants to run as root is
```
/usr/bin/kcmshell kde-clock.desktop --lang en_US
```

If I run from a shell:

```
sudo /usr/bin/kcmshell kde-clock.desktop --lang en_US
```

...it works fine.

I'd be glad to look at what KdeSudo is trying to do and failing, but I can't seem to find any sort of log that will tell me.

I suppose this can be the result of me changing to the kdesudo_2.5-0ubuntu1_i386 package.  However, I've had that installed for a few weeks now and this is the first time I've run into any trouble whatsoever w/ KdeSudo.  I upgraded it because KMyFirewall doesn't work with the version of KdeSudo that's in the repositories for Kubuntu 7.10.

I suppose I can live with getting to the applet via the command line, but I'd much rather it work properly, so if anyone has any ideas, I'm all ears.

**Edit**:  Hmmm... I have just discovered that it's not limited to the Adjust Date & Time applet.  If I go to System Settings | System Services and try to enter Administrator Mode there, I have the same exact problem.  I wonder if it has something to do with the "ubuntu1" part of the kdesudo package I'm using.  If I remember correctly, the default kdesudo package had "ubuntu2" after it.

But strangely, so far these are the only places I've noticed the issue.  I've not had any trouble otherwise going into Adept or opening kate with the "kdesu kate" command from the command line.

---

### Post by scottws on 2008-05-08
Just wanted to check back in and say that upgrading to 8.04 solved this issue.

---

