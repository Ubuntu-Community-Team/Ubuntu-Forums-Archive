---
title: "Maintain symlinks to directory on tmpfs across reboot?"
date: 2013-12-03
forum: General Help
---

### Post by raptir on 2013-12-03
I am running Ubuntu on an SSD and have set up /tmp as tmpfs to prevent unnecessary writes for temporary files. I am trying to move Chrome's cache directory to /tmp so that it will be kept in RAM rather than on the disk. My first instinct was to use a symlink from the Chrome cache directory to a directory on /tmp (/tmp/chrome/cache). The issue that I should have foreseen is that /tmp/chrome/cache is deleted on every reboot and thus the symlink is broken each time. I've thought of a couple solutions but I'm wondering if there's anything I'm missing:

[LIST]
[*]Add commands to rc.local to create the directories I need on boot
[*]Edit fstab to mount the standard chrome cache directory as tmpfs
[/LIST]

The second option concerns me since I'm not sure what would happen if the chrome cache directory was deleted and I didn't edit fstab. Would the system handle it well if you try to mount a file system on a directory that doesn't exist?

The first option seems OK but a bit hacky. Is there any better way to do this?

---

### Post by PaulBx on 2013-12-03
This might help:

[http://ubuntuforums.org/showthread.php?t=991205](http://ubuntuforums.org/showthread.php?t=991205)

One might reasonably assume Chrome has a similar facility. Or try googling about it...

---

