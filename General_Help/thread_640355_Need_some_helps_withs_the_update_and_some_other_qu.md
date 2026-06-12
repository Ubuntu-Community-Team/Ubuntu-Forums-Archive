---
title: "Need some helps withs the update and some other question"
date: 2007-12-14
forum: General Help
---

### Post by erickong on 2007-12-14
Hi there,
I was confusing wit the update.At first, i tried to update with the update manager but it doesnt work. At the end of the point, i get this sort of problem wit the update

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2)
[http://my.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://distro.holonyx.com/restore/dists/gutsy/Release.gpg:](http://distro.holonyx.com/restore/dists/gutsy/Release.gpg:) Could not connect to distro.holonyx.com:80 (1.0.0.0), connection timed out
[http://distro.holonyx.com/restore/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://distro.holonyx.com/restore/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to distro.holonyx.com:80 (1.0.0.0), connection timed out


Can some one guide me for the problem?I am using i386 Ubuntu 7.10 version. I just install the window and i couldn't do anything..:confused:. This is really pissing me off, wad should i need to do to update the window?

One more question,can i know what is library and gnupg? How do it function?

---

### Post by erfahren on 2007-12-14
I should first mention that you don't want to run more than one package manager application at a time (don't use Synaptic Package Manager and Add/Remove Programs, or the Update Manager and try to update through the terminal, and so on. - you may not know what all those are but just keep that in mind).

Anyway, go to System > Administration > Software Sources and enable (check) all the repositories except "Source Code". If you checked anything it'll prompt you to reload. (If they were already checked let us know.)

Close it and try updating again. 

To clean up your /etc/apt/sources.list file and enable other repositories for some of the non-free programs see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
make sure you do the part where it says to add the key for Mediubuntu
(note: sometimes that wiki doesn't go directly to the section. The "Enabling extra repositories" part is just a little bit down in the contents.)

---

### Post by erfahren on 2007-12-14
> **erickong said:**
> 
One more question,can i know what is library and gnupg? How do it function?
I don't know what you mean by that last part, can you explain?

---

### Post by erickong on 2007-12-14
I though library is something for the window?And gnupg is some sort of, how to say...Erm, GNU privacy guard?

Thx for the answer...I'll try that later on,

I've found many "package" from some site, those package comes out wit many strange name and i dont know which are the one i should use like for wine,codec for video and etc...

One more, i tried to type in the command for the wine in terminal, why it doesnt start download? The web is " [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) "... Correct rite?I'd follow the instruction which is copy and paste " sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list " up...But it aint start download. Can i have a solution for it?Or maybe i haven't update?

---

### Post by erfahren on 2007-12-14
that line you entered "sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list " 

... is to enter that repository in the sources.list file. The sources.list contains the repositories that you are able to download packages from. You can see all the packages that are available to download in Synaptic Package Manager. (System > Adminstration > Synaptic Package Manager)

I thought wine was already in there. You should check Synaptic (search it) before going to the internet to find programs. The software in the repositories is already pre-compiled to and pre-configured to be installed on your version of Ubuntu.

That's why I first suggested that you go and clean up your sources.list and add Mediubuntu repository. It contains the non-free programs and codecs.

see:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

for more info on codecs go to: [https://help.ubuntu.com/](https://help.ubuntu.com/)
and then "Music, Videos, and Photos"

hint: installing the "ubuntu-restricted-extras' meta-package would get you off to a good start. It contains Flash, Java, some codecs and some other things.

For playing online video I've had better luck with vlc (VLC) and the mozilla-plugin-vlc

if you haven't already, you might want to go to System > Administration > Restricted Drivers Manager and see if there is a restricted driver that needs enabled. They aren't always enabled by default.

---

