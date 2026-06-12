---
title: "installing updates fails (dependency issues?)"
date: 2015-01-12
forum: General Help
---

### Post by joachim-vermeeren on 2015-01-12
Since a few weeks I can no longer install updates the normal way (being: message box tells me there are updates, and I verify and updates are installed). In my notifications bar I get an error notification and it says "Error: BrokenCount > 0". When I try to run the updates it gives my this error message:

> The following packages have unmet dependencies:

indicator-datetime: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-16ubuntu6 is installed
                    Depends: systemd-services but it is a virtual package
                    Depends: systemd-shim but it is not installed
libpam-systemd: Depends: systemd (= 208-8ubuntu8.1) but 208-8ubuntu8.1 is installed
                Depends: systemd-sysv but it is not installed

As suggested by the message box I have tried "apt-get install -f" multiple times, which has changed some things, but in the end, it didn't fix it completely. Trying to install systemd-shim results in this error:
> Adding 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting `/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd' with
  different file `/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service', not allowed
dpkg: error processing archive /var/cache/apt/archives/systemd-shim_8-1ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/systemd-shim_8-1ubuntu0.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

And trying to install systemd-sysv results in this error:
> The following packages have unmet dependencies:
 indicator-datetime : Depends: systemd-shim but it is not going to be installed
 systemd-sysv : Conflicts: upstart
                Conflicts: upstart:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have run synaptic package manager and selected "fix broken packages" this gives an "OK" message, but doesn't result in it actually being ok...

I have no clue what to do next...

---

### Post by wyliecoyoteuk on 2015-01-12
This thread may help:
[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

---

### Post by matt_symes on 2015-01-12
Hi

I would start by looking at your sources files to make sure there are no conflicts and taking it from there so can you post the output (between code tags) of these commands into your next post.

To get the version of Ubuntu you are running

```
cat /etc/lsb-release
```

To get your sources files.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by joachim-vermeeren on 2015-01-12
wyliecoyoteuk, thnx I did the first steps, but the last one gave the same error as before, and I don't know which package I should remove.

matt_symes, I'm running 14.10. This is the result for the sources files:

```
/etc/apt/sources.list:7:deb http://archive.ubuntu.com/ubuntu utopic main restricted
/etc/apt/sources.list:8:deb-src http://archive.ubuntu.com/ubuntu utopic main restricted
/etc/apt/sources.list:12:deb http://archive.ubuntu.com/ubuntu utopic-updates main restricted
/etc/apt/sources.list:13:deb-src http://archive.ubuntu.com/ubuntu utopic-updates main restricted
/etc/apt/sources.list:18:deb http://archive.ubuntu.com/ubuntu utopic universe
/etc/apt/sources.list:19:deb-src http://archive.ubuntu.com/ubuntu utopic universe
/etc/apt/sources.list:20:deb http://archive.ubuntu.com/ubuntu utopic-updates universe
/etc/apt/sources.list:21:deb-src http://archive.ubuntu.com/ubuntu utopic-updates universe
/etc/apt/sources.list:28:deb http://archive.ubuntu.com/ubuntu utopic multiverse
/etc/apt/sources.list:29:deb-src http://archive.ubuntu.com/ubuntu utopic multiverse
/etc/apt/sources.list:30:deb http://archive.ubuntu.com/ubuntu utopic-updates multiverse
/etc/apt/sources.list:31:deb-src http://archive.ubuntu.com/ubuntu utopic-updates multiverse
/etc/apt/sources.list:38:deb http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse
/etc/apt/sources.list:39:deb-src http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse
/etc/apt/sources.list:41:deb http://archive.ubuntu.com/ubuntu utopic-security main restricted
/etc/apt/sources.list:42:deb-src http://archive.ubuntu.com/ubuntu utopic-security main restricted
/etc/apt/sources.list:43:deb http://archive.ubuntu.com/ubuntu utopic-security universe
/etc/apt/sources.list:44:deb-src http://archive.ubuntu.com/ubuntu utopic-security universe
/etc/apt/sources.list:45:deb http://archive.ubuntu.com/ubuntu utopic-security multiverse
/etc/apt/sources.list:46:deb-src http://archive.ubuntu.com/ubuntu utopic-security multiverse
/etc/apt/sources.list:52:deb http://archive.canonical.com/ubuntu utopic partner
/etc/apt/sources.list:53:deb-src http://archive.canonical.com/ubuntu utopic partner
/etc/apt/sources.list.d/google-musicmanager.list.distUpgrade:3:deb http://dl.google.com/linux/musicmanager/deb/ stable main
/etc/apt/sources.list.d/wfg-0ad-trusty.list.distUpgrade:1:deb http://ppa.launchpad.net/wfg/0ad/ubuntu trusty main
```

---

### Post by mc4man on 2015-01-12
I don't have 14.10 so can't be too useul also noting that in regards to systemd 14.10 is between 14.04 & earlier and  15.04 & later.

By default these 4 were installed - 
systemd	 (208-8ubuntu8
systemd-shim	(8-1
upstart	(1.13.2-0ubuntu2
upstart-bin	(1.13.2-0ubuntu2

It seems something you did caused systemd-shim to be removed?
You could ck. current staus of all 4 with 
```
apt-cache policy systemd systemd-shim upstart upstart-bin
```

* I'd likely *consider* installing systemd-shim with dpkg & a --force-overwrite option, making sure that the couple of dependencies of systemd-shim were already installed.
You may choose to proceed more cautiously & try to see why systemd-shim was removed ( if it was, apt-cache policy would show.

---

### Post by joachim-vermeeren on 2015-01-12
systemd-shim wasn't installed and it seemed that one file blocked the installation (/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd), so what I did was, rename the file, do the installation, and then restore the first file.

Quite dirty I would say, but it seems that this did the trick.

---

