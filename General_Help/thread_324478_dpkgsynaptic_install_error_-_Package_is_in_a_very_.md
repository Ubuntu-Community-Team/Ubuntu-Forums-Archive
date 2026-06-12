---
title: "dpkg/synaptic install error - Package is in a very bad inconsistent state"
date: 2006-12-23
forum: General Help
---

### Post by huang earnie on 2006-12-23
Trying to install Java5 through synaptic, and it keeps freezing up.  i have to reboot and upon reopening synaptic it shows this error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. did that, nothing seems to happen. tried removing the files that synaptic is struggling with, sun-java5-bin and sun-java5-jre.  when i tried to remove through symantic i got this *E: sun-java5-bin: Package is in a very bad inconsistent state - you should* (???thats it, seriously).  also followed advice [here]("http://ubuntuforums.org/showthread.php?t=324402&highlight=dpkg")  but to no avail....

---

### Post by taurus on 2006-12-23
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install sun-java5-bin
```

---

### Post by huang earnie on 2006-12-23
```
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
```

---

### Post by taurus on 2006-12-23
> **huang earnie said:**
> ```
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
```
What command did you run to get the above message?

---

### Post by huang earnie on 2006-12-23
i pasted in exactly what you posted above.  the contents of my previous post is what i get.  also tried the same lines again but changed to: sudo aptitude install sun-java5-jre....that gave the same error (except switched java5-jre and java5-bin).

---

### Post by taurus on 2006-12-23
How about

```
sudo aptitude remove sun-java5-jre
```

---

### Post by huang earnie on 2006-12-23
looks like basically the same error.  

```
The following packages will be REMOVED:
  sun-java5-jre
0 packages upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

```

---

### Post by huang earnie on 2006-12-24
suspect there may be probs with the multiverse or other stuff in sources.list.  changed a couple things, then ran:

```
sudo aptitude update
```

and got this error at the end:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

```

ideas, pleeeeeease?

---

### Post by taurus on 2006-12-24
Well, let's have a look at your /etc/apt/sources.list then!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by huang earnie on 2006-12-24
```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://us.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listendeb http://www.getautomatix.com/apt edgy main

```

---

### Post by taurus on 2006-12-24
What's the output of these two commands from a terminal then?

```
sudo find / -name sun-java5-jre* -print
sudo find / -name sun-java5-bin* -print
```

---

### Post by benjo316 on 2006-12-27
I have a similar problem with a different package.

When I try to remove it I get:

```
The following packages are unused and will be REMOVED:
  libqt3-mt 
The following packages will be REMOVED:
  wpasupplicant 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 9613kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing wpasupplicant (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
(Reading database ... 120289 files and directories currently installed.)
Removing libqt3-mt ...
Aborted (core dumped)
```

 When I used the commands (Substituting for my problem package) I got this output:
```
nobu@nobu-laptop:~$ sudo find / -name wpasupplicant* -print
/var/cache/apt/archives/wpasupplicant_0.5.5-3v1ubuntu4_i386.deb
/var/lib/dpkg/info/wpasupplicant.conffiles
/var/lib/dpkg/info/wpasupplicant.list
/var/lib/dpkg/info/wpasupplicant.md5sums
/var/lib/dpkg/info/wpasupplicant.postinst
/var/lib/dpkg/info/wpasupplicant.postrm
/etc/default/wpasupplicant
/home/nobu/Desktop/wpasupplicant
find: WARNING: Hard link count is wrong for /proc/10562: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: /proc/10567/task: No such file or directory
find: /proc/10567/fd: No such file or directory

```

---

### Post by BLTicklemonster on 2007-01-01
We're screwed fellas. I tried to install opera and all this is happening to me. I can't find an answer anywhere.

---

### Post by BLTicklemonster on 2007-01-01
Argh. Everytime I give up, I find the answer....


[http://ubuntuforums.org/showpost.php?p=1720900&postcount=7](http://ubuntuforums.org/showpost.php?p=1720900&postcount=7)

---

### Post by rudiz on 2007-01-01
The error messg indicate that you have to close synaptic. You can not use apt-get and synaptic at the same time.

---

### Post by BLTicklemonster on 2007-01-01
In my case, there was nothing else open. I tried the installation with the installer (gdebi), and half way through it stopped with an error. Until I logged off and back on, it kept saying that something running was keeping it from working. After logging off and back on, it started giving me all kinds of strange errors. It was like, even though services didn't show it running, synaptic or update kept running anyway. Or so the computer thought.

Anyway, dpkg -i took care of that. I guess it's a bug with gdebi.

---

### Post by benjo316 on 2007-01-02
> **benjo316 said:**
> I have a similar problem with a different package.

When I try to remove it I get:

```
The following packages are unused and will be REMOVED:
  libqt3-mt 
The following packages will be REMOVED:
  wpasupplicant 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 9613kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing wpasupplicant (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
(Reading database ... 120289 files and directories currently installed.)
Removing libqt3-mt ...
Aborted (core dumped)
```

 When I used the commands (Substituting for my problem package) I got this output:
```
nobu@nobu-laptop:~$ sudo find / -name wpasupplicant* -print
/var/cache/apt/archives/wpasupplicant_0.5.5-3v1ubuntu4_i386.deb
/var/lib/dpkg/info/wpasupplicant.conffiles
/var/lib/dpkg/info/wpasupplicant.list
/var/lib/dpkg/info/wpasupplicant.md5sums
/var/lib/dpkg/info/wpasupplicant.postinst
/var/lib/dpkg/info/wpasupplicant.postrm
/etc/default/wpasupplicant
/home/nobu/Desktop/wpasupplicant
find: WARNING: Hard link count is wrong for /proc/10562: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: /proc/10567/task: No such file or directory
find: /proc/10567/fd: No such file or directory

```

I (Somehow) fixed mine by opening aptitude ```
sudo aptitude
``` and then just plain uninstalling it... Kinda strange but it worked anyway.:-k 

Hope that helps. heheh

---

### Post by Stemp on 2007-02-13
ooops wrong thread, sorry

---

### Post by omkarwagh on 2007-09-11
run the thing in the terminal. ive had the same error happen to me thrice and i guess this is what i did

look very closely in the error messages. all three times with me at least it said something like some particular file is missing or does not exist.
solution:- simply create a blank file of that name in the directory where the error occurs. then ask dpkg to remove the package. that worked for me at least.

---

