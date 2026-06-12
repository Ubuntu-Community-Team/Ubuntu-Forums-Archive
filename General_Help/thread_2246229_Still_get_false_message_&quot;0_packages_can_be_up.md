---
title: "Still get false message &quot;0 packages can be updated&quot;."
date: 2014-09-29
forum: General Help
---

### Post by sim085 on 2014-09-29
Hello when I log in I get the message:

```

0 packages can be updated.
0 updates are security updates.

```

However if run apt-get update and apt-get upgrade I get:

```

The following packages will be upgraded:
  bash linux-firmware
2 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 21.0 MB of archives.
After this operation, 17.4 kB of additional disk space will be used.

```

Doesn't this mean that the message I get at the start is false!? Is there a way to fix this?

Here is my output from apt-get update:
```

Ign http://mt.archive.ubuntu.com trusty InRelease
Ign http://mt.archive.ubuntu.com trusty-updates InRelease
Ign http://mt.archive.ubuntu.com trusty-backports InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://mt.archive.ubuntu.com trusty Release.gpg
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://mt.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:3 http://mt.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Get:4 http://security.ubuntu.com trusty-security Release [59.7 kB]
Hit http://mt.archive.ubuntu.com trusty Release
Get:5 http://mt.archive.ubuntu.com trusty-updates Release [59.7 kB]
Get:6 http://mt.archive.ubuntu.com trusty-backports Release [59.7 kB]
Get:7 http://security.ubuntu.com trusty-security/main Sources [45.3 kB]
Hit http://mt.archive.ubuntu.com trusty/main Sources
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://mt.archive.ubuntu.com trusty/restricted Sources
Get:9 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Get:10 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]
Hit http://mt.archive.ubuntu.com trusty/universe Sources
Get:11 http://security.ubuntu.com trusty-security/main amd64 Packages [144 kB]
Hit http://mt.archive.ubuntu.com trusty/multiverse Sources
Hit http://mt.archive.ubuntu.com trusty/main amd64 Packages
Hit http://mt.archive.ubuntu.com trusty/restricted amd64 Packages
Get:12 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:13 http://security.ubuntu.com trusty-security/universe amd64 Packages [48.9 kB]
Hit http://mt.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://mt.archive.ubuntu.com trusty/multiverse amd64 Packages
Get:14 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,148 B]
Get:15 http://security.ubuntu.com trusty-security/main i386 Packages [136 kB]
Hit http://mt.archive.ubuntu.com trusty/main i386 Packages
Hit http://mt.archive.ubuntu.com trusty/restricted i386 Packages
Get:16 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Hit http://mt.archive.ubuntu.com trusty/universe i386 Packages
Get:17 http://security.ubuntu.com trusty-security/universe i386 Packages [48.8 kB]
Hit http://mt.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://mt.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://mt.archive.ubuntu.com trusty/main Translation-en
Hit http://mt.archive.ubuntu.com trusty/multiverse Translation-en_GB
Get:18 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://mt.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://mt.archive.ubuntu.com trusty/restricted Translation-en_GB
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://mt.archive.ubuntu.com trusty/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://mt.archive.ubuntu.com trusty-updates/universe Sources
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://mt.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Get:19 http://mt.archive.ubuntu.com trusty-updates/main i386 Packages [318 kB]
Get:20 http://mt.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:21 http://mt.archive.ubuntu.com trusty-updates/universe i386 Packages [206 kB]
Get:22 http://mt.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,545 B]
Hit http://mt.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/main Sources
Hit http://mt.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://mt.archive.ubuntu.com trusty-backports/universe Sources
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse Sources
Get:23 http://mt.archive.ubuntu.com trusty-backports/main amd64 Packages [6,356 B]
Get:24 http://mt.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:25 http://mt.archive.ubuntu.com trusty-backports/universe amd64 Packages [16.8 kB]
Get:26 http://mt.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [943 B]
Get:27 http://mt.archive.ubuntu.com trusty-backports/main i386 Packages [6,379 B]
Get:28 http://mt.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:29 http://mt.archive.ubuntu.com trusty-backports/universe i386 Packages [16.8 kB]
Get:30 http://mt.archive.ubuntu.com trusty-backports/multiverse i386 Packages [945 B]
Hit http://mt.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/universe Translation-en
Fetched 1,206 kB in 9s (132 kB/s)
Reading package lists... Done

```

---

### Post by mcduck on 2014-09-29
The message you get when you log in reports any updates the system is aware of. It doesn't run *apt-get update* to check for available updates before it allows you to log in, so of course the information might be outdated and actually running apt-get update to check for the updates might give you new information.

I don't think there really is any way how this could be changed, unless you are happy to wait for apt to actually check the repositories instead of just reporting any updates it already knows about before it lets you log in...

---

### Post by sim085 on 2014-09-29
Thanks for the quick answer. Indeed after I called apt-get upgrade I entered 'n' (not to upgrade). When I log out and logged in I correctly got the message that I have two upgrades.

Should the system run apt-get update and apt-get upgrade automatically every so often? This machine is always on so that is why I find it strange that when I log in I don't get updated information. Maybe such schedule is not set up properly after I upgraded from Ubuntu 12 to Ubuntu 14.

