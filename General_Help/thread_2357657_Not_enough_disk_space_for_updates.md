---
title: "Not enough disk space for updates"
date: 2017-04-04
forum: General Help
---

### Post by alexwaltz on 2017-04-04
I'm running Ubuntu 14.04 with whole drive encryption.  Perhaps every month or so, I get an error message that there is "not enough disk space" and to free up space before I can perform a security update.  The error is similar to what is posted at the url [https://i1.wp.com/julianhigman.com/blog/wp-content/uploads/2014/08/not-enough-space.png?w=484](https://i1.wp.com/julianhigman.com/blog/wp-content/uploads/2014/08/not-enough-space.png?w=484)

Is there any official Canonical fix for this issue or is there a workaround so that I can avoid reinstalling the OS every month or so?

Thank you

---

### Post by ian-weisser on 2017-04-04
It's fixed in 16.04 and newer releases of Ubuntu.

Since you have 14.04, you can either manually delete old kernels every so often, or you can enable the autoremove option in /etc/apt/apt.conf.d/50unattended-upgrades.
Reinstalling seems a rather extreme solution - properly maintaining your system is much easier and faster.

---

### Post by alexwaltz on 2017-04-04
> **ian-weisser said:**
> It's fixed in 16.04 and newer releases of Ubuntu.

Since you have 14.04, you can either manually delete old kernels every so often, or you can enable the autoremove option in /etc/apt/apt.conf.d/50unattended-upgrades.
Reinstalling seems a rather extreme solution - properly maintaining your system is much easier and faster.

I didn't realise this was fixed in Ubuntu 16.04.  Unfortunately, I'm on 14.04 as some of my apps won't work on the newer version of Ubuntu.

I've attached a copy of the 50unattended-upgrades.  Would you be able to advice how I would go about enabling autoremove through this file?

```
 

// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"${distro_id}:${distro_codename}-security";
//	"${distro_id}:${distro_codename}-updates";
//	"${distro_id}:${distro_codename}-proposed";
//	"${distro_id}:${distro_codename}-backports";
};


// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//	"vim";
//	"libc6";
//	"libc6-dev";
//	"libc6-i686";
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

---

### Post by ian-weisser on 2017-04-04
It's right there in plain language:

```
// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

Edit using sudo. Uncomment the apt-setting line. Change it to 'true'. Save.

---

### Post by alexwaltz on 2017-04-05
> **ian-weisser said:**
> It's right there in plain language:

```
// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

Edit using sudo. Uncomment the apt-setting line. Change it to 'true'. Save.

Might be right there in plain language for you, but not a chance I would have known to change from false to true.  You have to realise the audience you are speaking to, some of us are very green

---

