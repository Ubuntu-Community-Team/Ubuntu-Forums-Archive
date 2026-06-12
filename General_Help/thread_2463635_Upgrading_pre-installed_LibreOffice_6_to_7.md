---
title: "Upgrading pre-installed LibreOffice 6 to 7"
date: 2021-06-15
forum: General Help
---

### Post by freesitebuilder on 2021-06-15
I'm running Ubuntu 20.04 LTS that was pre-installed, including Libre Office 6.3.6.2 which didn't work for a while but does now. I'd like to upgrade, but although LO tells me there's an upgrade, Ubuntu doesn't have it in software. Version shown for Writer is 1:6.4.7-0ubuntu0.20.04.1 which I think means it's not Snap?

I'm not a high-end user, so I'm really more concerned about updates that will get rid of any bugs or security issues, so is it worth just waiting until 7 reaches the repositories?

I'm also confused as to why Ubuntu doesn't auto-update - is it simply because the latest version isn't confirmed to be OK with Ubuntu yet? My settings include a Launchpad PPA for LibreOffice, and Software tab shows ppa selected for Bionic sourcecode, and "disabled for Focal" is not selected.

Thanks

---

### Post by CatKiller on 2021-06-15
> **freesitebuilder said:**
> I'm not a high-end user, so I'm really more concerned about updates that will get rid of any bugs or security issues, so is it worth just waiting until 7 reaches the repositories? 

Security updates and bugfixes get backported for all the software in the repositories. You don't need a higher version number for that. 

> My settings include a Launchpad PPA for LibreOffice, and Software tab shows ppa selected for Bionic sourcecode

Repositories for source code are only useful if you're compiling from source (which you aren't) and a Bionic repository is only useful if you're using Ubuntu 18.04 (which you aren't). You don't want to keep using that repository.

---

### Post by grahammechanical on 2021-06-15
> Version shown for Writer is 1:6.4.7-0ubuntu0.20.04.1 which I think means it's not Snap?

The Ubuntu developers take the LibreOffice code and build it into an application for Ubuntu. What you are quoting is the Ubuntu build number that can be used to identify which build of an app has a reported bug. The version of LibreOffice as shown in the "About" dialog is 6.4. I am on 20.04.2 which is an upgraded version of 20.04.1 and Writer has the same build number.

Ubuntu 20.04 will get version 7 of LibreOffice in time. New versions of applications such as LibreOffice and Firefox get back ported to the existing Long Term Support (LTS) versions of Ubuntu. 20.04 is LTS.

There is a version of LibreOffice that is packaged as a Snap in comparison to the traditional Deb package format. The Snap version of LibreOffice is at  version 7.1.3.2. Snap and Deb packaged versions of applications can be installed alongside each other and do not have conflict. 

[https://snapcraft.io/libreoffice](https://snapcraft.io/libreoffice)

Regards

---

### Post by rsteinmetz70112 on 2021-06-15
Unless you have a specific need, I'd stay with the standard version, as has been mentioned security fixes and bugs are back ported.

---

### Post by monkeybrain20122 on 2021-06-15
Add this ppa [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt upgrade

```

then you get LO 7.1.4rc2 (according to LO developers rc2 is practically the same as release)

This ppa is created by the same team who created the "official" packages.

A really cool selling point of Ubuntu is that there are many ways to get updated software, reputable PPA's like LO's are pretty safe to use. If I only stick with "official" repos and predictably broken versions of software because of "stability" I would use Debian (in Debian speak "stability" means basically predictability, that includes "predictably broken")

---

### Post by ajgreeny on 2021-06-15
Yes, go with what monkeybrain20122 says; I have been using that ppa for as long as it's been available and so far had absolutely no problems of any sort with its use.

Being a ppa you will get all upgrades as soon as they appear which is just about the same as downloading direct from Libreoffice itself but without the bother; the upgrades will appear just the same as any other package from the Ubuntu repos.

---

### Post by freesitebuilder on 2021-06-16
Thanks for all the info. One day I'll understand everything Ubuntu ... maybe!:D

---

### Post by cyver-yo on 2021-09-12
In my case, usability is the specific need.
If you have co-workers that use MS Office Suite, you may have noticed that LO 7 have several tweaks in compatibility (impress still lacks) absent from LO 6. As a remarkable example, LO 6 have issues with comments when a file is opened in Word (or Excel) and vice versa... so you may need install LO 7, that apparently fixed this issues (at least for me). However, if you avoid installing LO 6 from ubuntu repositories (via apt) by installing LO 7 from snap, you may find new additional issues. Two of the more annoying are 1) you can't open files in the home dir (/home/your-user-dir/) and you can't open files in fuse-mounted dirs (for example those mounted with rclone for Google Drive, One Drive, etc. even if these are mounted in /media/something) because of snap "security" restrictions; and 2) the PDF created by Export to PDF command menu, will have no images, you have to "Print to File... PDF" to obtain a complete file (good luck if you file supposed to have forms and fields).
So, in my experience, you should add LO PPA, as monkeybrain20122 posts below and upgrade to lo 7. I know that it may be a little unstable but at least allows me do collaborative work.

---

