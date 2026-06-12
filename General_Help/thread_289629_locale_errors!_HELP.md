---
title: "locale errors! HELP"
date: 2006-10-31
forum: General Help
---

### Post by joefie on 2006-10-31
```
#  apt-get install linux-686 linux-headers-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmikmod2 libxt-dev libxul0d libxul-common libruby1.8
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-686 linux-headers-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.4kB of archives.
After unpacking 106kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/restricted linux-686 2.6.17.10 [23.7kB]
Get:2 http://archive.ubuntu.com edgy/main linux-headers-686 2.6.17.10 [23.7kB]
Fetched 47.4kB in 0s (68.6kB/s)         
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "nl_NL@euro"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package linux-686.
(Reading database ... 141385 files and directories currently installed.)
Unpacking linux-686 (from .../linux-686_2.6.17.10_i386.deb) ...
Selecting previously deselected package linux-headers-686.
Unpacking linux-headers-686 (from .../linux-headers-686_2.6.17.10_i386.deb) ...
Setting up linux-686 (2.6.17.10) ...
Setting up linux-headers-686 (2.6.17.10) ...
root@gvhmifxv:~# locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

```

help?

---

### Post by BLTicklemonster on 2006-12-12
Hmm, hope he got it fixed. I am having the same problem after installing edgy on a computer (using live cd) that was not hooked up to the internet. It installed an old kernel, so when I went to upgrade once I connected it to the internet, it somehow started having all kinds of problems. Fortunately, I installed icewm and fluxbox before upgrading, because I have no gnome desktop at all now, and have to use flux to do anything. So I'm looking to resolve this, and have found these so far:

> **jthompson said:**
> Hmmm, I changed the file /etc/default/locale to:

```
LANG="en_US.UTF-8"
```

I rebooted, and wala.  I don't get the error message anymore.  Perhaps the ISO locales aren't supported anymore?  I guess I must have selected an unsupported locale on install.  Anyone who can enlighten me, please do so.


> **ebash said:**
> Modify your environment and set the variable LC_ALL and LANGUAGE. Normally these variables should already be set, but it seems that your profile is missing them.

In a shell do:
```
export LC_ALL=en_US.UTF-8 LANGUAGE=en_US.UTF-8
```

You may want to add this variables to your ~/.bashrc.

---

