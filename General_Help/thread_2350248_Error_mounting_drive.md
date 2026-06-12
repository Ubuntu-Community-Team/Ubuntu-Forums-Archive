---
title: "Error mounting drive"
date: 2017-01-22
forum: General Help
---

### Post by talljustin on 2017-01-22
Hi all, I get an error when mounting a EXT4 drive in ubuntu:
```
Error mounting system-managed device /dev/sdc1:Command-line 'mount "mnt/Movies4 exited with non-zero exit status 32: mount:mount dev/sdc1 on /mnt/Movies4 failed:Bad message (udisks-error-quark,0)
```

any help would be amazing, ive never seen this error and google isnt much help as it all relates to other issues not this exact one.

---

### Post by DuckHook on 2017-01-22
Welcome to the forums, talljustin.

Please post verbatim the command you are trying to use, as well as output of:```
sudo blkid
``````
sudo parted -l
``````
cat /etc/fstab
``````
ls -laF /mnt
```
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

