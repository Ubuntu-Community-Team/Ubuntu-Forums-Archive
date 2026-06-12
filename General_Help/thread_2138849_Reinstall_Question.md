---
title: "Reinstall Question"
date: 2013-04-25
forum: General Help
---

### Post by moosehead11 on 2013-04-25
Hello

Possibly a silly question but i guess it never hurts to ask.  I am currently running Ubuntu Server 12.04 but it appears that it has become corrupted and i can not do any updates.  In my setup i have two hard drives running one for the OS and one for storage.  What i am wondering is if i do a fresh install of 13.04 on the OS drive will i have any data lose on the Storage drive?  I know in Windows its not an issue but i have never done this with Ubuntu

thanks

---

### Post by sudodus on 2013-04-25
I would stay with 12.04 for Ubuntu Server because it is a long time support version, unless there is some particular software, where you need a newer version, that would come with Raring. It's not that I dislike Raring, on the contrary, I have helped testing the Lubuntu flavour during the last weeks (from beta to final release).

So, I suggest that you reinstall 12.04 if necessary (start from the newest point release 12.04.2). But first you should try to repair the current version. The following list of commands was originally posted by *oldfred*
```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by moosehead11 on 2013-04-25
> **sudodus said:**
> I would stay with 12.04 for Ubuntu Server because it is a long time support version, unless there is some particular software, where you need a newer version, that would come with Raring. It's not that I dislike Raring, on the contrary, I have helped testing the Lubuntu flavour during the last weeks (from beta to final release).

So, I suggest that you reinstall 12.04 if necessary (start from the newest point release 12.04.2). But first you should try to repair the current version. The following list of commands was originally posted by *oldfred*
```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```


Thanks...will have to try this later as it appears that i am getting errors trying to resolve any ubuntu.com sites

If i were to do a fresh install of 12.04 would i have to worry about losing the data on my storage drive?

Edit:  turns out the resolving issue had to do with the DNS in my server crapping out...tried your suggested fix but still get the same error when running updates

"dpkg: warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `powermgmt-base' missing, assuming package has no files currently installed.
(Reading database ... 160414 files and directories currently installed.)
Preparing to replace tzdata 2012b-1 (using .../tzdata_2012e-0ubuntu2_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2012e-0ubuntu2_all.deb (--unpack):
 unable to remove obsolete info file `/var/lib/dpkg/info/tzdata.postre': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2012e-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

---

### Post by sudodus on 2013-04-26
tzdata is time-zone-data. See for example ```
man tzfile
```

Try again to run the following commands
```

# fix Broken packages -f
sudo apt-get -f install
sudo dpkg --configure -a

```
or
```
sudo apt-get purge tzdata
sudo apt-get install tzdata

```
After that you may need to reset the local time to be correct for your time zone again.

---

