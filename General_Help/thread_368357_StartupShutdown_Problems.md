---
title: "Startup/Shutdown Problems"
date: 2007-02-23
forum: General Help
---

### Post by amphet on 2007-02-23
I'm running Ubuntu 6.10 Edgy, one of my problems is that when I start ubuntu almost every time right after the ubuntu boot up screen, kubuntu boot up screen would show up shutting down my system, this happens like 3 or 4 times before my system boots up correctly. any ideas?

---

### Post by cronholio on 2007-02-23
Are you running Ubuntu or Kubuntu? Do you remember any change you did to your system that might cause the error? What do you mean by boot up screen, the GDM login prompt?

---

### Post by amphet on 2007-02-23
I'm running ubuntu, with kde which technically makes it kubuntu? by boot up screen I mean the ubuntu's progress bar while booting the system. and I've had the problem since I installed kde (kubuntu-desktop)

---

### Post by cronholio on 2007-02-23
Can you tell us the contents of your /etc/rc2.d/ directory?

---

### Post by amphet on 2007-02-23
```


README              S13kdm                S20dbus          S20mysql-ndb          S25bluetooth       S99rc.local
S01apport           S19cupsys             S20exim4         S20nfs-kernel-server  S89anacron         S99rmnologin
S05vbesave          S19hplip              S20festival      S20nvidia-kernel      S89atd             S99stop-readahead
S10acpid            S19mysql              S20firestarter   S20powernowd          S89cron            S99timidity
S10powernowd.early  S19mysql-ndb-mgm      S20hddtemp       S20rsync              S90binfmt-support
S10sysklogd         S20apmd               S20hotkey-setup  S20samba              S91apache2
S11klogd            S20apt-index-watcher  S20kde-guidance  S20ssh                S98usplash
S13gdm              S20clamav-freshclam   S20makedev       S21nfs-common         S99acpi-support

```

---

### Post by cronholio on 2007-02-23
Delete S13gdm and try again (don't worry, it is just a link and can easily be restored).

---

### Post by amphet on 2007-02-23
didn't worked :(

---

### Post by cronholio on 2007-02-23
You might try reinstalling:

```
aptitude reinstall kubuntu-desktop
```

Don't worry, it will keep your old settings and data.

---

### Post by amphet on 2007-02-23
still not working, it's really annoying as the ubuntu's progress bar fills up the other one appears shutting down the computer well almost since it doesn't shut it down completely

---

### Post by amphet on 2007-02-23
anyone?

---

### Post by amphet on 2007-02-23
please?

---

### Post by cronholio on 2007-02-24
Since it's obviously a KDM problem, try deleting the S13kdm entry as well and reboot. You should get a text login prompt. Log in and type:
```
sudo /etc/init.d/kdm start
``` and tell us if it works.

---

### Post by amphet on 2007-02-24
I think that actually worked, hmm I wonder what was causing that.

---

