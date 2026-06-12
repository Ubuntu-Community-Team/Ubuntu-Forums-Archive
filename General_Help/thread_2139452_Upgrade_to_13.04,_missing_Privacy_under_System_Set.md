---
title: "Upgrade to 13.04, missing Privacy under System Settings"
date: 2013-04-26
forum: General Help
---

### Post by lotsofish on 2013-04-26
I upgraded two machines from 12.10 to 13.04. One of them has the Privacy settings under "System Settings" (gnome-control-center), the other does not.

Is privacy built into gnome-control-center or is it a separate install? I did get an error message during the install on the machine it doesn't work on, but running 'dpkg --configure -a' and 'apt-get -f install' don't show any output.

I uninstalled and reinstalled gnome-control-center on the machine that doesn't have it, and it did not appear in the system settings.

Privacy is the one I was looking for. It also appears that I am missing Landscape Service. (I don't have a use for it, but that tells me something is wrong here.) I'm not sure if I am missing anything else at this point.

'do-release-upgrade' shows "No new release found."

---

### Post by lotsofish on 2013-04-26
OK, so it looks like the install process definitely didn't finish correctly. How can I finish or run it again?

/var/log/dist-upgrade/main.log
This is the end. On the machine that worked, it entered a lot more after this section, including removing all the obsolete software and kernels. I still have the old kernels on this machine that didn't work.

```
2013-04-26 10:05:16,547 INFO cache.commit()
2013-04-26 10:05:16,547 DEBUG failed to SystemUnLock() (E:Not locked) 
2013-04-26 11:23:05,903 DEBUG got a conffile-prompt from dpkg for file: '/etc/gnome/defaults.list'
2013-04-26 11:32:06,389 ERROR got an error from dpkg for pkg: 'apt-xapian-index': 'subprocess installed post-installation script returned error exit status 1'
2013-04-26 11:32:06,389 DEBUG running apport_pkgfailure() apt-xapian-index: subprocess installed post-installation script returned error exit status 1
2013-04-26 11:32:06,395 WARNING Failed to determine apport version (No module named pyexpat)
2013-04-26 11:32:06,545 ERROR got an error from dpkg for pkg: 'apt-xapian-index': 'subprocess installed post-installation script returned error exit status 1'
2013-04-26 12:03:12,304 WARNING no activity on terminal for 300 seconds (Installed app-install-data)
2013-04-26 12:06:43,019 ERROR not handled expection:
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2013-04-26 12:06:43,020 DEBUG running apport_crash()
2013-04-26 12:06:43,023 ERROR failed to import apport python module, can't report bug: No module named pyexpat
2013-04-26 12:11:43,038 WARNING no activity on terminal for 300 seconds (Installed icedtea6-plugin)
2013-04-26 12:33:43,998 DEBUG enabling apt cron job
2013-04-26 12:33:44,332 ERROR SystemError from cache.commit(): installArchives() failed
2013-04-26 12:34:00,465 DEBUG enabling apt cron job
2013-04-26 12:34:00,467 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
2013-04-26 12:34:00,473 ERROR got error from PostInstallScript ./xorg_fix_proprietary.py (Failed to execute child process "./xorg_fix_proprietary.py" (No such file or directory))
2013-04-26 12:34:03,032 DEBUG enabling apt cron job
```

---

### Post by lotsofish on 2013-04-27
I discovered another problem. If I have the machine that the install didn't work connected to WIFI (it's a laptop), the entire wireless network goes to a crawl. The network seed on all the other machines that connect to WIFI all slow down to barely usable.

I guess I'm probably going to end up having to reinstall?

---

### Post by charlesopondo on 2013-05-01
I was trying to change privacy settings on my computer and realized I have exactly the same problem: missing privacy and landscape settings. The other computer I upgraded at the same time (and ironically using .debs downloaded by this one during its upgrade, to speed the process up) appears to have both.

---

### Post by charlesopondo on 2013-05-02
I installed Activity Log Manager and Landscape from Software Centre. This should put Privacy in System settings; works for Landscape but not Privacy because apparently in the latter case there's a bug in the package, I think: [https://bugs.launchpad.net/ubuntu/+source/activity-log-manager/+bug/1050620](https://bugs.launchpad.net/ubuntu/+source/activity-log-manager/+bug/1050620)

---

