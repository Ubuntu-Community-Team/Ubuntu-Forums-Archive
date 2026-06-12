---
title: "Software and Updates application"
date: 2021-11-21
forum: General Help
---

### Post by John Jason Jordan on 2021-11-21
I have a computer with Xubuntu 20.04.1 and the Software and Updates application pops up every few hours. In the settings window it says:

Snap packages are checked routinely and installed automatically
For other packages subscribe to: Security updates only
Automatically check for updates: Never
When there are security updates: Display immediately
When there are other updates: Display every two weeks
Notify me of a new Ubuntu version: For long-term support versions

Is it possible to uninstall the Software and Updates application? If not, is there any other way to make this thing shut up?

---

### Post by ActionParsnip on 2021-11-22
Did you select automatic updates. Not sure if this is the cause but it is in the same area. If you disable the automatic updates (as a test) does it go away?

---

### Post by Impavidus on 2021-11-22
It doesn't automatically check for updates, but if you manually check, update manager will display them anyway. You can remove it. It's in a package named update-manager. Don't forget to check for updates manually.

BTW, if you installed all updates, Xubuntu should by now have version 20.04.3.

---

### Post by T6&amp;sfpER35% on 2021-11-22
> Automatically check for updates: Never
that just seem dangerous, updates are you're friend lol, it only takes a minute or two...

this is what mine looks like , i believe that's sufficient .

[ATTACH=CONFIG]289516[/ATTACH]

---

### Post by KBar on 2021-11-22
I check for updates manually. I've never got notifications. For that, I set options to these:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289517&stc=1[/IMG]

---

### Post by John Jason Jordan on 2021-11-22
> **ActionParsnip said:**
> Did you select automatic updates. Not sure if this is the cause but it is in the same area. If you disable the automatic updates (as a test) does it go away?

I can' find 'automatic updates.' The closest I can come is 'Automatically check for updates,' which has always been set to 'Never.'

I tried 'sudo apt remove update-manager,' but it wanted to remove xubuntu-desktop as well, which sounded like it might not even boot, so I aborted the command.

I should have added at the beginning that I do dist-upgrades as soon as there is a new LTS version available, but updates in between are a PITA because they always include a new kernel, which requires a reboot. Rebooting takes half an hour because I always have dozens of things running, and re-launching everything takes a long time. If update-manager finds a new kernel it requires a reboot even if I uncheck everything related to it and install just things like firefox and libreoffice.

I should also mention that I have another computer sitting on my desk, also with Xubuntu 20.04, and software manager has the same settings, but it rarely pops up. And this started happening on the problem computer only about a month ago.

---

### Post by KBar on 2021-11-22
If you don't want automatic installation of kernel upgrades specifically, uncomment the following line in **/etc/apt/apt.conf.d/50unattended-upgrades**:

```
// Python regular expressions, matching packages to exclude from upgrading
Unattended-Upgrade::Package-Blacklist {
    // The following matches all packages starting with linux-
_//  "linux-";_
```

This will blacklist kernel upgrades. It's generally not recommended to do so.

**unattended-upgrade**(8)

---

### Post by ajgreeny on 2021-11-22
The first thing I do each day after starting on my computers is to run the commands ```
sudo apt update && apt list --upgradable
sudo apt full-upgrade
``` to ensure everything is updated fully. Incidentally I normally reboot only when a new kernel version appears; currently 9 days ago.
I never run a distro version upgrade but always clean install when a new LTS version of Xubuntu appears and has reached its 1st point release.

I have also removed the package ***unattended-upgrades*** and also deselected the ***Update Notifier*** in Application Autostart from the Session and Startup section of Settings Manager; I like to update things when I want to, not when the system decides to do it.

---

### Post by John Jason Jordan on 2021-11-22
> **ajgreeny said:**
> 
I have also removed the package ***unattended-upgrades*** and also deselected the ***Update Notifier*** in Application Autostart from the Session and Startup section of Settings Manager; I like to update things when I want to, not when the system decides to do it.

That was it! The Update Notifier application was check-marked in Application Autostart on the problem computer, but not on the other one. I unchecked it, and it was running, so I killed it. 

I think that will solve the problem, although I am curious how it got checked in Application Autostart. Since the problem started only about a month ago that's when it must have gotten checked, but I certainly don't remember doing it. Oh well. 

Thanks to all for the replies!

---

