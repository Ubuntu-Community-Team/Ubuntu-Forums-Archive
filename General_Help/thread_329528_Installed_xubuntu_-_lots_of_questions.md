---
title: "Installed xubuntu - lots of questions"
date: 2007-01-01
forum: General Help
---

### Post by shadowwyvern on 2007-01-01
As the thread says, I installed xubuntu on my laptop (fedora is too slow on it), and have lots of questions.

1.) How do I enable ntp support?  this is really basic, but apparently it is not...
2.) apt-get seems to not work at all.  even basic stuff like vlc, gobby, firestarter, even sshd (I basically just tried stuff I thought would work) comes up empty.  Is there a package that is know to work so I can test this? I have uncommented all but the last two "evil" repositories in /etc/apt/sources.list
3.) What kind of iptables configuration is enabled by default?
4.) How do I stop gdm from playing that silly sound?
5.) in xfce, how do I set behavior on acpi events, like lid close?
6.) where do I get a full graphical service editor? The default one shows only a few services and has no options for editing specific run levels....


Thanks in advance

---

### Post by bruenig on 2007-01-01
2. Paste your /etc/apt/sources.list in here so we can see what you are missing. Just uncommenting the repos doesn't enable them all, multiverse for instance requires that you actually add it.

4. Go to the Applications>System>Login Window, then the Accessibility Tab and uncheck the sound stuff.

---

### Post by shadowwyvern on 2007-01-01
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

There it is :)

Fixed #4, thanks.

---

### Post by Azakus on 2007-01-01
Uncomment everything that has a "universe" tag to it. Those are the repos with the programs that you are looking for in there.

---

### Post by compwiz18 on 2007-01-01
#3: Default iptables config: everything is open, but nothing is listening - I know that doesn't make much sense.  Let me try that again - iptables blocks nothing.  But there are no programs listening, so every port appears closed.  There will be no open ports on a default Ubuntu install.

See [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) for a good reference guide - it might help if you have more questions.

---

### Post by koenn on 2007-01-01
> 3.) What kind of iptables configuration is enabled by default?

run
```
iptables --list
```
and see

---

### Post by kerry_s on 2007-01-01
> **koenn said:**
> run
```
iptables --list
```
and see

It's " sudo iptables --list "

---

### Post by bruenig on 2007-01-01
Change
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
```
into
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
```

---

