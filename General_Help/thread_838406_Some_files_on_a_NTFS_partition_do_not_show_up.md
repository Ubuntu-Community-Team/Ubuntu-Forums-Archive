---
title: "Some files on a NTFS partition do not show up"
date: 2008-06-23
forum: General Help
---

### Post by Orestez on 2008-06-23
Hey.


Im successfully mounting a xp partition in ubuntu. Everything works, except that a couple of folders and files are simply not shown, as if they werent there. They are being shown in windows though. They do not contain any special character (first thought it was because of that) or otherwise "stand out"... they are mostly pictures and music. 

Anybody have encountered this before? Ive tried everything from the ntfs-config tool, manually editing fstab, from the terminal etc.

---

### Post by Orestez on 2008-06-24
bump?

---

### Post by chrisccoulson on 2008-06-24
How is the partition mounted? Is it automatically mounted, or have you added an entry to your /etc/fstab? If the latter, could you please post your fstab here?

Also consider this (from [http://www.ntfs-3g.org/support.html#questions]("http://www.ntfs-3g.org/support.html#questions")):
> **Missing, disappeared files or directories?**
or
**Why can't I see all filenames with national characters?**
or
**Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?**
This means that your operating system (OS) doesn't have the correct language specific settings (locale, LANG variable, LC_ALL, etc) thus some filenames can't be converted to your language and won't be visible. The reason can be:

[LIST]
[*]The locale setting wasn't configured during installation.
[*]Not the correct locale was configured.
[*]The configured value doesn't exist on the system.
[*]The OS configures the setting in a too late stage during the boot process, only after the NTFS volume was already mounted. 

The most common explanation is the latter one. This is why unmounting then mounting such volumes after boot often makes all filenames visible.

Solution: The OS vendor should move the language specific configuration to an earlier phase to precede the mounts of the NTFS volumes in time.

Workaround: NTFS-3G supports the 'locale' mount option which can be used to set the correct language value. You can see what locales you have on your system by using the following command:

```
locale -a
```

If you can't find the preferred setting then you must generate it, which is very distribution dependent. To do so, a package like glibc-i18ndata (openSUSE, Mandriva, ...) or locales (Debian, Ubuntu, ...) must be installed then enter the below command as root to generate the language_COUNTRY.UTF-8 locale. For example the Brazilian is:

```
localedef -i pt_BR -f UTF-8 pt_BR.UTF-8
```

Then you can use the "locale=pt_BR.UTF-8" option during mount.

If some of your softwares are not UTF8 ready then they will not show correctly the UTF8 filenames. Please consult your distribution documentation about how to enable full UTF8 support.

Status: Not NTFS-3G problem. Please ask your OS vendor to fix the boot time configuration problem. 

If you have specified an entry in your /etc/fstab, please try passing a 'locale=' option (in my case, I use 'locale=en_GB.utf8'). Have a look at [http://gentoo-wiki.com/HOWTO_NTFS_write_with_ntfs-3g]("http://gentoo-wiki.com/HOWTO_NTFS_write_with_ntfs-3g") for more info.

---

### Post by Orestez on 2008-06-24
Yes, I have tried both mounting it with an entry in fstab (will post that later, not on that comp now), and via the terminal. I have also tried out different locale settings already, as well as unmounting and mounting it again some time after booting. 

I can use locale-specific (ä,å  etc) characters just fine, and the filenames of the files that have vanished dont even contain such characters either (one folder for instance was just a date, 24.10 etc). I even renamed a file that wont show in Ubuntu in Windows to something really simple, and it still wont show up.

I will try again later today, even though I cannot see how this can be locale related... then again there seems to be no other possible reason. :confused:

---

