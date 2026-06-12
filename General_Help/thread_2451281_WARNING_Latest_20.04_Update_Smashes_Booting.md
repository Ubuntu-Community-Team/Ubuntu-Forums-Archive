---
title: "WARNING: Latest 20.04 Update Smashes Booting"
date: 2020-09-30
forum: General Help
---

### Post by GhX6GZMB on 2020-09-30
Today, I ran a routine "apt update", "apt full-upgrade".

Now, after rebooting, my machine is practically dead. After the BIOS window I have a black screen with five message lines flashing in the upper left corner (I always have those, but they just flash once very shortly).

No key action could terminate this behaviour. In the end, I decided to do a new install from DVD.

Worked, and so did my Timeshift backup and I was back in business (took an hour, though).

Just for the hell of it, I did a new "apt update" and "apt full-upgrade".

Again the same mess! Boot and hangup with the same blinking messages on my screen and a practically dead PC.

**What's going on here? Did someone inject malicious code into the repositories?**

---

### Post by deadflowr on 2020-09-30
Well, if you have timeshift and can revert back with ease why not take a look at what
```
apt list --upgradeable
```
shows will be updated.

---

### Post by dinkidonk on 2020-10-01
There was a recent update of "shim" which is a "pre-bootloader" used with UEFI and secure boot to load GRUB. My guess would therefore be that whatever causes your misery has something to do with secureboot, and may be a hardware related incompatibility.

I've updated shim on my system (Kubuntu 20.04) and have not experienced any issues, so it is not a general issue.

---

### Post by tea for one on 2020-10-01
There is a difference between [COLOR="#0000FF"]sudo apt upgrade[/COLOR] and [COLOR="#006400"]sudo apt full-upgrade[/COLOR]

Apparently, [COLOR="#006400"]sudo apt full-upgrade[/COLOR] also removes packages.

I must admit, I also find it a bit confusing - here is some info:-

[https://askubuntu.com/questions/1246828/is-apt-full-upgrade-safe](https://askubuntu.com/questions/1246828/is-apt-full-upgrade-safe)

I haven't yet encountered your problem yet, probably because I only use [COLOR="#0000CD"]sudo apt upgrade[/COLOR]

---

### Post by GhX6GZMB on 2020-10-01
After a full evening of re-installing (including running "badblocks" to check for a disk error etc.) and restoring, I'm now up and running again.

This is the output of "sudo apt update":

```
macro@macro-pc:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  imagemagick-6-common libegl-mesa0 libgbm1 libgl1-mesa-dri libglapi-mesa libglx-mesa0 libldb2 libmagickcore-6.q16-6 libmagickwand-6.q16-6
  libsane libsane-common libsmbclient libuv1 libwbclient0 libxatracker2 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers opera-stable
  samba-libs sane-utils
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 101 MB of archives.
After this operation, 2.733 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

I don't see anything that would kill my PC there, though I've no idea what "imagemagick" is.

Just ran "sudo upgrade" with one error:

```
update-inetd: warning: cannot add service, /etc/inetd.conf does not exist
```

No idea what it means. I'll now try to reboot after these two super-dangerous commands and see what happens.

---

### Post by GhX6GZMB on 2020-10-01
UPDATE:

After the "sudo update" and "sudo upgrade", I rebooted my PC

It's dead again with exactly the same symptoms :( :( :(

So it's got nothing to do with "apt upgrade" vs. "apt full-upgrade". Something gets upgraded that kills my boot totally.

---

### Post by GhX6GZMB on 2020-10-03
OK, it seems to be a problem with a PPA.
[B]
How this can prevent booting is a total mystery to me.[/B]

The PPA link for Kicad has changed, after modifying it to the new PPA and upgrading, my PC operates as before. Upgrading using the old PPA apparently blocked booting.

Can a wrong PPA really prevent a PC from booting? I'm shocked. I've spent hours on this problem!!


PS: please ignore the attachment(wrong file). But this site does not allow correcting mistakes :(

---

### Post by oldfred on 2020-10-03
Standard rule for upgrading is to remove all proprietary drivers, all ppas and have system fullly updated & working. Then users rarely have issues.
Often drivers or ppas may need to be different after an upgrade.

But a normal update should not change anything unless the ppa was changed. But each user is responsible for ppas as they are not part of standard Ubuntu repository and verified to work.

---

### Post by tea for one on 2020-10-03
> **ml9104 said:**
> 

Can a wrong PPA really prevent a PC from booting? I'm shocked. I've spent hours on this problem!!

A wrong ppa preventing a PC from booting is a new one for me.

Did you ever find anything about your previous upgrade error message?

```
update-inetd: warning: cannot add service, /etc/inetd.conf does not exist
```

Anyway, well done for persevering and finding the culprit.

---

### Post by GhX6GZMB on 2020-10-04
> **tea for one said:**
> A wrong ppa preventing a PC from booting is a new one for me.

Did you ever find anything about your previous upgrade error message?

```
update-inetd: warning: cannot add service, /etc/inetd.conf does not exist
```

Anyway, well done for persevering and finding the culprit.

No, but it worries me a bit. Something wants to add a network service, but I don't have any services that I want to offer with inetd. An attack vector?

Anyway, it's just a warning, and friendly one at that, as it doesn't start any inetd services.

Also, it didn't show up again after resolving the PPA problem. Strange...

---

