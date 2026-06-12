---
title: "Startup disk creator wont show any source OS or ISO selected"
date: 2020-03-13
forum: General Help
---

### Post by maytus on 2020-03-13
I installed Lubuntu 18.04, then tried to create a usb with another OS, I was able to see listed my OS, the iso never showed up, I rebooted and tried again, this time the OS was not visible, I decided to upgrade (via software updater) to 19.10 and I still cant make the startup disk creator to show the OS source, I googled the problem and all I can see is issues burning ISOs, can you help me?

---

### Post by guiverc on 2020-03-13
> **maytus said:**
> I installed Lubuntu 18.04, then tried to create a usb with another OS, I was able to see listed my OS, the iso never showed up, I rebooted and tried again, this time the OS was not visible

I'm not sure what you did here. As I understand it you downloaded another ISO, did you write it to usb? If you did with what. The ISO never showed up means?  After downloading it should be wherever you downloaded it to; for me it would be in the my current directory (I use `wget` from the CLI) but I assume it would normally be downloaded to ~/Downloads/ unless you specified another location or changed that folder to another one.  It's also possible I'm completely missing your issue.

> **maytus said:**
> I decided to upgrade (via software updater) to 19.10 and I still cant make the startup disk creator to show the OS source, I googled the problem and all I can see is issues burning ISOs, can you help me?

Lubuntu 18.04 LTS was the last Lubuntu using LXDE. All releases starting from 18.10 use the LXQt and therefore should be fresh installed.

Yes it was possible to release-upgrade to 18.10, but it had problems such that the team decided it wasn't possible for most users & never published the 'guide' and it remained unsupported.

A normal 18.04 LTS release has two upgrade paths, firstly to the next release (18.10) which is now EOL & thus is now closed.  The second option is to the next LTS release (20.04 in this case), but that doesn't open until 20.04.1 has been released (no date scheduled; likely August 2020) but that won't be offered for Lubuntu due to desktop change.  You used neither of those options so it was untested and is unsupported (and neither is supported by Lubuntu due change of desktop).

Regardless, you seem to have gotten it to work though so well done. 

As for your last question: Lubuntu 19.10 uses `usb-creator-kde` ([https://packages.ubuntu.com/eoan/usb-creator-kde](https://packages.ubuntu.com/eoan/usb-creator-kde)) and possibly you are meaning when you click '*Other*' to point to an ISO it isn't showing?  It only shows ISO files it recognizes (there are multiple types) and you weren't specific as to what type of ISO file, so I'd suggest going to a terminal and using `file` to query the type of file.   eg. the output I get for a `file` command shows

```
/de2900/nix_iso/ubuntu-18.04.4-live-server-amd64.iso:      DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 1320672, 4928 sectors
/de2900/lubuntu_64/focal-desktop-amd64.iso: DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 3464572, 7936 sectors

```



I wonder if your ISO file shows something different to a debian/ubuntu type of ISO (not all OSes use the same format, and thus need to be written differently).

---

### Post by sudodus on 2020-03-13
Maybe this causes your problem with the Ubuntu Startup Disk Creator:

The Ubuntu Startup Disk Creator is designed to only make live drives with Ubuntu and Ubuntu family flavours (Kubuntu, Lubuntu ... Xubuntu). It works also with a few other distros with iso files that are configured like Ubuntu (usually because they are 're-spins' developed from Ubuntu).

If you want to make a live drive with some other Linux distro, you can use some other tool, for example [mkusb](https://help.ubuntu.com/community/mkusb).

---

