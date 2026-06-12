---
title: "how do I add Canonical Partners in Unattended Updates?"
date: 2017-06-20
forum: General Help
---

### Post by ardouronerous on 2017-06-20
I'm maintaining my dad's laptop which has Lubuntu 16.04 on it, I've installed Adobe Flash Player via Canonical Partners because my dad likes to play Candy Crush Saga which is reliant on Adobe Flash Player, and I want Adobe Flash Player to be automatically updated for security reasons.

Here's my */etc/apt/apt.conf.d/50unattended-upgrades*:

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

---

### Post by deadflowr on 2017-06-20
You need to add the origin and the codename.
You can find those in the archive release files found in /var/lib/apt/lists.
For canonical partners it would be
```
"Canonical:<Ubuntu-version-here>";
```
example is:
```
"Canonical: xenial";
```
add it anywhere in the allow-origin section.
run
```
sudo unattended-upgrades -d
```
to make sure that the entry is correct.
It'll usually tell you if something is off, or at least use to.

---

### Post by ardouronerous on 2017-06-20
I've tested this out on a Xubuntu laptop, here's my *50unattended-upgrades*
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
    **"Canonical: xenial";**
};
```

[FONT=courier new]sudo unattended-upgrades -d[/FONT] updated my Adobe Flash Player to the latest version.

Okay, I'll be applying this to my dad's Lubuntu laptop.

Thanks so much for the help  		deadflowr! :)

---

