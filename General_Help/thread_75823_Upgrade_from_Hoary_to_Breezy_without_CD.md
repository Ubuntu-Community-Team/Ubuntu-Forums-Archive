---
title: "Upgrade from Hoary to Breezy without CD?"
date: 2005-10-14
forum: General Help
---

### Post by Svip on 2005-10-14
I don't know if this is the wrong sector to post this in. But I'm having trouble upgrading my Hoary.

First I tried the old from Warty to Hoary with apt-get dist-upgrade.

Instead I replaced "hoary" with "breezy" in /etc/apt/sources.list

However, when I do apt-get update, I get the following errors:

```
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com breezy/main Packages
  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages - open (2 No such file or directory)
Fetched 638kB in 22s (28,9kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages - open (2 No such file or directory)Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I tried ignoring that, and did apt-get dist-upgrade anyway.

However, when I had my system rebooted, my /dev file for my cdrom was suddenly gone, so burning a CD suddenly wasn't an option. And no, Breezy wasn't installed, still Hoary. :(

Here is my etc/apt/sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

I really want to upgrade, but I just feel lost now. :(

---

### Post by gdcondor on 2005-10-14
i've the same problem here... but didn't try to force the upgrade

---

### Post by Svip on 2005-10-14
Okay, I fixed the problem.

I did
```
$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

And now my system is upgrading correctly! :D

---

### Post by Doctoxic on 2005-10-14
i cannot upgrade either

i tried the:
$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get dist-upgrade

but it didn't upgrade

should i have changed Hoary to Breezy in sources list?

Can someone post a definitive step by step guide for us newbies on how to upgrade without a CD

many thanks

Doc

---

### Post by Strangerdave on 2005-10-14
I assumed that you just replaced the hoary repositories with breezy, (easy enough to do using the "find" "replace" method) then do a apt-get update, 
then apt-get dist-upgrade

It worked seemlessly for me, and I have yet to find a problem with any of the programs.  I should say though that my machine is quite basic.

-SD-

---

