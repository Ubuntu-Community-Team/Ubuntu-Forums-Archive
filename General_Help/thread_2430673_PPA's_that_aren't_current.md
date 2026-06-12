---
title: "PPA's that aren't current"
date: 2019-11-05
forum: General Help
---

### Post by Shibblet on 2019-11-05
There are two PPA's out there that I use for Kubuntu.  They are not available yet for Eoan Ermine 19.10.

Grub Customizer
[https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer")

Ubuntu Cleaner
[https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa]("https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa")

**Do I have to wait until the author updates these programs, or is there a way to run the older version until the new one comes out?**

P.S. Yes, I have noticed that Ubuntu Cleaner has an Eoan version, but it does not work.  It was uploaded July 17th.

---

### Post by CatKiller on 2019-11-05
It depends on the specifics of the package.

There was something - I can't remember what any more - that I grabbed and installed from packages.ubuntu because it had been dropped from the repositories for newer releases. Whatever it was was old and crusty, and, importantly, didn't change anything else on the system.

The sensible thing to do is to simply wait, or find a newer PPA, or use a snap or similar. Only you know your own balance between patience and tolerance for complete breakage.

---

### Post by oldfred on 2019-11-05
I do my own grub custom settings.
Depends on what you want to do and/or how complicated it is. 
Grub has now changed from 2.02 to 2.04 and grub customizer creates its own scripts, so would need major updates.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

I also run my own script to houseclean. Simple bash file with multiple commands. Originally just a few lines. But over time added more & more.
[https://askubuntu.com/questions/657091/whats-the-good-way-to-clean-up-the-system-and-is-bleachbit-safe-on-ubuntu-14](https://askubuntu.com/questions/657091/whats-the-good-way-to-clean-up-the-system-and-is-bleachbit-safe-on-ubuntu-14)

---

### Post by deadflowr on 2019-11-05
[s]The Ubuntu Cleaner ppa has an eoan archive.[/s]
(I missed the PS. new comment below)

And personally, I found it quicker, and quite frankly easier, to DIY grub myself.
This helped: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")


Edit: Snoozed, so I lost.
ninja'd by oldfred, who posted good links beyond just the wiki.


To add: I just noticed the Ubuntu Cleaner package in the ppa hasn't been updated for almost 3 years.
If it doesn't work probably to be expected. With it being such an outdated pieces of software by now.
( and with all the changes that have taken place in the last 3 years,
I would think it was running on fumes and inertia...)

---

### Post by sudodus on 2019-11-06
There is no independent or organized or systematic testing of the PPAs, so in general, you take a risk, when you use them. With that said,

- several PPAs are well maintained and have a good reputation,

- some PPAs lag behind and are not available until some time after a new Ubuntu version is released. The developer/maintainer may be busy with other tasks ...

- some PPAs depend on features that may change between Ubuntu versions, and you should wait for a PPA version for the new Ubuntu version until you start using it,

- some PPAs are designed to be as independent as possible of features that change between Ubuntu versions. One example is ppa:mkusb/ppa, that is developed and maintained by me. It uses bash shellscripts, that call standard programs, that will not change much between Ubuntu versions. The mkusb versions for all current versions of Ubuntu are exactly the same, I copy them from a master version after testing that they work in the various versions of Ubuntu. So in this case you could use a PPA from an older version, if it is not yet available in the newest version, but I try to provide versions early for the developing versions, so you should not need that.

It is a good idea to have a test system, a [persistent] live system or an installed system in a USB drive or installed alongside your main operating system. You can test various things in such a system, for example PPAs, before you start using them in your main operating system.

---

### Post by Frogs Hair on 2019-11-07
Grub Customizer is available from the repository.

---

### Post by Shibblet on 2019-11-13
So, what is a good alternative for Ubuntu-Cleaner?

---

### Post by #&amp;thj^% on 2019-11-13
Original Topic kind of changed here.... but here's some worth consideration: [https://www.tecmint.com/ccleaner-alternatives-for-ubuntu/](https://www.tecmint.com/ccleaner-alternatives-for-ubuntu/)

---

### Post by Shibblet on 2019-11-13
> **1fallen said:**
> but here's some worth consideration: [https://www.tecmint.com/ccleaner-alternatives-for-ubuntu/](https://www.tecmint.com/ccleaner-alternatives-for-ubuntu/)

I've looked into some of those already, but they don't seem to do the same thing that Ubuntu-Cleaner does.

> **1fallen said:**
> Original Topic kind of changed here...

Let me steer us back on course then.  Is there anyway to make the current PPA work?  It's missing some dependencies, and I don't know how to add them.

---

### Post by sudodus on 2019-11-14
The following link describes how to make an Ubuntu PPA work with Debian,

[Add the PPA manually to the file '/etc/apt/sources.list'](https://help.ubuntu.com/community/mkusb/install-to-debian#Add_the_PPA_manually_to_the_file_.27.2Fetc.2Fapt.2Fsources.list.27)

Maybe it will give you enough information in order to try using an old PPA in your current version of Ubuntu. *This may or may not work.* It may even create problems with other parts of your Ubuntu system.

[Warning](https://help.ubuntu.com/community/mkusb/install-to-debian#Warning)

---

### Post by #&amp;thj^% on 2019-11-14
Thought I'd give this go on "focal" Chaning to "eoan" on the source list but.....
```
apt depends ubuntu-cleaner
ubuntu-cleaner
  Depends: python-defer
  Depends: python-lxml
  Depends: <python:any> (<< 2.8)
    python:i386
    python
  Depends: <python:any> (>= 2.7.5-5~)
    python:i386
    python
  Depends: python-dbus
  Depends: <python-aptdaemon>
  Depends: <python-aptdaemon.gtk3widgets>

```
Strange thing with:
```
apt policy python-defer
python-defer:
  Installed: 1.0.6-2build1
  Candidate: 1.0.6-2build1
  Version table:
 *** 1.0.6-2build1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
        100 /var/lib/dpkg/status

```
And this is the only Dep I can not find for myself:
```
python-aptdaemon.gtk3widgets:
  Installed: (none)
  Candidate: (none)
  Version table:
```
  I would think the maintainer should be made aware of this for Eoan at the very least. ;)
So Long story short ****not advisible****

---

### Post by Shibblet on 2019-11-14
> **sudodus said:**
> The following link describes how to make an Ubuntu PPA work with Debian,

[Add the PPA manually to the file '/etc/apt/sources.list'](https://help.ubuntu.com/community/mkusb/install-to-debian#Add_the_PPA_manually_to_the_file_.27.2Fetc.2Fapt.2Fsources.list.27)

Maybe it will give you enough information in order to try using an old PPA in your current version of Ubuntu. *This may or may not work.* It may even create problems with other parts of your Ubuntu system.

[Warning](https://help.ubuntu.com/community/mkusb/install-to-debian#Warning)

Oh, the PPA adds in just fine.  But the current PPA requires a couple of dependencies that cannot be made.  What can be done about this, besides just wait until the package manager fixes them?

---

### Post by #&amp;thj^% on 2019-11-14
> **Shibblet said:**
> Oh, the PPA adds in just fine.  But the current PPA requires a couple of dependencies that cannot be made.  What can be done about this, besides just wait until the package manager fixes them?

It would help if they were aware of:
```
python-aptdaemon.gtk3widgets:
  Installed: (none)
  Candidate: (none)
  Version table:
```
That was the only Depends I could not solve.
For my cleaning needs, the terminal is my most trusted friend.

---

### Post by Shibblet on 2019-11-14
> **1fallen said:**
> It would help if they were aware of:
```
python-aptdaemon.gtk3widgets:
  Installed: (none)
  Candidate: (none)
  Version table:
```
That was the only Depends I could not solve.

Is that because I am using Kubuntu (KDE), and not Ubuntu (Gnome 3)?

---

### Post by #&amp;thj^% on 2019-11-14
> **Shibblet said:**
> Is that because I am using Kubuntu (KDE), and not Ubuntu (Gnome 3)?

Nope, no matter what DE your using, it's just _not_ available on Eoan and Focal (19.10 & 20.04 alpha). :o
That's why I suggested letting them know.

---

