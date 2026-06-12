---
title: "Autoremove Issue"
date: 2023-07-11
forum: General Help
---

### Post by mpmckinnon on 2023-07-11
Hi there I am having this issue can anyone help with me please and thank you. 

[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  radeon-profile-daemon
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 75.8 kB disk space will be freed.
Do you want to continue? [Y/n]  
(Reading database ... 304033 files and directories currently installed.)
Removing radeon-profile-daemon (20190603+git43-7923bd6~ubuntu23.04.1) ...
Disabling/removing radeon profile daemon symlink
[COLOR=#FF5454]**Failed to disable unit: Unit file radeon-profile-daemon.service does not exist.**[/COLOR][COLOR=#000000][/COLOR]
dpkg: error processing package radeon-profile-daemon (--remove):
 installed radeon-profile-daemon package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 radeon-profile-daemon
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]

---

### Post by mpmckinnon on 2023-07-11
I tried to use Synaptic and get this error message

(Reading database ... 304033 files and directories currently installed.)
Removing radeon-profile-daemon (20190603+git43-7923bd6~ubuntu23.04.1) ...
Disabling/removing radeon profile daemon symlink
Failed to disable unit: Unit file radeon-profile-daemon.service does not exist.
dpkg: error processing package radeon-profile-daemon (--remove):
 installed radeon-profile-daemon package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 radeon-profile-daemon
Processing was halted because there were too many errors.
W: Download is performed unsandboxed as root as file '/root/.synaptic/tmp//tmp_sh' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...

---

### Post by mpmckinnon on 2023-07-13
I am still having issues can anyone help please.

---

### Post by grahammechanical on 2023-07-13
Looking at this from a different view point. What video driver are you using? The Radeon Driver or the open source video driver? Check in Software & Updates>Additional Drivers tab. Allow time for the utility to access the internet. Disable the proprietary video driver. Reboot.

You should tell us more about your system. What video adapter? There are commands to use to remove Nvidia proprietary video drivers. I do not think that we do this using Apt or Synaptic.

Regards

---

