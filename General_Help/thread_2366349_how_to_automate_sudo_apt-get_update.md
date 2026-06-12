---
title: "how to automate sudo apt-get update?"
date: 2017-07-17
forum: General Help
---

### Post by ardouronerous on 2017-07-17
I've experienced this on Lubuntu 16.04, I have unattended-updates installed and running, but didn't get updates for a couple of days, that was until I pressed 'Reload' and 'Mark All Upgrades' in Synaptic Package Manager, then all the updates started pouring in.

Pressing 'Reload' on Synaptic is the same as [FONT=courier new]sudo apt-get update[/FONT] right? Anyway to automate it? Like on startup?

---

### Post by aasheeshjoshi on 2017-07-17
Perhaps you can create a simple bash script with this command and follow the instructions [here]("https://stackoverflow.com/questions/8339555/how-to-run-a-script-at-the-start-up-of-ubuntu") to ensure it runs on boot.

You can also just add it to cron if you know your computer will always be powered on at a specific time of the day.

The script could look something like this:
```
#!/bin/bash
sudo apt-get update
```

---

### Post by ardouronerous on 2017-07-17
> **aasheeshjoshi said:**
> Perhaps you can create a simple bash script with this command and follow the instructions [here]("https://stackoverflow.com/questions/8339555/how-to-run-a-script-at-the-start-up-of-ubuntu") to ensure it runs on boot.

You can also just add it to cron if you know your computer will always be powered on at a specific time of the day.

The script could look something like this:
```
#!/bin/bash
sudo apt-get update
```

Thanks for the reply.
I'd like to do the command on startup, so based off the instructions you referenced, the easiest way to run things at startup is to add them to the file /etc/rc.local.

I haven't edited my rc.local yet, but I want confirm if I'm doing the right thing because I don't want to accidently bork my system.

This is what I'm going to add to my rc.local:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**sudo apt-get update**
exit 0
```

Please confirm if this is correct, thanks.

---

### Post by deadflowr on 2017-07-17
If you're going to add it to the /etc/rc.local file, then lose the sudo.
The command would already be running as root.

Beside that, you seem to be having a lot more trouble setting automatic updates than most people.
(Most people are having an opposite reaction, where they have a hard time disabling them)

---

### Post by ardouronerous on 2017-07-17
> **deadflowr said:**
> If you're going to add it to the /etc/rc.local file, then lose the sudo.
The command would already be running as root.

Beside that, you seem to be having a lot more trouble setting automatic updates than most people.
(Most people are having an opposite reaction, where they have a hard time disabling them)

Thanks for the correction :)
So it's going to look like this then:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**apt-get update**
exit 0
```

I have no idea why I'm having such a hard time with setting automatic update, but shouldn't unattended updates include automating sudo apt-get update?

Question, why would anyone want to disable autoupdate?

---

### Post by deadflowr on 2017-07-17
> Question, why would anyone want to disable autoupdate?
More control.
Not having valuable bandwidth get eaten away.
Not being surprised when they start some app and it loads differently, only to find it got updated.

Those are just a couple quick reasons, there are more.

---

### Post by ardouronerous on 2017-07-17
> **deadflowr said:**
> More control.
Not having valuable bandwidth get eaten away.
Not being surprised when they start some app and it loads differently, only to find it got updated.

Those are just a couple quick reasons, there are more.

For me, it's all about security, because I heard the recent ransomware trojans hitting Linux exploited unpatched software, so I kinda want my system to be always up to date.

Does rc.local have a log file?

How would I know if sudo apt-get update ran on startup or not?

Does rc.local have a log file? Thanks.

---

### Post by efflandt on 2017-07-18
If you want to log to /var/log/syslog you could pipe the output to logger:```
/usr/bin/apt-get update | /usr/bin/logger -e
```If that may add too much clutter to syslog, see **man logsave** to save output to a file instead (depending upon options can either replace or append to a file).

You should get in the habit of using full paths for things that might not have any or complete $PATH (especially start up scripts or using cron).

---

### Post by ardouronerous on 2017-07-18
Sorry efflandt, I didn't understand you're instructions. Where am I suppose to put the code?

---

### Post by Dennis N on 2017-07-18
If you have "Automatically check for updates" = anything but Never, in "Software and Updates" > Updates Tab, then you shouldn't need a script of your own to initiate a check for available updates.

_Unattended upgrades_
Check if it ran:
Results are logged in /var/log/unattended-upgrades. Typical log entry:
```
2016-04-26 11:36:25,075 INFO Starting unattended upgrades script
2016-04-26 11:36:25,075 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-04-26 11:36:27,169 INFO No packages found that can be upgraded unattended and no pending auto-removals

```

---

### Post by deadflowr on 2017-07-18
> **ardouronerous said:**
> Sorry efflandt, I didn't understand you're instructions. Where am I suppose to put the code?

You would put the code efflandt posted in place of the apt-get update line in your rc.local file.
So you would replace the apt-get update with the /usr/bin-apt-get update .
And it was also suggested adding the logger option, which would then place any logging the command ran in the syslog file, which you can see at /var/log/syslog.

If that makes more sense.

---

### Post by ardouronerous on 2017-07-18
> **Dennis N said:**
> If you have "Automatically check for updates" = anything but Never, in "Software and Updates" > Updates Tab, then you shouldn't need a script of your own to initiate a check for available updates.

