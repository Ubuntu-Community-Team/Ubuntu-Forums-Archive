---
title: "Having all sorts of package software issues (packages not found etc)"
date: 2018-01-25
forum: General Help
---

### Post by Demosthenesaus on 2018-01-25
Hi all...

I have followed all the usual instructions online about sudo apt-get update etc, but I am getting all sorts of issues with the software repositories - e.g

sudo apt-get install ubuntu-restricted-extras
E: Unable to locate package ubuntu-restricted-extras

And errors like this when I run apt-get update..

Any help appreciated... I've tried everything I can think of including resetting the software sources to 'main'...  Thanks...

```
Ign:11 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease
Hit:12 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                                        
Err:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty Release                                              
  404  Not Found [IP: 91.189.88.161 80]                                                            
Err:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates Release                                       
  404  Not Found [IP: 91.189.88.161 80]   
Err:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main amd64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main all Packages
Ign:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main i386 Packages
Ign:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en_AU
Ign:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main Translation-en
Ign:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main amd64 DEP-11 Metadata
Ign:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 128x128 Icons
Ign:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/restricted i386 Packages
Ign:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Err:54 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
  404  Not Found [IP: 91.189.88.161 80]

Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu zesty-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en_AU) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:8
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target Translations (restricted/i18n/Translation-en_AU) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:13
```

---

### Post by slickymaster on 2018-01-25
apt is telling you what the problem is, Zesty is/was only supported for 9 months until January 2018, hence the reason you're getting those errors and warnings. I'd recommend you either to upgrade to Ubuntu 17.10 or install Ubuntu 16.04.

But in case you still want to get zesty packages, you can use the [old-releases site]("http://old-releases.ubuntu.com/releases/"), to install them.

---

### Post by Demosthenesaus on 2018-01-28
I apologise, I omitted my system information (very poor of me).  I am actually running KUbuntu 17.04.  17.10 was not listed on the site due to issues, and it received some very poor reviews, so I stuck with 17.04 as the 'last stable version'.

If these issues have now been resolved, it may be worth upgrading to KUbuntu 17.10 now.  I just assumed I would be prompted to do that when ready.  There is no 'distribution upgrade' available in Software Centre (which is also now often hanging and crashing for some reason)...

So this is why I cannot install kubuntu-restricted-extras among other issues?

now when I try installing kubuntu or just ubuntu-restricted-extras I get "E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?" - which doesn't seem to fix anything f I run it...

Thanks...

---

### Post by Demosthenesaus on 2018-02-04
Is there any way to just reset it all to default...  Now packages keep 'failing to download' even in the package manager and I have no idea why, no matter what I do.

---

### Post by oldos2er on 2018-02-04
Support for 17.04 ended last month, which is why the package manager can't locate any updates or packages. I suggest you install 17.10.1.

---

### Post by vasa1 on 2018-02-04
> **Demosthenesaus said:**
> I apologise, I omitted my system information (very poor of me).  I am actually running KUbuntu 17.04.  17.10 was not listed on the site due to issues, and it received some very poor reviews, so I stuck with 17.04 as the 'last stable version'.

...
If you don't like 17.10, install 16.04. It will be supported longer than 17.10.

---

### Post by Topsiho on 2018-02-04
I don't think the OP has a clue as to the  rationale behind the (correct) answers he gets.

(K)Ubuntu is released as LTS every two years, in April, the latest one is (K)Ubuntu 16.04 LTS, the next one will be (K)Ubuntu 18.04 LTS, next April
LTS versions are maintained 5 years.
Intermediate versions, every 6 months, will only be maintained during 9 months after their releases.
That's why the support of Zesty (17.04) has just been ended.

My advise is to install 16.04.3 (the latest point release, I think) and use that until 18.04 LTS is out for a few month, giving that time so that all initial problems are solved :)
Unles he wants to be adventurous and install the latest intermediate release, which is 17.10.1. Be careful not to use 17.10 (without .1) as that version is broken and might ruin your computer.


Topsiho

---

### Post by Demosthenesaus on 2018-02-05
It's not that I "don't like" 17.10 - it is that Ubuntu's **own website** explicitly warned **against** installing KUbuntu 17.10, and advised to install 17.04 instead, which I did.
So should I just dist-upgrade to 17.10 then?  I am just going by Ubuntu's own advice here, not subjective opinion.  There were also reviews scathing of 17.10, which kind of supported Ubuntu's own warning to not install it.  I don't know why Ubuntu would point users to 17.04 if there was not some sort of resolution available in the near future or something.

Reinstalling everything would be a royal pain in the butt.  I am dual-booting successfully with a full partition encrypted KUbuntu setup, with Windows 10, after much painful research about how to set up a dedicated encrypted partition when dual booting because the installer, for whatever reason, will only support encryption when not dual booting (even though it seems to work fine after manual intervention, but anyway).

So...  Should I just wait until whatever the show-stopper issues are with 17.10 are resolved.  It seems odd to downgrade, then upgrade again shortly after, if that's what is causing all these package issues.

dist-upgrade and software manager do not prompt to upgrade to 17.10 - is this why?

---

### Post by deadflowr on 2018-02-05
> Ubuntu's own website explicitly warned against installing KUbuntu 17.10,
Link please.
I do not remember that ever happening.

Perhaps you are thinking of the kernel bug Ubuntu had regrading enabling the [buggy intel_spi driver for 17.10]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147").
That actually affected all Ubuntu flavors, and was fixed with Ubuntu 17.10.1.
Subsequently, all other flavors also rebuilt new 17.10.1 versions.
So you can download and install that version now.

---

### Post by Demosthenesaus on 2018-02-06
It was from the official download page - [https://kubuntu.org/getkubuntu/](https://kubuntu.org/getkubuntu/) - which obviously doesn't have it anymore - so I guess whatever the issue was is now fixed.

However, I can't work out how to upgrade...  All I am getting is the below, and nothing in the software manager that I can find..

Looks like I could be in luck

ran this

kdesudo "do-release-upgrade -m desktop -f DistUpgradeViewKDE"

And some movement..  I'll try later when I am on an appropriate network.

---

### Post by Demosthenesaus on 2018-02-23
Worked!!!  Upgraded fine... so that obscure command above was the trick.  This should be more clearly documented for newbies so they know..  Nothing else would work but it seems happy now.

---

### Post by Topsiho on 2018-02-24
Great. Thank you for reporting your success!

In a previous post you mentioned that the (K)Ubuntu site warned you against using 17.10. That was when the then valid release of Ubuntu 17.10, and probably Kubuntu too, had a very severe bug, that even could ruin your computer. The present release, Ubuntu 17.10.1, doesn't have that bug, so there is no problem now, using 17.10(.1).

Ubuntu 17.10 will be supported for only 9 months, from October 2017, so be prepared that you'll have to upgrade again very soon. To 18.04 (released end of April, or 16.04. Both are LTS (Long time Support) which are maintained for 5 years after their releases.

Topsiho

---

### Post by SeijiSensei on 2018-02-24
I've been using the daily build for Kubuntu 18.04, with frequent updates, for about a month now.  Overall I haven't had any issues.

If you want to give that a try, the ISO is here: [http://cdimage.ubuntu.com/kubuntu/daily-live/current/HEADER.html](http://cdimage.ubuntu.com/kubuntu/daily-live/current/HEADER.html)

---

