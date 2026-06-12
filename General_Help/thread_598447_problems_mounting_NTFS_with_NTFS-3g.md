---
title: "problems mounting NTFS with NTFS-3g"
date: 2007-10-31
forum: General Help
---

### Post by frankp_live on 2007-10-31
Im having a small problem mounting my windows partitio in ubuntu 7.10 64 bit version.
I have followed the tutorial [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009), and my fstab file looks like this:
> /dev/sda1 /media/windowd ntfs-3g defaults,locale=en_DK.utf8   0    0
/dev/sda1 is the windows partition, i know that for sure. The windows partition does not show up anywhere, and when i look into the /media/windowd folder, it is empty.

When trying to run "sodu mount -a" i get > $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:


when writing "sudo umount /dev/sda1" i am told that the device is not mounted.

What should i do?

thank you

---

### Post by Maestro23 on 2007-10-31
Did you have an improper shutdown when you were last in Windows?

---

### Post by frankp_live on 2007-10-31
About a week ago, windows crashed for no appearent reason. After having done nothing new, play som albums, tjeck my mail etc i cleanly shut down windows XP, in the morning, windows stops at the startup screen. I am able to start in safemode, but nothing looks wrong, and nothing has been changed.

short answer, yes :)

---

### Post by Maestro23 on 2007-10-31
> **frankp_live said:**
> About a week ago, windows crashed for no appearent reason. After having done nothing new, play som albums, tjeck my mail etc i cleanly shut down windows XP, in the morning, windows stops at the startup screen. I am able to start in safemode, but nothing looks wrong, and nothing has been changed.

short answer, yes :)

So, you can't cleanly boot into Windows?  That has to be corrected before you can access the NTFS  drives/partitons from Ubuntu.

This has happened to me before.  Didn't have a clean shutdown in XP.  Booted up Ubuntu and it stated a similar problem like yours.  Had to boot back up into XP, properly shutdown.  After that, everything was fine.

---

### Post by frankp_live on 2007-10-31
I have booted windows up in safe mode, the only thing i can get to work, and shut it down the proper way, but it still doesnt work :(

I have no idea about what is wrong with my windows partition, but i have a great deal of files on it i would like to save.

---

### Post by dayanandasaraswati on 2007-10-31
i also have the same problem when i hibernate windows and try to mount ntfs in linux. What can i do to correct dis problem..?

---

### Post by cdenley on 2007-10-31
```

sudo ntfsfix /dev/sda1

```

I'm not sure if ntfsprogs is installed by default. If not
```

sudo apt-get install ntfsprogs

```

---

### Post by dayanandasaraswati on 2007-10-31
thank you..i'll try doing it..

---

### Post by frankp_live on 2007-10-31
Thank you very much, the ntfsfix worked it out. Is there a simple answer to what was the problem?

thank you again for helping

---

### Post by gbmsgb on 2007-11-04
> **cdenley said:**
> ```

sudo ntfsfix /dev/sda1

```

I'm not sure if ntfsprogs is installed by default. If not
```

sudo apt-get install ntfsprogs

```

Will any of these remove the windows hibernation file? - ie when I execute this, will I be able  to shutdown Ubunto and then resume Windows from hibernation? (I am running of the LiveCD 7.10)?
Thank you

---

