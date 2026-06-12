---
title: "VirtualBox 4.3.34 Update problem"
date: 2015-11-28
forum: General Help
---

### Post by philchambers on 2015-11-28
I have just allowed the installation of the VirtualBox update to version 4.3.34 (was on 4.3.10.  All my Virtual machines now crash when loading, except for one Windows XP VM.  In particular a Windows 7 VM.

The crash occurs at the point where the Windows Logo appears on boot-up.  I tried using F12 and booting from the Windows 7 Installation CD but that crashed in the same way.

I am on Ubuntu 14.04. I first raised this on the VirtualBox forum but could not get help because I am using the Ubuntu release!

I still have VB version 4.3.10 on a laptop, so I exported the Windows 7 VM which is crashing and imported it on the laptop.  It runs fine there, so this is a problem with the new version.

can anyone help?

---

### Post by ajgreeny on 2015-11-28
Have you updated the guest-additions if you have it installed in the VBox-manager?

I am now using VBox 5.0.10 and have enabled the repos from VBox direct so that version 5 now appears in normal upgrades of my system; perhaps it is worth trying that yourself as it can't be any more of a problem than your current VBox version, and if it is no better than 4.3.34 you can always remove it and start again with a 4.3.## version.

See the **Debian-based Linux distributions** section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) for info on doing this.

---

### Post by philchambers on 2015-12-01
After I did the VB update the VM (which was not powered down) loaded and things seemed to be OK.  I immediately did the Guest additions update and it was when I rebooted that the problem occurred.  I initially assumed it was a VM problem brought about by the updated guest additions.  However, other VMs crashed when re-booting and the fact that the exported VM booted fine on the laptop led me to conclude it was a VB problem.

I also tried uninstalling and re-installing VB but that did not help.

Since no-one has come forward with any possible solution I have downloaded and installed the latest VB from the VB site (5.0.10) and that has fixed things.

I generally prefer to use software downloaded using the Ubuntu Software Centre, even though these are not the latest possible versions but that is not to be with VB!

---

### Post by ajgreeny on 2015-12-01
Go to the vbox link.I show in post #2 and you can add the vbox repository very easily.  You can then install with software centre or any other way, eg apt-get install virtualbox-5.

---

### Post by BPickle on 2015-12-03
I've had the same problem, but have yet to get it fully resolved no matter what I do.

In my case, unchecking USB 2.0 allowed me to boot up. I think the fact that the extensions were a different version is what was causing the boot-up problem.

I did switch to the Oracle versions, and have tried 5.0.10, 5.0.0,  4.3.10, and 4.3.34. I've now switched back to the Ubuntu version. Still, my WinXP guest lacks:


[LIST]
[*]Networking.
[*]Shared clipboard.
[*]Shared folders.
[*]Printing to a USB printer.
[/LIST]

It all worked fine before this recent update to 4.3.34. Now, no matter what I try, these features don't work.

That I can easily switch from the host to the guest to the host with my mouse makes me think that Guest Additions are working, but there is no tray icon. Maybe I never could (I don't remember ever trying), but I can't terminate VBoxTray or VBoxService via TaskManager. The event log says that VBoxService timed out without responding when it was being loaded, but it does show up  in TaskManager.

---

