---
title: "LVM2 commands can't find libreadline.so.5 and fail!"
date: 2020-02-19
forum: General Help
---

### Post by mbuell on 2020-02-19
I have  hard drive from a retired system that used LVM. I need to mount the drive to pull data off. I'm running 16.04 xubuntu. I installed LVM2 via apt, and rebooted. Vgscan and the other LVM2 commands all fail, as they can't find libreadline.so.5. I searched for all libreadline on the drive. Libreadline5 only appears ```
/var/cache/apt/archives/libreadline5_5.2+dfsg-3build1_amd64.deb
/var/lib/dpkg/info/libreadline5:amd64.list
/var/lib/dpkg/info/libreadline5:amd64.md5sums
/var/lib/dpkg/info/libreadline5:amd64.shlibs
/var/lib/dpkg/info/libreadline5:amd64.triggers
/var/lib/dpkg/info/libreadline6:amd64.list
/var/lib/dpkg/info/libreadline6:amd64.md5sums
/var/lib/dpkg/info/libreadline6:amd64.shlibs
/var/lib/dpkg/info/libreadline6:amd64.symbols
/var/lib/dpkg/info/libreadline6:amd64.triggers
```
Libreadline6 and libreadline7 do exist, but I assume they are different libraries, not just newer versions of 5. 

So, I'm lost. Need to mount this drive - and can't. Apt says libreadline5 is installed. I reinstall it. No change. 

How do I fix this?

---

### Post by mbuell on 2020-02-19
Well - that was quick. I think I found an answer here: > [There's a really dirty hack]("https://askubuntu.com/questions/1075656/error-while-loading-shared-libraries-libreadline-so-7-cannot-open-shared-objec") (not recommended, but not very dangerous) you could try if you just want to get past this step to see if you're going to hit another issue before you commit to upgrading, or you really can't upgrade right now. This is to make a symlink pointing to the older version of the library, so that the program thinks it's using libreadline.so.7 and is actually using libreadline.so.6:

sudo ln -s /lib/x86_64-linux-gnu/libreadline.so.6 /lib/x86_64-linux-gnu/libreadline.so.7
This might possibly make the program run. But it might also crash mysteriously without any meaningful error messages. If you leave the symlink like this, other programs you install from third party sources might also fail to report the missing dependency and crash mysteriously. You might forget what you did and wonder what is wrong with your silly system, so it's better only to try things like this for testing. You can always just delete the symlink libreadline.so.7 to get back where you started.

This answer indicates that libreadline6, 7, etc, are just later versions of the library. I reversed the link creation, making a link to the earlier version (5), that pointed to libreadline6. I did use ```
ldconfig -p | grep readline
``` to determine that libreadline6 is the active version.

Vgscan now works, but I'm not sure if this is an appropriate solution. I would appreciate feedback before marking this solved.

---

