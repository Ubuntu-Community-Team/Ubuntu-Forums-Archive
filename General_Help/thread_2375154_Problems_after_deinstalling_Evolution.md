---
title: "Problems after deinstalling Evolution"
date: 2017-10-22
forum: General Help
---

### Post by Mel_Blakey on 2017-10-22
I installed Evolution but didn't get on with it. So, I de-installed it by following these instructions:
> ```

sudo apt-get --purge remove evolution evolution-exchange evolution-plugins evolution-common evolution-webcal 
```  The above command will not remove evolution-data-server, evolution-data-server-common
  I would recommend that you use Synaptic Package Manager to completely  remove Evolution.  Just search for it, and mark it for complete  removal.
  Also just to be sure, after removing do:

  ```
sudo rm /usr/share/indicators/messages/applications/evolution

```  Now keep in mind that removing evolution, will also remove gnome panel.  to install just do:

  ```
sudo apt-get install gnome-panel
```

I found these instructions here: [https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution)
I then used Synaptic to deleting everything associated with Evolution.

I am now getting various error messages whilst using Ubuntu 16.04 including:

> enter password to unlock your login keyring

System problem detected

The application SSH Key Agent has closed unexpectedly.

The warnings are repetitive and whilst Ubuntu continues to run, various programs (Firefox, Software Centre and Libra Office) have a tendency to 'grey out' and freeze for 20-30 seconds.

Up to this I've not had any probs and 16.04 has worked great for me. Can anyone help?

Thanks!

---

### Post by maglin2 on 2017-10-23
I can't pretend to know what's going on, but here is a thread that discusses some causes of the login keyring prompt that might give some pointers (ie gnome-online-accounts, automatic login and chrome/chromium). If you use automatic login it might be an idea to change to standard (password entry) login and see if that makes any difference.

[https://ubuntuforums.org/showthread.php?t=2341449](https://ubuntuforums.org/showthread.php?t=2341449)

(if nothing else this will put your post back to the top where it might attract some more expert attention).

---

### Post by ian-weisser on 2017-10-23
> **Mel_Blakey said:**
> I found these instructions here: [https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution)

See if you can find the terminal of of the removal. If you did the removal within the past seven days, it should be in the /var/log/apt directory.
That will tell us what you unintentionally removed.

Alternately, you can reinstall each package one-by-one until you discover which package's removal caused the problem.

If you cannot find the log, and if you cannot determine by restoring packages, then you must decide if you want to troubleshoot and learn (my preferred)...or if you want to reinstall and forget about it.

---

### Post by Mel_Blakey on 2017-10-28
I apologise for not responding sooner. I have been away for a few days.

[**[COLOR=#000000]maglin2[/COLOR]**]("https://ubuntuforums.org/member.php?u=1905722")
Nothing in the link is applicable. But, thanks for bumping my post up for Ian to see :)

> **ian-weisser said:**
> See if you can find the terminal of of the removal. If you did the removal within the past seven days, it should be in the /var/log/apt directory.
That will tell us what you unintentionally removed.

Alternately, you can reinstall each package one-by-one until you discover which package's removal caused the problem.

If you cannot find the log, and if you cannot determine by restoring packages, then you must decide if you want to troubleshoot and learn (my preferred)...or if you want to reinstall and forget about it.

I found nothing with regard to Evolutions removal. I have no idea how to restore each package, so I would be really grateful of some guidance  as I would much prefer to troubleshoot and learn as opposed to a full reinstall.

They 'Login Key Password' prompt appears at each boot up. I have never had that before.

I also get a pop-up which says:
**The application SSH Key Agent has closed unexpectedly.**

**ExecutablePath**
   /usr/bin/gnome-keyring-daemon
**Package**
   gnome-keyring 3.18.3-0ubuntu2

Further down it says:

*You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occur*s:

libeg1-mesa, ligl1-mesa-dri, libglapi-mesa, libpam-systemd0, libudev1, libwayland-egl1-mesa, systemd, udev

So, I tried the following:
```

sudo apt update 
sudo apt dist-upgrade
```
To no avail

Dispite this Ubuntu is plodding along, except that some apps (FireFox in particular) are freezing with a grey screen.

---

### Post by ian-weisser on 2017-10-28
> **Mel_Blakey said:**
> 
So, I tried the following:
```

sudo apt update 
sudo apt dist-upgrade
```
To no avail

'to no avail' might mean many things.
Can you please show us the complete output?

---

### Post by Mel_Blakey on 2017-10-28
> **ian-weisser said:**
> 'to no avail' might mean many things.
Can you please show us the complete output?

Sorry, by to no avail I meant that it didn't fix my problems...

Is this the output required?
```
Start-Date: 2017-10-28  18:18:08
Commandline: apt dist-upgrade
Requested-By: mel (1000)
Install: libpam-kwallet-common:amd64 (4:5.8.8-0ubuntu1~ubuntu16.04~ppa1, automatic)
Upgrade: libgnutls28-dev:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libgnutlsxx28:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libgles2-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libgnutls-openssl27:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libsystemd0:amd64 (229-4ubuntu19, 229-4ubuntu21), adobe-flash-properties-gtk:amd64 (1:20170912.1-0ubuntu0.16.04.1, 1:20171025.1-0ubuntu0.16.04.1), grub-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), libglapi-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), binutils:amd64 (2.26.1-1ubuntu1~16.04.4, 2.26.1-1ubuntu1~16.04.5), libgnutls-dev:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libxatracker2:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), grub2-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), udev:amd64 (229-4ubuntu19, 229-4ubuntu21), libegl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), boot-sav:amd64 (4ppa53, 4ppa62), initramfs-tools-bin:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), libudev1:amd64 (229-4ubuntu19, 229-4ubuntu21), libgbm1:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), adobe-flashplugin:amd64 (1:20170912.1-0ubuntu0.16.04.1, 1:20171025.1-0ubuntu0.16.04.1), boot-sav-extra:amd64 (4ppa53, 4ppa62), libpam-kwallet5:amd64 (4:5.5.5-0ubuntu1, 4:5.8.8-0ubuntu1~ubuntu16.04~ppa1), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), systemd-sysv:amd64 (229-4ubuntu19, 229-4ubuntu21), libwayland-egl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libpam-systemd:amd64 (229-4ubuntu19, 229-4ubuntu21), distro-info-data:amd64 (0.28ubuntu0.3, 0.28ubuntu0.5), systemd:amd64 (229-4ubuntu19, 229-4ubuntu21), glade2script:amd64 (3.2.3~ppa2, 3.2.3~ppa4), libgl1-mesa-dri:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), libgl1-mesa-glx:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), grub-efi-amd64-signed:amd64 (1.66.12+2.02~beta2-36ubuntu3.12, 1.66.14+2.02~beta2-36ubuntu3.14), libgnutls30:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), mesa-vdpau-drivers:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), initramfs-tools-core:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), initramfs-tools:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), boot-repair:amd64 (4ppa53, 4ppa62)
End-Date: 2017-10-28  18:20:25
```

Thanks BTW

---

