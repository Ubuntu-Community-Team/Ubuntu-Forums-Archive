---
title: "Update Adobe Flash Player as a Firefox plugin to latest version"
date: 2014-01-30
forum: General Help
---

### Post by roadrawts on 2014-01-30
Facebook site game requires installation of updated Adobe Flash Player to version 11.2.202.335.   When I choose APT 10.04+ as the method to install a pop-up appears asking me to Choose an application.  I don't know what they are referring to.  As an alternative I downloaded the tar file and installed the libflashplayer.so file in /usr/lib/mozilla/plugins but it doesn't seem to be what the game is looking for.

When I use the software center to update Adobe Flash it says that the version installed is up to date.

Does anyone have any idea what is happening and how to get this accomplished?

Thanks

---

### Post by Yellow Pasque on 2014-01-30
You need to purge the old version first (using package manager), or it will conflict with the newer .so file you install.

BTW, you should put the .so in ~/.mozilla/plugins (you probably need to create plugins dir). Dumping files not belonging to a package into /usr is against Debian policy and is a good way to cause issues.

---

### Post by jeanjd63 on 2014-01-30
Hello.
What is the version installed in firefox ?
(Clic right on windows video youtube)

And if you do  :
[B]sudo  apt-get  purge flashplugin-installer
sudo  apt-get  install flashplugin-installer[/B]

---

### Post by Impavidus on 2014-01-30
The software centre should (via the package flashplugin-installer) provide you the flash player version 11.2.202.335, unless you're running an unsupported release of Ubuntu.

---

### Post by roadrawts on 2014-01-31
purged and reinstalled as per post #3 and moved .so into ~/.mozilla/plugins as per post #2.  Application still thinks version needs to be updated.  How can I run the flashplugin-installer?  Maybe that will help.  Thanks for the replies.

---

### Post by deadflowr on 2014-01-31
What version does 
```
apt-cache policy adobe-flashplugin
```
or
```
apt-cache policy flashplugin-installer
```
tell you is installed.

---

### Post by Impavidus on 2014-01-31
Now you are trying to install the flash plugin in two different ways at the same time. The one in ~/.mozilla/plugins will override the one installed via sudo apt-get install flashplugin-installer. With flashplugin-installer is the easier way to install. You don't have to run it, as that happens automatically as part of the installation script.

But first, which version of Ubuntu are you using? And in firefox, click extra&#8594;add-ons&#8594;plug-ins and check whether flash is listed and, if so, which version.

---

### Post by roadrawts on 2014-01-31
Adobe-flashplugin:
	Installed: (none)
	Candidate: (none)
	Version Table:


flashplugin-installer:
	Installed:  11.2.202.335ubuntu0.12.04.1
	Candidate:  11.2.202.335ubuntu0.12.04.1
	Version table:
	*** 11.2.202.335ubuntu0.12.04.1 0
	       500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse i386 Packages
	       500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages
	       100 /var/lib/dpkg/status
	11.2.202.233ubuntu2 0
	       500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages

---

### Post by Impavidus on 2014-02-01
You have flash 11.2.202.335, which is the latest version, installed via the package flashplugin-installer, which is the recommended way. The .so file should be present now somewhere in /usr/lib. If firefox still doesn't have to latest flash version either the installation if the package went wrong (in that case, reinstall it) or you have an older flash installed in an alternative way taking precedence. In the last case, remove the older version.

---

### Post by jeanjd63 on 2014-02-01
What say a "right clic" in a windows flashplayer (video youtube) in firefox.

---

### Post by roadrawts on 2014-02-01
It says: 11.2.202.335 which is the latest.

---

### Post by roadrawts on 2014-02-01
It says:
Shockwave Flash 11.2.202.335
Shockwave Flash 11.2 r202
File:  libflashplayer.so, libflashplayer.so, libflashplayer.so
--------------------------------------------------------
MIME Types
application/x-shockwave-flash(Shockwave Flash:swf),
application/futuresplash(FutureSplash Player:spl),
application/x-shockwave-flash(Shockwave Flash:swf),
application/futuresplash(FutureSplash Player:spl),
application/x-shockwave-flash(Shockwave Flash:swf),
application/futuresplash(FutureSplash Player:spl)

Don't know why everything is repeated 3 times??????

---

### Post by roadrawts on 2014-02-01
Noticed in /usr/lib/mozilla/plugins have the following files:
flashplugin-alternative.so
libflashplayer.so
libjavaplugin.so

Could the alternative be the problem?

---

### Post by Dennis N on 2014-02-01
Its possible the Facebook game you mentioned in post #1 and Firefox are using different versions of the plugin in different locations of the filesystem. Firefox reports its version to the Mozilla test page, and Software Center reports what was installed by flashplugin-installer. Both report the latest version so everything looks fine. Yet the other, older version is also there on your system.

---

### Post by monkeybrain20122 on 2014-02-01
flash in FF will not get updated since adobe has dropped flash for Linux except for security update til 2017. To get up to date flash in Linux you have to install chrome (it comes bundled with its own flash) Most websites work with flash 11.2 but with a few you may need newer version and only Chrome provides that.

Another way is to install Windows' flash using pipelight. [http://fds-team.de/cms/pipelight-installation.html#section_2_3](http://fds-team.de/cms/pipelight-installation.html#section_2_3)  It is up to date and with the bonus of being able to access drmed material, the catch is that it may not work as smoothly as native linux flash and loads more slowly  and may crash during loading (since it relies on wine) So, if you want to try it install galternatives from the repo and use it to switch between which version you use (open galternatives, go to mozilla-flash or something like that, add the path to pipelight flash and choose which one to use and reload Firefox every time you make a change)

---

### Post by Dennis N on 2014-02-01
> **roadrawts said:**
> Noticed in /usr/lib/mozilla/plugins have the following files:
flashplugin-alternative.so
libflashplayer.so
libjavaplugin.so

Could the alternative be the problem?

flashplugin-alternative.so is a symlink:

```
lrwxrwxrwx 1 root root     37 Jan 15 13:56 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

```
the target, mozilla-flashplugin, is another symlink: 
```

lrwxrwxrwx 1 root root  48 Jan 15 13:56 mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so

```

the target **/usr/lib/flashplugin-installer/libflashplayer.so** is the flash plugin used by Firefox. You can check this by putting about:plugins in the Firefox address window to get the plugins page. Notice the location of the plugin used by Firefox is given:

```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11,2,202,335
    State: Enabled
    Shockwave Flash 11.2 r202


```

_I would test the hypothesis in post #14 by searching for other instances of libflashplayer.so. If any are found, you could manually replace them with the known copy of the latest version and all should be well._

[My reference system: Lubuntu 13.10 which in respect to the plugins, should be the same as Ubuntu 13.10]

---

### Post by roadrawts on 2014-02-01
thank you all for your suggestions.  I will search for other libflashplayer.so files and check the dates/versions and try and eliminate the errant one.  If that fails, I have chrome installed.  I'll try that also.

Don't want to take any more of your valuable time on this.  It's just a game, anyway.

Thanks again.

---

