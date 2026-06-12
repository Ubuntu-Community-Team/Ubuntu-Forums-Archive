---
title: "can't get sudo"
date: 2018-01-23
forum: General Help
---

### Post by chrischapman1973 on 2018-01-23
A new update came out to my system today and now I have no sudo privileges.  This is the error I get:

```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
```

ls -l /usr/bin/sudo produced the following result:

```
-rwxr-xr-x 1 gordy72 root 136808 Jul  4  2017 /usr/bin/sudo 
```

I have no idea how to fix this and it resulted from a simple Ubuntu update this morning.  I don't want to have to go back to windows but if this is going to happen as the result of an update idk.  Does anyone have any ideas?

---

### Post by slickymaster on 2018-01-23
Hello chrischapman1973, welcome to the forums

Please check this thread: [https://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set#471503](https://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set#471503)

---

### Post by Impavidus on 2018-01-23
That thread tells you to login as root. You can't do that directly in Ubuntu, but you can use recovery mode.

Use the grub menu to boot Ubuntu into recovery mode, then drop to a root shell. Remount the file system in read-write mode:```
mount -o rw,remount /
```Then execute the command in that thread and leave the root shell (use the exit command).

BTW, I've never seen anything like that go wrong in an update. Have you made sure that's the only file of which permissions or ownership were messed up? If there are others, fixing it may get really hard.

---

### Post by sisco311 on 2018-01-24
There is another setuid root app which you can use to run commands as root: pkexec. Assuming that the permission of pkexec are intact, run:
```
pkexec chown root:root /usr/bin/sudo
pkexec chmod 4755 /usr/bin/sudo
```to restore the original ownership and permissions of sudo.

> **Impavidus said:**
> BTW, I've never seen anything like that go wrong in an update. Have you made sure that's the only file of which permissions or ownership were messed up? If there are others, fixing it may get really hard.
+1

---

### Post by chrischapman1973 on 2018-01-24
Thank you so much for the help and the quick responses guys.

---

