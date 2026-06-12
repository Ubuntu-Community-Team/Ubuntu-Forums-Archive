---
title: "unable to use sudo"
date: 2013-05-17
forum: General Help
---

### Post by mnadarasan on 2013-05-17
sudo: must be setuid root . this is the error message i get when i tried after using chown -r command
i tried booting in recovery mode and used the following commands
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
but it shows there is no such directory
i tried the su command
but password authentication shows failure even after typing correct pwd in terminal
i tried pkexec in terminal and it shows pkexec must be setuid root

---

### Post by scbingham on 2013-05-17
Not sure what your question is, did you delete sudo?
On my system (12.04 LTS) within /usr/bin I have:   -rwsr-xr-x 2 root root 71288 Feb 27 20:54 sudo

---

### Post by PowerBarry43 on 2013-05-17
hi

what is the output of:
```
ls -al /usr/bin/sudo
```

also unlless you have enabled the root account with 

```
sudo passwd
```

then I wouldn't expect su wouldn't work ;)

Barry

---

### Post by SlugSlug on 2013-05-17
what "chown -r command" ?!

---

### Post by Impavidus on 2013-05-17
chown -r, and now sudo is no longer owned by root. Did you by any chance try to change ownership of some system directories to yourself? In that case more things than just sudo will be broken. You'll have a hard time repairing everything. My standard advice if you really did that is to reinstall.

---

### Post by mnadarasan on 2013-05-18
-rwxr-xr-x 2 root root 69708 Feb 28 02:02 /usr/bin/sudo
this is output for ls -al /usr/bin/sudo
mnadarasan@mnadarasan-AcerPower-Series:~$ sudo passwd
sudo: must be setuid root
mnadarasan@mnadarasan-AcerPower-Series:~$ passwd
Changing password for mnadarasan.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged

the above error message for passwd

---

### Post by Impavidus on 2013-05-18
Boot into recovery mode, drop to a root shell and mount the file system rw (if necessary), just as instructed [here]("http://www.psychocats.net/ubuntu/resetpassword"), up to but not including the third screenshot. If you have you /usr on a separate partition, then mount that rw. You would know it if that is the case. Then use the command```
chmod 4755 /usr/bin/sudo
```
But I don't know what you did wrong and it's likely there are more problems.

Edit: If this doesn't work, please post the complete output here. There may be other things wrong with your computer. In fact, it may be that bad that reinstalling is the best option. I still don't know what you meant by the chown -r command you mentioned in your first post, but recursive chowns on a system directory can be pretty disastrous.

---

