---
title: "System hibernates during startup"
date: 2019-10-16
forum: General Help
---

### Post by sarot2 on 2019-10-16
Hello,

I already had good experince with lubuntu in virtual machines but am having a little trouble on my 1st physical installation:

Asus Aspire One S150 (AtomN280; 1GB RAM)

I installed the current Lubuntu Image from USB (18.04.3 LTS) with standard installer (no advanced Settings) and it went all good. Lubuntu boots but:

When I power on the Netbook, it shows the boot-splash screen of lubuntu and then goes into hibernate-mode. After a few seconds I wake it up by any keyboard key and it continues to boot until the login screen. After entering my creds, it hibernates again. Waking it up again by keyboard key I am on my desktop. From now on everything is fine.

Has anyone an idea, how this behavior is caused and how to stop it?

Thx in advance

---

### Post by milesweb on 2019-10-16
Hold down Shift while booting to get to grub. Hit 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot.

---

### Post by guiverc on 2019-10-16
Rather than looking for clues in boot messages as @milesweb has indicated (*during boot*), I'd just scan `dmesg` for clues, next I'd also scan `journalctl`..

I suspect it sleeps rather than hibernates (hibernate requires a power-key to be pressed in my experience, and not a keystroke)

Since `dmesg` only contains boot messages (since cold-boot), I'd look for something like the following found in my journalctl for a recent 'sleep', then start looking backwards for clues..

```
Oct 15 00:31:21 d960-ubu2 systemd[1]: Reached target Sleep.
Oct 15 00:31:21 d960-ubu2 systemd[1]: Starting Suspend...

```
I don't know what caused it, but I'd hope to find clues in `dmesg` or `journalctl`, or at least clues on where I'd look next.

---

### Post by sarot2 on 2019-10-22
Thx for your hints. I copied the dmesg log and found a few entries about 'sleep' - but have no clue where to look next:

[https://paste.ubuntu.com/p/zz7b3zbg2M/](https://paste.ubuntu.com/p/zz7b3zbg2M/)

---

