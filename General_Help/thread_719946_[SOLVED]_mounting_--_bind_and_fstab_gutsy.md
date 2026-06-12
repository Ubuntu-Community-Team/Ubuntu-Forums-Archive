---
title: "[SOLVED] mounting -- bind and fstab gutsy"
date: 2008-03-09
forum: General Help
---

### Post by Oldsoldier2003 on 2008-03-09
running Ubuntu server 7.10 with jailkit 2.5

The situation is this, I have a sftp user that needs access to a single directory outside of the jail to upload files for an app. I've managed to work it out by mounting the directory inside the jail with  ```
mount </dir/path/to/needed_files> </jailusers/home/dir>  -o bind
```

I know that in Gentoo you can just edit the fstab to reflect:

```
</dir/path/to/needed_files> </jailusers/home/dir> none bind
```

then run mount -a to make it a persistent mount.  


the question is is this also doable in Ubuntu server? The reason I ask is I really don't want to mess with having to remount if there is a power failure or reboot. Its a "headless server" so if anyone could verify or deny this information I'd really appreciate it.

---

### Post by Oldsoldier2003 on 2008-03-10
further discussion in another thread shows this to be a valid way of solving the issue

[http://ubuntuforums.org/showthread.php?t=720520](http://ubuntuforums.org/showthread.php?t=720520)

---

