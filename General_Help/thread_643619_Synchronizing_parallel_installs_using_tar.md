---
title: "Synchronizing parallel installs using tar"
date: 2007-12-18
forum: General Help
---

### Post by thelatinist on 2007-12-18
I recently moved my Ubuntu installation from the last to the first partition on my hard drive using tar.  I kept my original install on my hard drive while I checked to make sure the move hadn't caused any problems, and edited my grub menu to allow me easy access to either.  This has given me an idea: why not keep this original backup synchronized with my main install every couple of weeks so I will have a backup install for trouble shooting purposes?

When I'm booted into my main install, I have the backup install partition auto-mounted at /media/system_backup; when I have my backup install booted, I have my main install mounted at /media/system_main.  Now all I want is to be able to synchronize the two.

The command I am thinking about using for this purpose is:

```
sudo tar cvfp - --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys / | ( cd /media/system_backup; tar xvfp -)
```

Does this look like it would work?  Can anyone foresee any problems?  Suggestions and comments are welcome.

(Please note: I won't be using this as an alternative to regular system backups, of course; just as an extra precaution.)

---

