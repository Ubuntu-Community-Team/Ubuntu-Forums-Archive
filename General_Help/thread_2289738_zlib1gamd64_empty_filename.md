---
title: "zlib1g:amd64 empty filename"
date: 2015-08-06
forum: General Help
---

### Post by christopher-b-nash on 2015-08-06
Along with the title I can't upgrade to 3.13.0-48 generic b/c it depends on linux-image-3.13.0-48-generic

also tried running apt-get -f install and that didn't work.

---

### Post by ajgreeny on 2015-08-06
Welcome to the forum christopher-b-nash.

I don't think I know exactly what you are trying to do, nor why you are trying to update to linux-image-3.13.0-48-generic, as linux-image-3.13.0-61-generic is the latest version of the 3.13.0- series.

Please run commands ```
sudo apt-get update
sudo apt-get upgrade
``` and report back here with the output, using code-tags please.  See my signature for a "how-to" for code-tags.

---

### Post by christopher-b-nash on 2015-08-06
When I run apt-get dist-upgrade I get the error
```

Building Dependency tree
Reading state info done
You may want to run apt-get -f to correct these

Following packages have unmet dependencies
linux-image-extra-3.13.0-48-generic : depends : Linux-image-3.13.0-48-generic but its not installed 
linux-image-generic : depends:linux-image-3.13.0-48-generic but it is not installed
E: Unmet dependencies. Try using -f

```

sudo apt-get update finishes fine Reading package list done
sudo apt-get upgrade gives me the error stated above.

Im trying to get to the latest kernel. We run Fogproject off this server and its not working so I'm not sure what broke, but in trying to fix the problem I run in to these upgrade/upgrade issues.

Ive also on the current kernel ran into a panic issue and dropped back a few in advanced options to get back in the server. I haveing a few issues and not sure whats going on with it but before I was able to SSH into the server with my account "chris" and it was fine now it will not let me so I figured i would just run through and make sure everything is up to date and reboot.

---

### Post by christopher-b-nash on 2015-08-06
Also when I try sudo apt-get autoremove I get the same error as in my second post in the cod box.

---

### Post by matt_symes on 2015-08-06
Hi

I'm interested in why apt-get -f install failed so please post the entire output of the command

```
sudo apt-get -f install
```

EDIT: is zlib1g completely broken on your system ? It implements gzip and I seem to remember that is one of the compression formats that can be used in deb archives although I would have to double check that.

It may be an explanation as to why your package system is broken but we will only know that after more investigate.

Kind regards

---

### Post by christopher-b-nash on 2015-08-07
[https://drive.google.com/file/d/0B9NsgzC-iBj9a1lUaXQwbzloMlE/view?usp=sharing](https://drive.google.com/file/d/0B9NsgzC-iBj9a1lUaXQwbzloMlE/view?usp=sharing)

[https://drive.google.com/file/d/0B9NsgzC-iBj9RzNSSHRvU1FFSzg/view?usp=sharing](https://drive.google.com/file/d/0B9NsgzC-iBj9RzNSSHRvU1FFSzg/view?usp=sharing)

---

### Post by christopher-b-nash on 2015-08-07
I'm working in on a VM so I had to take screen shots.

---

### Post by christopher-b-nash on 2015-08-07
nothing?

---

### Post by steeldriver on 2015-08-07
Can you post the output of

```

cat /var/lib/dpkg/info/zlib1g:amd64.list

```

please?

---

### Post by christopher-b-nash on 2015-08-07
```

://bugs.launchpad.net/ubuntu/+filebug
Origine: Ubuntu

Package: dovecot-ldap
Priority: optional
Section: universe/mail
Install-Size: 599
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainroot@Fog:/boot#

```

---

### Post by matt_symes on 2015-08-07
Hi

I think I may have been along the right lines. 

It looks like zlib1g has become corrupted and needs to be reinstalled.

It looks to be trying to unpack the dpkg archive and failing there.

That is a problem as zlib1g may be needed to unpack the deb file to reinstall zlib1g.

Please be patient with responses on these forums as many members who post to try to help others have a full time role called life away from the keyboard :)

At the moment I am responding on my phone and not really in a position to respond but we can take this up tomorrow when I can and others, such as steeldriver who has also posted in the thread, may be able to respond.

EDIT: run fsck on the partition first.

```
sudo touch /forcefsck

sudo reboot
```

Wait for fsck to run during the reboot. When back at a terminal prompt

```
sudo rm /forcefsck
```

EDIT2: your list file needs to be fixed. I can help you with that tomorrow.

What release of Ubuntu are you using ?

In the meantime I'm going to find out how you turn off the spell checker on this useless phone. 

When I type shell I mean shell and not she'll.

EDIT3:

Here is the contents of my zlib1g:amd64.list file.

```

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/zlib1g
/usr/share/doc/zlib1g/changelog.Debian.gz
/usr/share/doc/zlib1g/copyright
/lib
/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu/libz.so.1.2.8
/lib/x86_64-linux-gnu/libz.so.1 
```

The file above is from a 64bit version of a trusty installation.

As you can see it's different than yours. 

You need to edit your copy of the file and remove what you have in there.

You need to copy and paste what i have in my file into yours but you may have to change it slightly if you're not using 64bit (the path x86_64-linux-gnu) and if your libz library is not at version libz.so.1.2.8.

libz.so.1 should be a standard symlink to whatever version of libz.so.X.X.X you are using.

If you need more instruction, post back.

Kind regards

---

### Post by christopher-b-nash on 2015-08-10
Thanks sorry for the rush. So after the sudo touch /forcefsk runs and I log back in I get this error

```

rm: cannot remove '/forcefsck' : No such file or directory

```

So when I vi the zlib1g:amd64.list file I find this. I have removed all lines and replaced with yours.
```

://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: dovecot-ldap
Priority: optional
Section: universe/mail
Installed-Size: 599
Maintainer: Unbuntu Developers <ubuntu-devel discuss@lists.ubuntu.com>
Original-Maintain

```

My Release 
```

Distributor ID: Ubuntu
Description: Ubuntu 14.04.1 LTS
Release: 14.04
Codename: Trusty

```

Uname -mrs reports

```

Linux 3.13.0-46-generic x86_64

```

apt-get upgrade still not functional

When I run apt-get -f install I now get an error

```


Dpkg: unrecoverable fatal error, aborting:
Files list file for package 'ppp' is missing final newline
E: Sub-process /usr/bin/dpkg returne an error code (2)

```

---

### Post by christopher-b-nash on 2015-08-10
I think it may be better if I do a reInstall of the OS.

---

