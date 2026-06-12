---
title: "Accidentally removed Python, now everything is broken"
date: 2020-09-13
forum: General Help
---

### Post by ahashemi on 2020-09-13
[COLOR=#242729][FONT=Arial][COLOR=var(--black-200)  !important][FONT=inherit][COLOR=var(--black-500)  !important][FONT=inherit]0[/FONT][/COLOR]


[URL="https://askubuntu.com/posts/1274660/timeline"]
[/URL][/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]I mistakenly tried to sudo apt remove python3 (I was trying to install multiple versions of Python), but stopped it using Ctrl+C immediately. Looks like I damaged the package and I was unable to open a terminal or anything. After struggling for hours now I can open terminal and apps like Google Chrome and Telegram, but can't open VS Code.[/FONT]
[FONT=inherit]When I try to sudo apt install python3, after lots of failed dpkg queries, it says:[/FONT]
Processing was halted because there were too many errors.
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]I looked it up and on [“sub process usr bin dpkg returned an error code 1&#8243; Error in Ubuntu]("https://itsfoss.com/dpkg-returned-an-error-code-1/") it was suggested to try these commands:[/FONT][/COLOR]
sudo dpkg --configure -a[COLOR=#242729][FONT=Arial]It fails and after failed dpkg queries, returns:[/FONT][/COLOR]
Processing was halted because there were too many errors.[COLOR=#242729][FONT=Arial]sudo apt-get install -f also failed with the following error message:[/FONT][/COLOR]
Processing was halted because there were too many errors.
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also Running "sudo dpkg-reconfigure libdvd-pkg" 
returns
"dpkg-query: package 'libdvd-pkg' is not installed and no information is available Use dpkg --info (= dpkg-deb --info) to examine archive files. /usr/sbin/dpkg-reconfigure: libdvd-pkg is not installed"

and trying to install libdvd-pkg manually from .deb file returns 
"dpkg: dependency problems prevent configuration of libdvd-pkg: libdvd-pkg depends on debhelper (>= 9); however: Package debhelper is not configured yet. libdvd-pkg depends on dh-autoreconf; however: Package dh-autoreconf is not configured yet."

and trying to install debhelper from .deb file returns the same error for dh-autoconf and trying to install dh-autoconf returns error for debhelper.

What is the way out to fix this mess without reinstalling Ubuntu?

---

### Post by Impavidus on 2020-09-13
Many important parts of Ubuntu depend on Python, so if you break Python, your system is in such a poor state that you can't use the tools you need to fix it.

Theoretically you can fix it. You can boot a live disk and use the functional package manager on the live disk to reinstall all affected packages of your installed system. But the best way to solve this is by reinstalling Ubuntu.

---

### Post by HermanAB on 2020-09-13
The easy solution is to backup your data and re-install.

Another way to fix it, is to make a virtual machine with the exact same version of Ubuntu, then use rsync to copy all the system directories over.

---

### Post by dragonfly41 on 2020-09-13
I looked into my Synaptic Package Manager, searched "python3" and there are of course countless packages.
But if you look at File > History you see a log of packages installed or removed by date.  This might help .. I don't know.
It gives some reference point to compare.

---

### Post by HermanAB on 2020-09-13
"File > History you see a log of packages installed or removed by date." - The trouble is that the wizards needed to manage the system are broken and installing a long list of things manually is something that anyone will rather avoid doing.

---

### Post by TheFu on 2020-09-13
The truth.

You did something foolish.  Deleting parts of the OS is bad.  You've learned that now.  Unix-like systems think you are a genius, even when you are being stupid. It does what you tell it because the OS can't tell the difference between stupidity and genius.  We've all done something similar over the decades.  

I once deleted an complete OS in a new Solaris server that was less than 1 week old. ;)  Fortunately, I'd made an image of everything to tape the day prior. Unfortunately, I hadn't looked up the command to restore that tape. This was before the internet had all knowledge available for asking.  Had to buy this thing made from dead trees ... it is long ago ... think it was called a book.  ;)

So, you've been chastised enough.  I wish I could say this would be the last time you do something foolish on a computer.  It isn't.  We all do foolish things. Some of us every day.  Yesterday, I tweaked some RAM performance numbers slightly and the system seems stable ... until it isn't ... many hours later.  Nothing in the logs, just 
```
------ Rebooting ------
```
The system has been running fast and stable for almost 2 yrs, but I'm an idiot for messing with it.

Ok, for python programming/learning, never touch OS versions that are installed.  Those exact, specific versions are necessary for the OS.  The same applies to perl and ruby. The OS is dependent on those specific releases.  As a programmer, you'll need/want exact control over the versions of whatever language you are using too.  With python, there are a few different ways to have multiple versions installed, concurrently, and for us to choose which gets used at any time for our programming and each program we create.  One solution is called **pyenv**. There are others.  These all work in the same way.  They modify specific environment variables so that a specific python and python libraries are used rather than the system or any other version of python.  You can change between different environments (different pythons) with a pyenv command. For example:
```
$ pyenv versions
* system (set by /home/tf/.pyenv/version)
  2.7.17
  3.6.10
  3.8.1

```
I have 3 versions of python controlled by pyenv. These are separate from the OS installed versions.
```
$ which python
/home/tf/.pyenv/shims/python
```
controls which version of python I'm actually using.
```
$ python --version
Python 2.7.12
```
See how that version isn't in the list, but that "system" is?  The system python is what I use unless I'm doing python work. For python3, 
```
$ python3 --version
Python 3.5.2
```
Again, it is the system version, not one that I've installed.  v3.8.1 was the latest python when I last did some python3 work.  3.6.xx is what the python book I used to learn the language had, so I wanted as few surprises as possible.  Books, especially programming books, already have enough bugs/typos around the code. Things that work in 3.6 may not work or may return slightly different results than v3.8 does.

As a programmer, we often need tools on our systems that aren't "packaged", but we still need to keep those tools separate from the core OS tools.  Environment management is how we accomplish that.  I always keep my development stuff completely separate from the OS stuff.  Bad things can happen in a corporate environment when we don't do that.  The OS guys have a job. They need for the OS to be patched and for the audit scanners to report that those patches "pass".  At some point, they will patch the OS at 4am on a Sunday and break all your code.  Or they can patch at 4am and all your code keeps running.  Your choice.  The other thing is that when we bring our tools for the environment, now we are both in control of them and required to maintain them.  Best to be proactive, stay ahead of the OS teams, get any security patches into our systems, and redeploy "the new" at least every 2 weeks for an active project under development.  Deploy early and often.  Also patch as early as possible, hopefully, in an automatic way, as part of the CI/CD workflows.

Anyways, pyenv is pretty easy and very useful, especially if you'd rather not have to reinstall the OS all the time.  There are other python tools that can accomplish similar stuff. If you have a mentor, ask them how they do it.

---

### Post by mIk3_08 on 2020-09-13
The sad side thing of  not being careful.

---

### Post by oldfred on 2020-09-13
You may be able to chroot into your system from the live installer & repair it.
If not, new install & restore from your backups is best alternative.

chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

