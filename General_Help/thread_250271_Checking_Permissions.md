---
title: "Checking Permissions"
date: 2006-09-03
forum: General Help
---

### Post by cssutto on 2006-09-03
Googling the other day, I ran across a script that would check the systemm permissions and reset those that were not correct.

I did not care to try it since it was set up for RedHat or something similar and the file structure would not be the same.

Is there anything similar for Ubuntu?

CSSJR

---

### Post by apiper on 2006-09-04
Why, have you been changing the permission of system files at random? If you haven't then I wouldn't worry about it, as all system files have the correct permissions set by default.

---

### Post by taurus on 2006-09-04
I don't know if I trust that kind of a program unless I know darn sure it doesn't do some funny business with my machine...  If you don't go crazy on your machine with the sudo command, then won't worry about it!

---

### Post by cssutto on 2006-09-05
apiper:

Well, for instance rkhunter gives this:

* Application version scan
gpg: WARNING: unsafe enclosing directory ownership on configuration file `/home/claude69694/.gnupg/gpg.conf'
   - GnuPG 1.4.2.2                                            [ Unknown ]
   - OpenSSL 0.9.8a                                           [ OK ]
   - Procmail MTA 3.22                                        [ OK ]
   - OpenSSH 4.2p1     


Since I never use encryption, I didn't even know the files existed.

And do you know that every package you downloaded and installed, you set the permissions correctly?

CSSJR

---

### Post by apiper on 2006-09-06
Hmmm - I get the same message from rkhunter for my gpg.conf file. This kind of has me stumped, as the ownerships of the enclosing directories look fine to me:
```
$ ll / | grep home
drwxr-xr-x   4 root root  4096 2006-09-03 21:55 home

$ ll /home | grep apiper
drwxr-xr-x 83 apiper apiper 4096 2006-09-06 09:31 apiper

$ ll -a /home/apiper | grep .gnupg
drwx------  2 apiper apiper    4096 2006-09-06 10:17 .gnupg
```

I did a bit of googling and found this:
[https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043123.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043123.html)

> ...
> 2.) Security Advisories -> WARNING!
> * gpg: unsafe ownership on /home/user/.gnupg/gpg.conf
> 
> Question: How to understand that? I just set up gpg slightly, not
> making any own preferences.

normally i already do a chmod 700 /home/* during boot-up
also this looks pretty harmless

I have to say that I agree with this guy's opinion - its pretty harmless, as the permissions are pretty much secured. I'm not going to lose sleep over read-access to my home dir...

---

### Post by cssutto on 2006-09-06
Interesting link because it also gets into hidden files.

My next question was going to be about this from rkhunter.

 Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)

I looked.  But how am I to know what to look for.  There must be hundreds of files in those directories.

But then how can we say that it is harmless?  rkhunter says that hidden files are very suspicious.

I sent an email requesting information and have as yet heard nothing.

CSSJR

---