_Unattended upgrades_
Check if it ran:
Results are logged in /var/log/unattended-upgrades. Typical log entry:
```
2016-04-26 11:36:25,075 INFO Starting unattended upgrades script
2016-04-26 11:36:25,075 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-04-26 11:36:27,169 INFO No packages found that can be upgraded unattended and no pending auto-removals

```

Here's my settings:
[ATTACH=CONFIG]276042[/ATTACH]
And here's /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    // Extended Security Maintenance; doesn't necessarily exist for
    // every release and this system may not have it installed, but if
    // available, the policy for updates is such that unattended-upgrades
    // should also install from here by default.
    "${distro_id}ESM:${distro_codename}";
    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
    "${distro_id}:${distro_codename}-backports";
    "Canonical: xenial";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//    "vim";
//    "libc6";
//    "libc6-dev";
//    "libc6-i686";
};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";
```

And /etc/apt/apt.conf.d/10periodic
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";
```

And /etc/apt/apt.conf.d/20auto-upgrades:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

But for some reason I wasn't getting updates, so I had to go into Synaptic Package Manager to reload the repos myself, then the updates started pouring in, any reason why that's happened?

> **deadflowr said:**
> You would put the code efflandt posted in place of the apt-get update line in your rc.local file.
So you would replace the apt-get update with the /usr/bin-apt-get update .
And it was also suggested adding the logger option, which would then place any logging the command ran in the syslog file, which you can see at /var/log/syslog.

If that makes more sense.

Thanks for the clarification :)

---

### Post by ian-weisser on 2017-07-19
> **ardouronerous said:**
> Anyway to automate it? Like on startup?


It's already automated. You just need to tweak it.

Unattended-updates is triggered by a daily cronjob: /etc/cron.daily/apt-compat

Simply edit that file to comment out the 'random_sleep' on line 49.
That 'random sleep' is why you think it's not running. It is running, it's just set for a random time when your system happens to be off. It will run automatically a few minutes after reboot. It's clever that way.

If you edit out the 'random_sleep' (intended to spread the load on servers), then apt-daily will run at the same time each day...or a few minutes after startup is the system happens to be off (thanks, anacron).
One tiny edit. Adding one character to one line. That's all.

You can have apt do update-before-shutdown (like Windows) even easier.

---

### Post by ardouronerous on 2017-07-19
> **ian-weisser said:**
> It's already automated. You just need to tweak it.

Unattended-updates is triggered by a daily cronjob: /etc/cron.daily/apt-compat

Simply edit that file to comment out the 'random_sleep' on line 49.
That 'random sleep' is why you think it's not running. It is running, it's just set for a random time when your system happens to be off. It will run automatically a few minutes after reboot. It's clever that way.

If you edit out the 'random_sleep' (intended to spread the load on servers), then apt-daily will run at the same time each day...or a few minutes after startup is the system happens to be off (thanks, anacron).
One tiny edit. Adding one character to one line. That's all.

I haven't edited [FONT=courier new]/etc/cron.daily/apt-compat[/FONT] yet, but I want to confirm if this is correct before I do, so here's what I'm going to do:
```
#!/bin/sh

set -e

# Systemd systems use a systemd timer unit which is preferable to
# run. We want to randomize the apt update and unattended-upgrade
# runs as much as possible to avoid hitting the mirrors all at the
# same time. The systemd time is better at this than the fixed
# cron.daily time
if [ -d /run/systemd/system ]; then
    exit 0
fi

check_power()
{
    # laptop check, on_ac_power returns:
    #       0 (true)    System is on main power
    #       1 (false)   System is not on main power
    #       255 (false) Power status could not be determined
    # Desktop systems always return 255 it seems
    if which on_ac_power >/dev/null 2>&1; then
        on_ac_power
        POWER=$?
        if [ $POWER -eq 1 ]; then
            return 1
        fi
    fi
    return 0
}

# sleep for a random interval of time (default 30min)
# (some code taken from cron-apt, thanks)
random_sleep()
{
    RandomSleep=1800
    eval $(apt-config shell RandomSleep APT::Periodic::RandomSleep)
    if [ $RandomSleep -eq 0 ]; then
    return
    fi
    if [ -z "$RANDOM" ] ; then
        # A fix for shells that do not have this bash feature.
    RANDOM=$(( $(dd if=/dev/urandom bs=2 count=1 2> /dev/null | cksum | cut -d' ' -f1) % 32767 ))
    fi
    TIME=$(($RANDOM % $RandomSleep))
    sleep $TIME
}

# delay the job execution by a random amount of time
**//random_sleep**

# ensure we don't do this on battery
check_power || exit 0

# run daily job
exec /usr/lib/apt/apt.systemd.daily

```

> **ian-weisser said:**
> You can have apt do update-before-shutdown (like Windows) even easier.

How do I do this?

---

### Post by ian-weisser on 2017-07-20
I suggest '#' instead of  '//' for comments in scripts.
It's not C code,

To run unattended-upgrades before shutdown, enable the option in the config file: /etc/apt/apt.conf.d/50unattended-upgrades . It's around line 37.
I don't use it. I find Debian/Ubuntu's in-the-background updates are much less intrusive the way they are.
During-shutdown has made me miss my bus, and a long wait for the next.

---

