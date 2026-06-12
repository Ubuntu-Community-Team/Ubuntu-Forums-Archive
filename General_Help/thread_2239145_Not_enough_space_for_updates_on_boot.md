---
title: "Not enough space for updates on /boot"
date: 2014-08-12
forum: General Help
---

### Post by captainKrash on 2014-08-12
Software updater runs every day. I got a message today:

> The upgrade needs a total of 81.7 M free space on disk '/boot'. Please free at least an additional 16.7 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Suffice to say, I ran

```
sudo apt-get clean
```

It did not solve the problem. I did a bit of googling in order that I might be able to resolve on my own, but am a bit uncertain. Here are some (hopefully) useful outputs:

```
$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  107G   19G   84G  18% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.5G  4.0K  1.5G   1% /dev
tmpfs                        301M  1.2M  300M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.5G  152K  1.5G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M  162M   63M  73% /boot

```

```
$ uname -r
3.13.0-32-generic
```

```
$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.32.38                                        amd64        Generic Linux kernel image

```

I am guessing I need to run a command something like:

```
sudo apt-get purge linux-image-3.13.0-{24,29}-generic
```

Leaving 30 as the previous version and keeping 32 as the current version.

Would this be safe/advisable to run?

I've never encountered this issue before, Is this normal? Is there anything I can do to prevent a reoccurrence? 

Thanks for any advice!

---

### Post by Impavidus on 2014-08-12
Yes, that's how you can solve it. If apt-get complains that it cannot remove packages as long as 3.13.0-33 hasn't been installed, use dpkg directly to uninstall the old kernels:```
sudo dpkg --purge linux-image{,-extra}-3.13.0-{24,29}-generic
```

This is normal on a somewhat smaller /boot partition. Regularly remove the old kernels. They're supposed to be autoremovable, so regularly running```
sudo apt-get autoremove
```should work to prevent this problem.

---

### Post by captainKrash on 2014-08-12
Thank you for the reply. Given the output of uname -r, I guess 33 has not been installed:

```

$ uname -r
3.13.0-32-generic
```

So, it will be safe to run the command? Thank you

---

### Post by Impavidus on 2014-08-12
Yes, just don't uninstall 32 yet.

---

### Post by captainKrash on 2014-08-12
Thanks for the reply. Unfortunately, not so straight forward:

```
dpkg: dependency problems prevent removal of linux-image-3.13.0-24-generic:
 linux-image-extra-3.13.0-24-generic depends on linux-image-3.13.0-24-generic.

dpkg: error processing package linux-image-3.13.0-24-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-29-generic:
 linux-image-extra-3.13.0-29-generic depends on linux-image-3.13.0-29-generic.

dpkg: error processing package linux-image-3.13.0-29-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-3.13.0-extra-24-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-extra-29-generic which isn't installed
Errors were encountered while processing:
 linux-image-3.13.0-24-generic
 linux-image-3.13.0-29-generic
```

---

### Post by oldfred on 2014-08-12
Similar issue, user gave up, but created bug report:
[http://ubuntuforums.org/showthread.php?t=2235403](http://ubuntuforums.org/showthread.php?t=2235403)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1349172](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1349172)

This user had same issue, but logged in as another user with admin rights & it worked??
[http://ubuntuforums.org/showthread.php?t=2235697](http://ubuntuforums.org/showthread.php?t=2235697)

---

### Post by Impavidus on 2014-08-12
Oops, I had put the {,-extra} and the -3.13.0 in the wrong order. Fixed the command in my previous post. It should work now.

---

### Post by captainKrash on 2014-08-13
```
/dev/sda1                    236M   86M  138M  39% /boot
```

That got it, thanks - will attempt update now!

---

