---
title: "Bash alias mounting iso"
date: 2013-02-04
forum: General Help
---

### Post by dwlamb on 2013-02-04
Based on a command that worked properly, I tried creating the  following alias:
```
alias m20='sudo mount -o loop,ro -t iso9660 $1 /mnt/iso0'
```However, when I execute it, I recive this message "ioctl: LOOP_SET_FD: Invalid argument".  Execution was in the form of
```
m20 /home/dan/images/DVD-005.iso
``` plus variations with single or double quotes.  In all cases, I received that error message.  Yet, if I enter   ```
sudo mount -o loop,ro -t iso9660 /home/dan/images/DVD-005.iso /mnt/iso0
``` the image mounts without error.

---

### Post by schragge on 2013-02-04
Aliases in bash don't allow parameters like $1.

If you know where all images you want  to mount are located, enter them as /mnt/iso0, /mnt/iso1 etc. in /etc/fstab and use
```
alias m20='sudo mount /mnt/iso0'
```
Alternatively, write a function instead of alias:
```
m20(){ sudo mount -o loop,ro -t iso9660 "$1" /mnt/iso0;}
```
An awkward way to do this in an alias is by invoking a shell from there:
```
alias m20="sh -c 'sudo mount -o loop,ro -t iso9960 \"\$0\" /mnt/iso0'"
```

---

