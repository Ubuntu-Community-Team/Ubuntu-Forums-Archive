---
title: "Automation of Software Updater Settings"
date: 2013-10-21
forum: General Help
---

### Post by dabbner2 on 2013-10-21
I'm looking to manipulate the Software Updater settings on a large number of systems all at once.  I have a management platform called Labtech, which we will use to either run a CLI command, or edit a config file.  The problem is, I can't find the file/command that will disable the Software Updater.  Before you go on a rant telling me how bad an idea the turning off updates is - we are going to patch the systems via automation / scripting using the same Labtech platform.  What we are trying to eliminate are issues where users will see popups about software updates being ready for their systems.  Having explained that, is there a way to manage the Ubuntu software updater via command line?  Or a config file that we can edit?  I keep coming up with information on all the aptitude CLI switches and their use, but nothing that will just turn the updater off.  

The settings I'd like to distribute and enforce are displayed in the attached screenshot.  

Any help you can provide would be appreciated.  

Thanks,

Alex

---

### Post by ian-weisser on 2013-10-21
1) To edit software updates using script or CLI:

Edit or replace /etc/apt/apt.conf.d/10periodic
The instructions are in /etc/cron.daily/apt (admittedly not an obvious location)
```

APT::Periodic::Enable "0";   # Enable the update/upgrade script (0=disable)

# or you can just zero out the existing fields to preserve compatibility with software-sources
APT::Periodic::Update-Package-Lists "0";    # Do "apt-get update" automatically every n-days (0=disable)
APT::Periodic::Download-Upgradeable-Packages "0";  # Do "apt-get upgrade --download-only" every n-days (0=disable)
APT::Periodic::AutocleanInterval "0";  # Do "apt-get autoclean" every n-days (0=disable)
APT::Periodic::Unattended-Upgrade "0";   # Run the "unattended-upgrade" security upgrade script every n-days (0=disabled)

```


2) You can also merely uninstall the update-manager and update-notifier packages.
They are dependencies of the ubuntu-desktop metapackage, so beware that a future reinstall of ubuntu-desktop will drag them back in again.

---

