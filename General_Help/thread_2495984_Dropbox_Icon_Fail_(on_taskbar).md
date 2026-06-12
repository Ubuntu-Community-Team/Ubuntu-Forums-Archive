---
title: "Dropbox Icon Fail (on taskbar)"
date: 2024-03-10
forum: General Help
---

### Post by Kurt_Alan on 2024-03-10
Hello All,

Unfortunately, I just realized that I posted on this same problem about a year ago. As I recall, there was no solution then. Maybe there is now??

I just did a clean install of Ubuntu 23.10, preparatory to the upcoming LTS.

I installed Dropbox via CLI. It runs correctly, i.e. it will downloadj nearly 1 TB of data but I cannnot use Selective Sync because Preferences are not available because the taskbar icon fails to open. I killed it with "Drobox stop."

Dropbox is a mandatory part of my workflow. If Dropbox doesn't work, it's good-bye Ubuntu (this iteration), not Dropbox. For me, Dropbox is more important than Ubuntu. 

Here are my troubleshooting steps:
1. Purge Dropbox from CLI and re-install -- FAIL
2. Re-boot -- FAIL
3. Workaround found on the Net: toggle the Lock Screen on and off -- FAIL

If I canf't get Dropbox running I'm going to have to wipe this install and re-install 22.04 LTS for which I had no problems with Dropbox (except that the Updater was corrupted, so I installed to 23.10). Now my Updater works but Dropbox fails. 

Any ideas? Anyone have this problem? 

Thanks!

---

### Post by dhlocker on 2024-08-04
A recommendation from another poster in another [thread]("https://ubuntuforums.org/showthread.php?t=2498274") worked for me; I don't know if it will survive a reboot, but I recommend trying:

```

**sudo apt --reinstall nautilus-dropbox**

```

I had previously uninstalled, reinstalled from the dropbox packages ([https://linux.dropboxstatic.com/pack....04.17_all.deb]("https://linux.dropboxstatic.com/packages/ubuntu/nautilus-dropbox_2024.04.17_all.deb"))  with no joy, and killed and restarted with several different options to  no effect. The first installation dropped down a menu that was  invisible; the second and third tries would do nothing when the icon was  clicked; the **sudo apt --reinstall nautilus-dropbox** brought me back to the menu I've grown to know.

---

