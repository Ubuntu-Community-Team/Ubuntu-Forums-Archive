---
title: "Can't copy to init.d folder"
date: 2007-01-30
forum: General Help
---

### Post by PaulFXH on 2007-01-30
Due to a problem I have with my GDM configuration, I am trying to copy the gdm from /usr/sbin/ to /etc/init.d/

However, I get this message:
```
cp: cannot create regular file `/etc/init.d/gdm': Permission denied

```

OTOH, I can readily copy the very same file to my Desktop.

I imagine this difficulty is related to the .d at the end of the init.d folder name but can somebody please explain this to me?

---

### Post by kebes on 2007-01-30
The problem is that you need "superuser" (root) privileges to copy files into important system folders. The way to do this is to put "sudo" in front of the command (sudo basically means "superuser do..."). So you would type:

sudo cp gdm /etc/init.d/gdm

The terminal will then ask for your password, and if you enter it, the copy will be performed.

Remember that "sudo" gives you all the power on your computer! Be careful with it, since you can break your computer if you use the wrong command!


Hope that helps.

---

### Post by bettlebrox on 2007-01-30
> **PaulFXH said:**
> Due to a problem I have with my GDM configuration, I am trying to copy the gdm from /usr/sbin/ to /etc/init.d/

However, I get this message:
```
cp: cannot create regular file `/etc/init.d/gdm': Permission denied

```

OTOH, I can readily copy the very same file to my Desktop.

I imagine this difficulty is related to the .d at the end of the init.d folder name but can somebody please explain this to me?

Why are you copying /usr/sbin/gdm to /etc/init.d/gdm?

/etc/init.d/gdm and /usr/bin/gdm are 2 very different files. The first is the startup script for gdm and the 2nd is the actual gdm binary/executable.

---

### Post by PaulFXH on 2007-01-31
Hi kebes
Yes, of course. I canot believe that I forgot about sudo.
Thanks for the reminder.

---

### Post by PaulFXH on 2007-01-31
Thanks bettlebrox but are they really *different* files?

This is a very long story but since you asked I'll present a much abbreviated version which you (or anybody else) are welcome to comment on.

I had been trying for a couple of days to install beryl but kept running into a problem with the nVidia driver not matching with the nVidia kernel. Because of the consequent "manipulations" I ended up with with the Xserver refusing to start and I was restricted to operating in Recovery Mode.

I then found that the gdm file from /etc/init.d/ had disappeared (I have no idea how or why) which seemed to have been the reason for the failure of GDM to startup.

However, by using the gdm file from /usr/sbin/ I was able to start the GDM from TTY1, so I had intended to copy the gdm from this folder to /etc/init.d/ to see if Ubuntu would then boot into GUI mode. And indeed it does (after I cottoned on to using sudo).

So, on this evidence it seems the files are exactly the same.

---

### Post by bettlebrox on 2007-01-31
```
$ file /etc/init.d/gdm  /usr/sbin/gdm
/etc/init.d/gdm: Bourne shell script text executable
/usr/sbin/gdm:   ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped
```


```
$ ls -l  /etc/init.d/gdm  /usr/sbin/gdm
-rwxr-xr-x 1 root root 2.6K 2006-10-08 16:44 /etc/init.d/gdm*
-rwxr-xr-x 1 root root 250K 2006-10-20 19:36 /usr/sbin/gdm*
```


Very different files indeed! /etc/init.d/gdm is a script that is used to startup & shutdown GDM. Probably the easist way to get it back is to reinstall gdm:
sudo apt-get install --reinstall gdm

Or, if you message me I'll forward you what is on my Edgy system.

---

### Post by PaulFXH on 2007-02-01
Thanks for your offer.
However, due to various other problems I had with this OS (all of which seemed to result from as yet unsuccessful attempts to install beryl), I have actually reinstalled Edgy.
So everything is fine now.
As I have a separate home partition, I didn't lose anything other than the 2-3 hours needed to do the re-install.
Nevertheless, I still remain puzzled that files with exactly the same name (gdm) can be very different.But certainly when I copied gdm from /usr/sbin/ to /etc/init.d/ what I wanted to happen (i.e. gdm to start at bootup) DID occur suggesting that there is at least some similarity between these files.
Thanks again for your comments.

---

