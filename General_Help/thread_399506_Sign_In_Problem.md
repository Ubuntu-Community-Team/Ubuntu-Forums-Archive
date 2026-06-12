---
title: "Sign In Problem"
date: 2007-04-02
forum: General Help
---

### Post by KerryeBerrye on 2007-04-02
I just installed Ubuntu this morning . Started it up. entered user name: ubuntu password: ubuntu
then I get:
User name or password incorrect.  i tried with and without caps lock: no luck. 
PLEASE HELP

---

### Post by taurus on 2007-04-02
Did you install with the alternate CD?  If that's the case, your login name is oem and use the same password that you've created during the installing.  Once you log in, you need to run this command to create an actual account for you to use from then on.

```
sudo oem-config-prepare
```

---

### Post by KerryeBerrye on 2007-04-02
Thanks. :) 
Gonna reboot and try now

---

### Post by KerryeBerrye on 2007-04-02
I tried that and it did not work now when I reboot. i get
initramfs/ type help
when i type help i get:

Comands:
alias bg break cd cddir command continue echo eval exec exit export false fg getopts hash help jobs kill let local pwd read readonly return set shift times trap true tyoe ulimit umask unalias unset cat chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep env expr false fbset fdcflush fgrep grep hostname ifconfig ip kill In loadfont loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt printf ps pwd readlink reset tm rmdirsed setkeycodeds sh sleep sort stat sync tail tee test touch tr tru tty umount uname uniq yes

I hope i got them all correct.
Please help!!

---

### Post by KerryeBerrye on 2007-04-02
the problem is worse

---

