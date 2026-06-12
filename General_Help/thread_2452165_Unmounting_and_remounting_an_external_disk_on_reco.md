---
title: "Unmounting and remounting an external disk on reconnect"
date: 2020-10-17
forum: General Help
---

### Post by poisonborz on 2020-10-17
I have a server, from which I host a few directories on an external hdd. I'd like to just yank out the disk any time I want (it's why it is external) without any prior preparation.

- on dismount: force unmount and remove the mount point, whatever process uses it
- on mount: mount it again

Is dismount like this possible without crashing my server?
I tried to write udev usb mount rules plus shell scripts (on add and remove), but:
- for remove/dismount, a umount -l does not work and the syslog just log disk errors whenever I try to to access the drive
- for add, mounting doesn't seem to work from the shell script. Yet after typing the command manually the mount occurs properly.

Is there a better strategy for this?

---

### Post by Tadaen_Sylvermane on 2020-10-17
Autofs or systemd automounting. Will only be mounted when its being actively used by the system.

---

