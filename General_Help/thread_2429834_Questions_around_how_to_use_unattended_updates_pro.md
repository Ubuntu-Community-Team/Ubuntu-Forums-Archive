---
title: "Questions around how to use unattended updates properly"
date: 2019-10-23
forum: General Help
---

### Post by greavette on 2019-10-23
Hello,

We have some servers in our office which we patch on a regular basis, usually monthly we'll schedule downtime and patch each server.

I've read about a feature within Ubuntu called unattended-upgrades whereby only security patches will be installed automatically.  I think this might be a good idea for us to use this but I have a few questions first and I'm hoping this community can point me in the right direction:

1.  I don't want my servers to automatically reboot and I can see in the configuration of using unattended upgrades that I can turn off auto reboot.  But if I schedule my reboots for each month, what is the danger of using unattended-upgrades on my Ubuntu server if O/S patches get installed at anytime during the month and I wait up to a month to finally reboot the servers?  Could this unattended upgrade install prior to the reboot break anything or cause my O/S not to work because it is waiting for a reboot?

2.  Will unattended-upgrades work on Ubuntu 16.04 and 14.04? I'm seeing reference in this post - [https://www.richud.com/wiki/Ubuntu_Enable_Automatic_Updates_Unattended_Upgrades](https://www.richud.com/wiki/Ubuntu_Enable_Automatic_Updates_Unattended_Upgrades) that unattended-upgrades did not remove the kernel properly for Ubuntu 16.04 versions and earlier.  Makes me wonder if unattended-upgrades shouldn't be used on Ubuntu servers older than 18.04?  Can anyone comment on the safety of using unattended-upgrades on my older Ubuntu servers?


What I'm really looking for is a way to patch Ubuntu only for security patches and not for all Apps.  In Red Hat I can use the --security switch in yum update and only the security patches for the O/S will be installed. I'd like to have the same function in Ubuntu and at times only patch for security patches on the O/S.  Any advice this community can provide on my above questions would be greatly appreciated.  

Thank you.

---

### Post by TheFu on 2019-10-24
>  Could this unattended installs break anything or cause my O/S not to work because it is waiting for a reboot?
Yes, it could.  If your systems are that critical, manual patching is the only sure solution.

Monthly is way too long for internet-facing servers.  I do weekly and patch everything on my servers - **sudo apt dist-upgrade**.  About once every 4-6 yrs, a patch will break something. That's why we have daily, automatic, backups. Restoring a backup takes 30-45 min clock-time and about 5 minutes of my time.  I still remember the time some broken dependencies decided to remove mariadb and install mysql. That took down our project management server for the entire company.  It happened once and I've never seen anything nearly as bad the last 8+ yrs.

You can pay for landscape patching which can patch running kernels, then just restart any impacted services and you are golden.  I'd only worry about libc updates requiring a full system reboot.  For desktops, restarting all GUI programs is much more important, since shared libraries may be updated while the main program is running, but those shared libs are not loaded. Incompatible program and libraries can result.

Free support for 14.04 ended months ago.  Contact your Canonical rep for questions about how their paid support works.  No server on any network should be running unsupported software.

Every month or so, I run **sudo apt autoremove ; sudo apt autoclean ** to remove package cruft from systems. If you have a separate /boot/ partition, it will fill up if you don't do this.

Ubuntu is not Debian nor is it Redhat.  dnf will automatically update the local package lists. On Ubuntu, we have to manually do that via *sudo apt update*.  People often forget that slight difference and get into APT-hell over it.

---

### Post by greavette on 2019-10-24
Thanks very much for the reply TheFu!  Really appreciate you taking the time to reply to my thread.  I also plan on running the autoremove and autoclean to keep severs cleaned up. None of our Ubuntu servers are Internet facing.

Yes we are pushing our team to move off of 14.04 for their server, definitely agree that this is a risk.  We are using 18.04 with a few 16.04 still in the mix.  

I've not heard of landscape patching which can patch running kernels.  I've read up a bit on kpatch for patching but I'm unsure if it will work with Ubuntu (I'll need to investigate more).  

Perhaps you can provide some context for me on something.  From my research it seems that apt upgrade will update all packages but not the kernel.  apt dist-upgrade will install all updates as well as kernel modules.  But does upgrading all packages mean that the application is upgraded or left at it's current version and a patch is applied to secure it?  For some apps we don't want to upgrade the app but we do want to patch the app if a patch exists. 

Back to unattended upgrades...I was planning on making this a manual process as follows:
```
Ensure the /etc/apt/apt.conf.d/50unattended-upgrades file is selecting only security updates.
I would then need to find a way to turn off the automatic updates of unattended upgrades (Still looking into this part).
Then when I'm ready to patch I manually issue "sudo unattended-upgrade" to install security updates.
```

And yet another option from an old post I found ([https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line](https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line)) ...here is a script to install security updates only (I'll test it out on a test sever first to confirm):

```
apt-get -s dist-upgrade | grep "^Inst" | 
    grep -i securi | awk -F " " {'print $2'} | 
    xargs apt-get install
```

Or this larger script that may do the job as well:

```
#!/usr/bin/env bash
set -e

# List upgradable packages
apt-get update
apt list --upgradable 2>/dev/null
# List security upgrades
test "$(apt-get upgrade -s -y)" && (apt-get upgrade -s -y)
# List upgradable apt packages then upgrade
apt-get update && apt-get upgrade -y  -V | grep '=>' | awk '{print$1}' && test "$(apt-get upgrade -y)"
```

---

### Post by TheFu on 2019-10-24
You have some specific questions which are outside my experience. 

The teams on 14.04 will have a hard time. Basically, they can't do a release-upgrade now.  They have to start from a fresh install.  Had they moved last Feb, there was a much better chance that things would work. Ok well, lots and lots of things have changed since 14.04 (init system, apache major version, network management) so it really is smarter to start fresh to ensure cruft isn't left over causing issues.

As for the difference between apt upgrade and apt full-upgrade, the apt-get manpage provides the clearest response:```

       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```

dist-upgrade == full-upgrade  These don't work in Ubuntu like a Debian admin would expect.

Kernels are patched based on the kernel line they are in.  Nothing short of do-release-upgrade or manually installing the HWE kernel stack will change the kernel line used on an install.  Well, you could do some funky debian things that Ubuntu doesn't expect any user to do manually, but besides those 2 methods, your 4.4.x.x kernel will stay as a 4.4.y.z kernel until you manually do one of the 3 things above.  

If you get an ISO file for 16.04, 16.04.1, 16.04.2, 16.04.3 .... each will almost certainly be in a different kernel "line".   apt dist-upgrade will take a 16.04.2 install to 16.04.3, but retain the .2 kernel.

It is very possible to have (20) 16.04.6 servers with some running 4.4 and others running 4.15 kernels.  I have that situation here.  Loading the HWE kernel just isn't worth it to me.  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Sorry I can't help with the other stuff.

---

