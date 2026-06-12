---
title: "apt-get upgrade problems"
date: 2013-01-30
forum: General Help
---

### Post by Rotto on 2013-01-30
Hello fellow Ubuntu people!

I'm having trouble updating my ubuntu install, because of what looks like a dependency issue and I was hoping someone could give me a hand.

I'm running (K)Ubuntu 12.04.1 LTS, which was last updated less than a week ago. Thank you for this OS by the way, it's perfect for me.

When I run *sudo apt-get update* and *sudo apt-get upgrade* I am shown the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.1 is installed
E: Unmet dependencies. Try using -f.

```

Then, after running *sudo apt-get -f install initramfs-tools* I am shown this (the same happens for *sudo apt-get -f upgrade*):

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/49.0 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            dpkg: dependency problems prevent configuration of linux-image-3.2.0-36-generic:
 linux-image-3.2.0-36-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-36-generic; however:
  Package linux-image-3.2.0-36-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.36.43); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                      No apport report written because MaxReports has already been reached
                        Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-36-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I haven't installed anything for a while apart from updates using the usual update and upgrade procedure and I don't use any PPA's.

I don't know if it's relevant, but my only unique configuration was that my install is in an encrypted LVM - but that was done early last year and I haven't had problems before, and /tmp is mounted as noexec (but I undo that and reboot every time I upgrade the kernel - as it is now).

Any help would be greatly appriciated.

---

### Post by dino99 on 2013-01-30
is it a pure genuine install ? or have you also added some third party package(s) ?

---

### Post by Rotto on 2013-01-30
Hi dino99,

It's a normal install with the main, universe, multiverse, backports (strange, I don't remember choosing that one), partner and security repositories.

No other repositories or PPA's.

Only thing installed from source is Truecrypt.

---

### Post by furything on 2013-01-30
If you look here
[https://launchpad.net/ubuntu/quantal/+package/initramfs-tools](https://launchpad.net/ubuntu/quantal/+package/initramfs-tools)
Then you should be able to download the matching tools and tools bin .deb installers

You may have to remove bin if is refuses to let you upgrade and then install from the package.

Let me know how you get on?

---

### Post by Rotto on 2013-01-30
I don't suppose you could walk me through what you think I should do? I don't know which package to install or what to do with it.

---

### Post by furything on 2013-01-30
Download
[http://launchpadlibrarian.net/102374523/initramfs-tools_0.99ubuntu13_all.deb]("https://launchpad.net/ubuntu/quantal/amd64/initramfs-tools/0.99ubuntu13")
and
[http://launchpadlibrarian.net/102374362/initramfs-tools-bin_0.99ubuntu13_amd64.deb](http://launchpadlibrarian.net/102374362/initramfs-tools-bin_0.99ubuntu13_amd64.deb)

right click tools package and install with package maintainer. 

According to your capture you should find that bins is already installed so you don't need to install but get it just encase.

i guess there is some screw up in the repos because it should get this version down. This is the release version.

---

### Post by ibjsb4 on 2013-01-30
Before you try that, try this ..

```
sudo apt-get dist-upgrade
```

---

### Post by Rotto on 2013-01-30
Cheers,

I tried *apt-get dist-upgrade* and got the same error as *apt-get upgrade*.

Neither of the packages let me install them using QApt - I've attached screenshots so you can see what I do. Same happens when QApt is run as root from the terminal. (They say 'Newer version in software channel' and initramfs-tools-bin shows 'Error: Breaks the existing package "initramfs-tools"'.)

Any ideas what I could try next?

---

### Post by Cheesehead on 2013-01-30
Please post the contents of your /etc/apt/sources.list file.

The most common reason for this kind of package management failure is a PPA (which you said you don't have), third-party repo, or incorrect Ubuntu repo.

If it's an incorrect repo, then it's also (usually) trivial to fix.

---

### Post by Rotto on 2013-01-30
Ok. See my sources.list below:
```

## Main
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
#deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
#deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
#deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
#deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
#deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu precise main
#deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by furything on 2013-01-30
The fact that the install states there are newer versions does mean it is picking up the back ports.

The version I gave was the current release but there are a couple under test (pre-release).

---

### Post by marsangr on 2013-02-01
Check if you have enough free space in /boot. In my case I got rid of exactly the same error message by purging old kernel images Synaptic Package Manager.

---

### Post by dirtclustit on 2013-02-20
I just had similar problems, I got impatient thinking my computer had locked up and cancelled in the middle of using the GUI update manager (my OS = 12.04lts) 

trying to update again I got similar errors, the last thing your posted error message says is "try -f"

My error said "furthermore try  apt-get install -f"

Using the command line interface in the terminal (cli)
the command "sudo apt-get install -f"  fixed the issue for me

I haven't had any problem since, all updates completely free of errors

---

### Post by dirtclustit on 2013-02-25
it seems I jumped the Gun and didn't read this thread closely enough, I somehow read right thru without realizing what I suggested was one of the first things you listed as action took.

Sorry bout that, I know how it upsets people who have been around awhile when people do exactly what I just did, failed to read the thread.

---

