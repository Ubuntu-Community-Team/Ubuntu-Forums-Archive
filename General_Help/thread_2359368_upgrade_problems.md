---
title: "upgrade problems"
date: 2017-04-23
forum: General Help
---

### Post by hmiersch on 2017-04-23
hi. i'm trying to upgrade from 16.04 to 16.10 and then to 17.04. the problem is that i keep getting an error telling me that the upgrade needs 103 MB free on /boot. but the thing is, gparted says there are way more than 100 MB (more like 150) available on /boot. so whats going on here, and what can i do about it?

---

### Post by Bashing-om on 2017-04-23
hmiersch; Hello

As a guess it is the /boot partition that is full of old kernels.
Let's take a closer look and then see what there is to do.
Post back - Between code tags, please - the outputs of terminal commands:
```

df -h
df -i
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

We will not know
[INDENT][INDENT]until the tale is told
[/INDENT][/INDENT]

---

### Post by sp40140 on 2017-04-23
In addition to what @Bashing-om said..the upgrade process downloads more lots of files, they need to be stored while system is being upgraded. That takes up lots of space as well. That is the most likely reason for your error.
So, you should have to clean up some file and make room. Most likely candidates are old kernels and old log files from /var/log.

---

### Post by hmiersch on 2017-07-15
old kernels? is that why there are so many files with very similar names? the names only differ in the version number, like abi-4.4.0-72-generic and abi-4.4.0-75-generic. can i simply remove the old files? that would free up quite a bit of space...

---

### Post by deadflowr on 2017-07-15
> **hmiersch said:**
> old kernels? is that why there are so many files with very similar names? the names only differ in the version number, like abi-4.4.0-72-generic and abi-4.4.0-75-generic. 
yep
> can i simply remove the old files? that would free up quite a bit of space...
nope

**do not delete those files**, instead run any number of package management utilities to remove the associated packages that installed the files.

First utility to try would be 
```
sudo apt-autoremove
```
sometimes, but unfortunately not always, this will clear old and obsolete kernel images.

if that doesn't work you can try removing the old kernel a little bit more manually with 
```
sudo apt-get purge name-of-package1 name-of-package2
```
Bashing-OM gave you a command that will list all installed kernels, you can run that to see what kernel are installed.
Use the command
```
uname -a
```
to see which kernel you are currently using.
Do that so you do not accidentally remove it.

Maybe this will explain things better:
[https://help.ubuntu.com/community/RemoveOldKernels]("https://help.ubuntu.com/community/RemoveOldKernels")

---

### Post by hmiersch on 2017-07-16
i tried your > sudo apt-autoremove and it gave me an error. command not found or something. so i tried > sudo apt-get autoremoveand that did the trick. but then i ran into another problem: i tried to upgrade to 16.10 using the software updater, and it downloaded a lot of stuff, then it gave me this error: 

> Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.13+16.10.20160929.1-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.13+16.10.20160929.1-0ubuntu1_all.deb) Hash Sum mismatch

so this is for facebook, right? so what am i supposed to do with it? i don't use facebook, so why should i download something i'&#314;l never need?

---

### Post by Bashing-om on 2017-07-16
hmiersch; Hey ...

Still with the hash sum mismatch issue - after a bit of wait to see if the mirror updated ?

Make sure you now have operational head room on the system:
```

df -h
df -i

```

With known space available have a read:
[https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error)

They have an explanation of what might be going on and offer resolutions.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by hmiersch on 2017-07-17
> **Bashing-om said:**
> 
[https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error)


i went through that list but it didn't do me any good :-( i still get the same error message on the same facebook-plugin. what makes this so annoying is that facebook prevents me from upgrading to 16.10 but i want nothing to do with facebook.

so what can i do? is there a way to upgrade to 16.10 from the terminal?

---

### Post by Bashing-om on 2017-07-17
hmiersch; Welp !

What we do is get the exact error in context.

Post back - Between Code Tags - the outputs of the terminal commands:
```

sudo apt update
sudo apt full-upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
See how facebook plays into this and what we can do about it.

I do not expect much todo about it.

[INDENT][INDENT]we tell that tale when  we get to it
[/INDENT][/INDENT]

---

### Post by hmiersch on 2017-07-27
> **Bashing-om said:**
> 
Post back - Between Code Tags - the outputs of the terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

```

>>sudo apt update
[sudo] password for admin: 
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 306 kB in 1s (265 kB/s)                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```


```
>>sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libllvm3.8 linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-image-4.4.0-79-generic linux-image-extra-4.4.0-79-generic
  linux-signed-image-4.4.0-79-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  binutils
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 2,311 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.4 [2,311 kB]
Fetched 2,311 kB in 2s (1,109 kB/s)   
(Reading database ... 276655 files and directories currently installed.)
Preparing to unpack .../binutils_2.26.1-1ubuntu1~16.04.4_amd64.deb ...
Unpacking binutils (2.26.1-1ubuntu1~16.04.4) over (2.26.1-1ubuntu1~16.04.3) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up binutils (2.26.1-1ubuntu1~16.04.4) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...

```

i'm pretty sure that some lines are missing from the second one. unfortunately i closed the terminal before i realized that something was wrong...

but anyway, software updater offered me 17.04 instead of 16.10, so i tried to install it. but i got the same error on (a new version of) the same file. and i seem to remember that i had the same problem when i tried to upgrade from 14.04 to 16.04. how can there be the same error on the same file in every new version of ubuntu? something is wrong here. also,

---

### Post by mastablasta on 2017-07-27
> **hmiersch said:**
> i tried your  and it gave me an error. command not found or something. 

it should proably be 

sudo apt-get autoremove

---

### Post by hmiersch on 2017-07-28
> **mastablasta said:**
> it should proably be   sudo apt-get autoremove  as i said in the post you quoted from, i tried it and it did the trick.

---

### Post by hmiersch on 2017-08-20
i still have the same problem. and after posting the info requested by bashing-om 3 weeks ago i was hoping that someone would be able to point me in the right direction. but nothing.   do i have to install 17.04 from scratch?

---

### Post by deadflowr on 2017-08-20
> **hmiersch said:**
> i still have the same problem. and after posting the info requested by bashing-om 3 weeks ago i was hoping that someone would be able to point me in the right direction. but nothing.   do i have to install 17.04 from scratch?

Nothing we see from the last clean output for post #10 shows anything wrong and looks normal.

Are you running into the hash sum mismatch again?

Without what the current output shows we can do little.
Perhaps posts all output for the apt-get update, apt-get upgrade and df -h, and df -i commands (which Bashing-om asked for already, twice) so we actually see and understand what you mean.

---

