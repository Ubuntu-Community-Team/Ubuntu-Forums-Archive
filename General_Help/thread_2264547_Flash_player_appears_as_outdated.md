---
title: "Flash player appears as outdated"
date: 2015-02-08
forum: General Help
---

### Post by fkervin on 2015-02-08
Hi all,

I have a message in all webs that uses flash saying that it's outdated and needs to be installed latest version. I've gone to adobe site here:

[https://www.mozilla.org/en-US/plugincheck/?utm_source=firefox-browser&utm_medium=firefox-browser&utm_campaign=plugincheck-update](https://www.mozilla.org/en-US/plugincheck/?utm_source=firefox-browser&utm_medium=firefox-browser&utm_campaign=plugincheck-update)

I've download the four versions that appears but I don't know how to install any of them. I've also try to remove adobe-flashplugin and reinstall in software center but problem is still here.

Any help?

Regards

---

### Post by sammiev on 2015-02-08
> **fkervin said:**
> Hi all,

I have a message in all webs that uses flash saying that it's outdated and needs to be installed latest version. I've gone to adobe site here:

[https://www.mozilla.org/en-US/plugincheck/?utm_source=firefox-browser&utm_medium=firefox-browser&utm_campaign=plugincheck-update](https://www.mozilla.org/en-US/plugincheck/?utm_source=firefox-browser&utm_medium=firefox-browser&utm_campaign=plugincheck-update)

I've download the four versions that appears but I don't know how to install any of them. I've also try to remove adobe-flashplugin and reinstall in software center but problem is still here.

Any help?

Regards

Go to there test site [here]("https://www.adobe.com/software/flash/about/") and try it.

---

### Post by Yellow Pasque on 2015-02-08
You're making it too difficult.  The updated version of Flash should install automatically like a normal Ubuntu security update. What version of Ubuntu are you using?

```
apt-cache policy flashplugin-installer
```

---

### Post by yancek on 2015-02-08
Don't download all 4 versions.  You should use the one which says 'apt for Ubuntu+'.  Right click on it and you should get an option to open in Software Center and install.  You could also download the tar.gz but installing the libflashplayer.so file is a different process.  You can also change the settings in firefox from the Tools tab, Add-ons, Plugins and on the right you have several options; Always Activate, Ask to Activate and Never Activate.

---

### Post by fkervin on 2015-02-08
Many thanks to all for the answers

> **sammiev said:**
> Go to there test site [here]("https://www.adobe.com/software/flash/about/") and try it.

It carries me to the same download site.

> **Temüjin said:**
> You're making it too difficult.  The updated version of Flash should install automatically like a normal Ubuntu security update. What version of Ubuntu are you using?

I use xubuntu 14.04, the result of the command:

```
apt-cache policy flashplugin-installer
```

is:

```
flashplugin-installer:
  Installed: 11.2.202.440ubuntu0.14.04.1
  Candidate:  11.2.202.440ubuntu0.14.04.1
  Table version:
 *** 11.2.202.440ubuntu0.14.04.1 0
        500 http://es.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.350ubuntu1 0
        500 http://es.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages


```


> **yancek said:**
> Don't download all 4 versions.  You should use the one which says 'apt for Ubuntu+'.  Right click on it and you should get an option to open in Software Center and install.  You could also download the tar.gz but installing the libflashplayer.so file is a different process.  You can also change the settings in firefox from the Tools tab, Add-ons, Plugins and on the right you have several options; Always Activate, Ask to Activate and Never Activate.

When I do this, Software Center opens showing a message saying: 

```

Not found
It doesn't exist any software package called "adobe-flashplugin" the the software sources

```

Regards

---

### Post by SeijiSensei on 2015-02-08
I believe you have to have the "Canonical Partners" repository enabled to install "adobe-flashplugin" directly.  You can do that from a GUI package manager, or just remove the hash mark from the line
```
deb http://archive.canonical.com/ubuntu trusty partner
```
in /etc/apt/sources.list, then run "sudo apt-get update && sudo apt-get install adobe-flashplugin".

Otherwise try installing "flashplugin-installer".

---

### Post by fkervin on 2015-02-08
> **SeijiSensei said:**
> I believe you have to have the "Canonical Partners" repository enabled to install "adobe-flashplugin" directly.  You can do that from a GUI package manager, or just remove the hash mark from the line
```
deb http://archive.canonical.com/ubuntu trusty partner
```
in /etc/apt/sources.list, then run "sudo apt-get update && sudo apt-get install adobe-flashplugin".

Otherwise try installing "flashplugin-installer".

I've just do this, as you said this line was disabled on /etc/apt/sources.list

I enabled it, made the sudo apt-get update and then in the install adobe-flashplugin the most relevant seemt to be this:

```
those packages will be REMOVED:
  flashplugin-installer
those NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
``` 

I don't know if those new packages are better than older one, but the message of "flash is outdated" is still here. I've try to update using 'apt for Ubuntu+' and now Software Center shows that it's installed but I have no choice to update, only remove.

So, I still don't know hog to get rid of the "it's outdated message".
Regards

---

### Post by Yellow Pasque on 2015-02-08
```
flashplugin-installer:
  Installed: 11.2.202.440ubuntu0.14.04.1
  Candidate:  11.2.202.440ubuntu0.14.04.1
```

Hmm, it just looks like you need to run "sudo apt-get update" because 11.2.202.**442** is available from your mirror: [http://es.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://es.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

As for the partner repository, it should not be necessary in modern versions of Ubuntu. The flashplugin-installer package and that is what you want (unless you don't have internet connection).

Enabling the partner repo and getting Flash there is

---

### Post by buzzingrobot on 2015-02-08
The current version of Flash for Linux is:11.2.202.442.  That is the version in the Ubuntu repositories and the version that will be installed, assuming the mirror in use is updated and current.

Quit and restart Firefox after installing the new version. Check the plugins list (Tools->AddOns->PlugIns) to verify its in use.

Flash releases by Adobe for Windows follow another, different, version numbering scheme, as do the pepper-flash versions maintained and released by Google.

Flash for Linux has received only security patches from Adobe for sometime, and Adobe plans to stop providing even those in the future.  Meanwhile, new features have gone into the Windows versions.  Pehaps these "out-dated Flash" reports we seem to be seeing lately are the result of sites assuming the presence of the Windows version of Flash.

---

### Post by SeijiSensei on 2015-02-08
The warnings will go away once you've installed 11.2.202.442.

It's possible to install [pipelight]("http://pipelight.net/cms/installation.html") and have it use the [Windows version]("http://pipelight.net/cms/plugin-flash.html") of Flash instead.

---

### Post by fkervin on 2015-02-09
Many thaks to all for the answers,

I really have had no more time for testint it, I have some problems I need to solve firstly. Of course I'll tell here when I'll come again to the flash issue.

About pipelight, I use this to have silverlight support, do you reccomend me using it also for flash instead using linux versión?

Regards and thanks

---

### Post by monkeybrain20122 on 2015-02-09
> **fkervin said:**
> Many thaks to all for the answers,

About pipelight, I use this to have silverlight support, do you reccomend me using it also for flash instead using linux versión?

Regards and thanks

You can check it out and decide it for yourself. To switch to it, close firefox, in terminal run
```
pipelight-plugin --enable flash

```
To switch back, close Firefox
```
pipelight-plugin --disable flash
```

(you don't need to run these commands with sudo like in the official documentation)

On the plus side, it is up to date and plays contents that native flash  doesn't either because it is not up to date (11.2) or because it is not  drm capable (11.2 and pepper flash in chrome) For the cons, pipelight flash loads a bit slower than native flash and some features don't work, like webcam, pure audio may not work like in google translate (can't remember) Aslo if you watch flash videos on non English sites foreign characters on player don't render, hardware acceleration doesn't work (but even for 11.2 it only works for Youtube anyway if it works at all)

---

### Post by fkervin on 2015-02-15
> **SeijiSensei said:**
> I believe you have to have the "Canonical Partners" repository enabled to install "adobe-flashplugin" directly.  You can do that from a GUI package manager, or just remove the hash mark from the line
```
deb http://archive.canonical.com/ubuntu trusty partner
```
in /etc/apt/sources.list, then run "sudo apt-get update && sudo apt-get install adobe-flashplugin".

Otherwise try installing "flashplugin-installer".

Many thanks for your help, SeijiSensei

In this way I've solve the problem, although I'll try to make it work with windows version when i'll have some time

Regards

---

### Post by jpvrlau on 2015-03-05
What is that status on this because I am experiencing the same difficulty.   
I get the exact same results from "apt-cache policy flashplugin-installer" listed above but adobe's version test continued to report version ...125 instead of ... 442.
Tried using synaptic but now adobe's test just lists a black box and apps(like mlbtv) request an updated adobe version.  Gone from bad to worse.
There appears to be some disconnect with Firefox,Adobe, and Ubuntu. I would like to know if fkervin or anyone with Trusty 14.04 got the latest and greatest 11.2.202.442 correctly installed.

3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Intel® Core™ i5 CPU 650 @ 3.20GHz × 4

---

### Post by jwn-2 on 2015-03-28
I also have a problem here. I keep getting the message “Firefox has prevented the outdated plugin Adobe Flash from running” or “The plugin is vulnerable and should be updated”, and then it offers to check for updates. However when I try to update it just seems to re-install the same version (11.2.202.378) again and the messages stays there. What must I do to get version ...442 or later installed?

---

### Post by buzzingrobot on 2015-03-28
> **jwn-2 said:**
> I also have a problem here. I keep getting the message &#8220;Firefox has prevented the outdated plugin Adobe Flash from running&#8221; or &#8220;The plugin is vulnerable and should be updated&#8221;, and then it offers to check for updates. However when I try to update it just seems to re-install the same version (11.2.202.378) again and the messages stays there. What must I do to get version ...442 or later installed?

11.2.202.451 is the current version. It's the only version available in any official Ubuntu repo for any supported release. All Flash updates for Ubuntu will be installed during routine system updates by the user. After it's installed and Firefox is restarted, it should be listed in Tools->AddOns->Plugins.  

Don't try to install or update Flash from within Firefox.  I.e., from one of those popups.

---

### Post by jwn-2 on 2015-03-28
Wel it doesn't seem to be installed during routine system updates for me. And if I am not supposed to update it from within Firefox, then how am I suppose to do it then???

---

### Post by buzzingrobot on 2015-03-28
> **jwn-2 said:**
> Wel it doesn't seem to be installed during routine system updates for me. And if I am not supposed to update it from within Firefox, then how am I suppose to do it then???

If your system is not updating from the repos, then your system is not functioning correctly. Flash updates appear in the repos very, very quickly after Adobe releases them.

---

