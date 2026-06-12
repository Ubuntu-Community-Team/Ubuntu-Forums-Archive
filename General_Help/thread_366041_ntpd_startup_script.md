---
title: "ntpd startup script"
date: 2007-02-20
forum: General Help
---

### Post by dibl on 2007-02-20
Kind Readers,

I've installed 6.10 and ntp-simple.  No startup script is included for /etc/init.d/

That seems odd to me.  Does anyone know where the startup script went?

-- David

---

### Post by grebo on 2007-02-21
Me, too! I tried ntp, then ntp-simple and ntpdate. None provided an init.d script. (Oddly enough, dpkg -L ntpdate includes "/etc/init.d" in the list.)

---

### Post by grebo on 2007-02-21
I just found bug 77506: [https://launchpad.net/bugs/77506](https://launchpad.net/bugs/77506)

Doesn't seem to have received the attention it deserves!

---

### Post by Sodki on 2007-02-21
This problem is a bit tricky... apparently, ntpdate runs on every boot, by default. The script that makes ntpdate run is:

/etc/network/if-up.d/ntpdate

That script runs every time a network interface is brought up. This means that, if you have Internet access while booting up, ntpdate will set your clock. You can check that for yourselves, just try setting your clock wrong and then do this:

/etc/init.d/networking restart

See? Now your clock has the correct time. But why doesn't this seem to work while booting up? I've messed around with the ntpdate initialization script and changed it so that it would write to a file the output of the "date" command right before and right after the setting of the clock by ntpdate. I've then set a wrong date in my computer (12/12/12) and rebooted. Surprise, surprise, check this out:

Wed Dec 12 12:26:45 WET 2007
Wed Feb 21 22:23:12 WET 2007

So ntpdate *does* set the clock right on boot time! The problem is that *something* changes it back to the wrong date afterwards!

---

### Post by grebo on 2007-02-22
Gave up on just ntp-simple. Based on [http://www.edafe.org/ubuntu/index.html#ntp](http://www.edafe.org/ubuntu/index.html#ntp) I decided to install this:

apt-get install ntp ntpdate ntp-server ntp-doc

*This* got me /etc/init.d/ntp-server. I'm happy now.

---

### Post by Sodki on 2007-02-22
> **grebo said:**
> Gave up on just ntp-simple. Based on [http://www.edafe.org/ubuntu/index.html#ntp](http://www.edafe.org/ubuntu/index.html#ntp) I decided to install this:

apt-get install ntp ntpdate ntp-server ntp-doc

*This* got me /etc/init.d/ntp-server. I'm happy now.
The problem is that ntp-server does not set the clock if the discrepancy is too high.

Check out this thread: [http://ubuntuforums.org/showthread.php?p=2175763](http://ubuntuforums.org/showthread.php?p=2175763)

Apparently, hwclock needs to be called before ntpdate, otherwise it reverts the time change.

---

### Post by bw44 on 2007-12-11
No ntp applications were installed by default on my gutsy system.

I installed ntpdate and it works fine from the command line. I would like it to run at boot-up and set the time.  (I'm planning to move to a laptop, so I don't want the ntp daemon running all the time when there's no network connection.)

Sodki said in a previous post:> ... apparently, ntpdate runs on every boot, by default. The script that makes ntpdate run is:

/etc/network/if-up.d/ntpdate

That script runs every time a network interface is brought up. This means that, if you have Internet access while booting up, ntpdate will set your clock.

It may run, but I don't think ntpdate is successfully updating my system clock at boot-up.  There **is** an /etc/network/if-up.d/ntpdate script on my system, but I still don't know whether it's run at boot time, and if not how to insure it is run and run after hwclock.  The answer may already have been given, but I didn't understand it.

Thanks for any help anyone can give me.

---

### Post by bw44 on 2007-12-14
> **bw44 said:**
> I installed ntpdate and it works fine from the command line. I would like it to run at boot-up and set the time . . . It may run, but I don't think ntpdate is successfully updating my system clock at boot-up. . . . The answer may already have been given, but I didn't understand it. . 
The answer I needed was on the UbuntuTime Community Documentaion page [https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff](https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff)
where it says:
```
Command Line ntpdate

Ubuntu comes with ntpdate as standard, and will run it once at boot time to set up your time
according to Ubuntu's NTP server. However, a system's clock is likely to drift considerably
between reboots if the time between reboots is long. In that case it makes sense to correct
the time occasionally. The easiest way to do this is to get cron to run it every day. With
your favorite editor, create a file /etc/cron.daily/ntpdate containing:

sudo ntpdate ntp.ubuntu.com

Make sure that you make this new file executable:

sudo chmod 755 /etc/cron.daily/ntpdate
```

I still don't think it runs at boot time, but the above cron job does what I want. (With thanks to qpieus who first pointed this out to me in another thread.)

---

