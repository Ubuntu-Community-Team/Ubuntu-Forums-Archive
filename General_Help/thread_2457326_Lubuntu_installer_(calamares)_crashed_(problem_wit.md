---
title: "Lubuntu installer (calamares) crashed (problem with apt)"
date: 2021-01-30
forum: General Help
---

### Post by lieven-debels on 2021-01-30
Hi all

I just tried to install lubuntu 20.04. However, at about 80% of the installation, the installer (calamares) hangs. After 3 minutes, I got the following error:

 Command *apt install -y --no-upgrade -o Acquire::gpgv::Options::=--ignore-time-conflict grub-efi-$(if grep -q 64 /sys/firmware/efi/fw_platform_size; then echo amd64-signed; else echo ia32; fi)* terminated with error code 100. Log: WARNING: apt does not have a stable CLI interface. Use with caution in scripts. Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 24184 (apt)...

Then it repeats dozens of times, Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 24184 (apt)... till text goes off screen at the bottom.

Any idea what's causing this and how I can get rid of this error so the installation finishes?

Thanks for helping out.

---

### Post by lieven-debels on 2021-01-30
Ok, solved the problem myself.

I first installed gparted on the live iso.
Then ran the installer again.
To my surprise it continued to the end.
When rebooting, the new lubuntu was booted promptly.

So I guess this might be a bug in the kde-partition-manager. But why include it in the iso, if it fails to install the system?
Why not stick to gparted, which seems to work fine?

Should I report this to the developers?

---

### Post by guiverc on 2021-01-30
I think your error occurred just because of bad luck (*timing*).  Had you have done nothing (just the wait whilst you installed `gparted`) then tried again, it's likely to have worked too  (*but I'm guessing*)

Modern Lubuntu uses LXQt & Qt5, as does *KDE Partition Manager*.

*gparted* however is GTK3 based; so will use a lot more resources (*require more libraries to be installed so more disk space, let alone more RAM required during its operation*) so makes little sense (*the hit was far less in LXDE releases of Lubuntu as they used GTK2 and it made more sense than anything else*).

`*gparted*` is not used at all by `calamares` so it has no play in it, neither does `*KDE partition manager*` either - they are *user* run partition tools, so are only run when you run & use them, and not used by the installer at all.

If you'd like to report bugs with Lubuntu, I'll provide the most useful link - [https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/) 

The issue was experienced in QA-testing, ie. @Leokolb experienced it and is reported via [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898936](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1898936) , but the final word is it's likely related to a bug I reported that **was** a much *larger & longer* issue...

You didn't say which ISO you used to install it (*original 20.04, later 20.04.1,  20.04.2 daily..*), and if you want to file a bug, please do so (*I'd also request you mention the bug report I've referenced or just link here, as it'll save me or whomever looks at it time by avoiding the searches I've just done..*)

---