---

### Post by ian-weisser on 2014-09-29
The login console messages are determined by /etc/update-motd.d/90-updates-available 
You can easily disable the pending updates stanza. See below for detail.

Apt has a cron job at /etc/cron.daily/apt that determines how often it refreshes the dpkg database (apt-get update), and how often it downloads upgrades (apt-get upgrade), and from which upgrades it will autoinstall. The cron job uses the config files in /etc/apt/apt.conf.d/

Let's look at my rootcrontab:
```
# /etc/crontab: system-wide crontab

25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```
So cron will trigger apt's daily check of it's config files at 06:25 daily. If my machine if off at that time, anacron will trigger the daily check a few minutes after boot.
Usually this means that the dpkg database update will happen at this time - it you login a few hours later, newer updates may have been pushed to the repositories.

Next, let's look at my apt config settings in the 10- and 50- config files:
```
# /etc/apt/apt.conf.d/10periodic

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
```
Automatically refresh the dpkg database (update-package-lists) every day ('1').
Don't pre-download updates or autoclean. I suppose I could change those....

```
# /etc/apt/apt.conf.d/50unattended-upgrades 

// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};
```
This is the Ubuntu default - automagically install security updates. You can see how it's easy to change the setting.

Finally, there's a tiny application -part of Update Manager- that provides the text message about the number of updates to motd. Motd displays the number of updates upon login.
```
/etc/update-motd.d/90-updates-available
#!/bin/sh

if [ -x /usr/lib/update-notifier/update-motd-updates-available ]; then
    exec /usr/lib/update-notifier/update-motd-updates-available
fi
```
You can do all kinds of customizations here - you can trigger an apt-get update so the number of updates is accurate (though it will delay your login), or you can display the number of days since your last installed upgrades, or you can simply disable the stanza.

---

### Post by ian-weisser on 2014-09-29
The login console messages are determined by /etc/update-motd.d/90-updates-available 
You can easily disable the pending updates stanza. See below for detail.

Apt has a cron job at /etc/cron.daily/apt that determines how often it refreshes the dpkg database (apt-get update), and how often it downloads upgrades (apt-get upgrade), and from which upgrades it will autoinstall. The cron job uses the config files in /etc/apt/apt.conf.d/

Let's look at my rootcrontab:
```
# /etc/crontab: system-wide crontab

25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```
So cron will trigger apt's daily check of it's config files at 06:25 daily. If off at that time, anacron will trigger the check a few minutes after boot.
Usually this means that the dpkg database update will happen at this time - if you login a few hours later, newer updates may have been pushed to the repositories.
So sure, the number of updates that motd claims can be incorrect/old.


Next, let's look at my apt config settings in the 10- and 50- config files:
```
# /etc/apt/apt.conf.d/10periodic

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
```
Automatically refresh the dpkg database (update-package-lists) every day ('1').
Don't pre-download updates or autoclean. I suppose I could change those....

```
# /etc/apt/apt.conf.d/50unattended-upgrades 

// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};
```
This is the Ubuntu default - automagically install security updates. You can see how it's easy to change the setting.

Finally, there's a tiny application -part of Update Manager- that provides the text message about the number of updates to motd. Motd displays the number of updates upon login.
```
/etc/update-motd.d/90-updates-available
#!/bin/sh

if [ -x /usr/lib/update-notifier/update-motd-updates-available ]; then
    exec /usr/lib/update-notifier/update-motd-updates-available
fi
```
You can do all kinds of customizations here - you can trigger an apt-get update so the number of updates is accurate (though it will delay your login), or you can display the number of days since your last installed upgrades, or you can simply disable the stanza.

---

### Post by weedwacker2 on 2014-09-29
Check out rubylaser's solution. Worked for me.

[http://ubuntuforums.org/showthread.php?t=2246138&highlight=bash+security](http://ubuntuforums.org/showthread.php?t=2246138&highlight=bash+security)

---

### Post by ian-weisser on 2014-09-29
> **weedwacker2 said:**
> Check out rubylaser's solution.

That problem was a missing DNS entry.
That doesn't seem to be the problem here. sim085's apt-get update output in Post #1 shows name resolution working properly.

---

### Post by sim085 on 2014-09-29
> **ian-weisser said:**
> Apt has a cron job at /etc/cron.daily/apt that determines how often it refreshes the dpkg database

Thanks for your detailed reply. When I go to /etc/cron.daily I can see that apt script is not green. I checked on the forums and this means it is not executable. Could this be a problem?

---

### Post by ian-weisser on 2014-09-29
Yes. The script should be executable.

Example from my system:
```
$ ls -l /etc/cron.daily/apt
-rwxr-xr-x 1 root root 15481 Apr 10 08:05 /etc/cron.daily/apt
```

---

### Post by sim085 on 2014-09-30
> **ian-weisser said:**
> Yes. The script should be executable.

Maybe that was my problem.
Thanks a lot for your help and the detailed description of how the underlying logic of this works. With such info next time it will be easier for me :)

---

