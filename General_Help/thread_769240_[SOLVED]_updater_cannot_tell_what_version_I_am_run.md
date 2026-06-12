---
title: "[SOLVED] updater cannot tell what version I am running"
date: 2008-04-26
forum: General Help
---

### Post by mandrill on 2008-04-26
trying to upgrade to 8.04 today, all good to go - all backups on slave,
separate /home partition.......I get this - "can't guess metapackage" with the following addenda - "non-ubuntu software, or, several other reasons, you need to install these programs thru synaptic....excuse me, but HUH?

---

### Post by ibuclaw on 2008-04-26
How are you trying to upgrade by the way?

There are one of a few several way.

1)
```
sudo update-manager -d
```

2) Download Ubuntu Alternate ISO. Burn to Disc and mount.
Then enter /media/cdrom directory and type the command:
```
sh cdromupgrade
```

3) Switch repositories in the /etc/apt/sources.list file to Hardy
```

sudo apt-get update
sudo aptitude -t hardy full-upgrade
*or*
sudo apt-get install ubuntu-desktop

```

4) Re-format "/" partition and install with LiveCD

5) Re-format "/" partition and install with Alternate CD.


All of those options are sound. But in general, a fresh install (option 4 or 5) is better for you than an upgrade.

Regards
Iain

---

### Post by chrisccoulson on 2008-04-26
Have you disabled all third party repositories? Have you got lots of software installed from third party repositories or from deb packages that you have downloaded from websites?

---

### Post by mandrill on 2008-04-26
> **chrisccoulson said:**
> Have you disabled all third party repositories? Have you got lots of software installed from third party repositories or from deb packages that you have downloaded from websites?

Yep. that's what I'm guessing. I'll just go for the clean install.

Thanks guys!

---

