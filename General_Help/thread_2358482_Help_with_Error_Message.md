---
title: "Help with Error Message"
date: 2017-04-14
forum: General Help
---

### Post by agemini68 on 2017-04-14
This particular error message is hard, I can't get past it, even tried updating to 16.10. It won't let me work with update manager, package manager or access anything that will help. Anyone else run across this? I have a screenshot in the attachement

This is what happens if I try to run the package manager.

---

### Post by RobGoss on 2017-04-14
Hello and welcome to the forum, There seems to be some applications that may not be supported, from the second screen shot you posted there should be some sort of errors messages at the bottom of the window at this point I am unable to see any 

Try running the updater again and this time copy & pasted the results and post then here using the code **tags**

---

### Post by agemini68 on 2017-04-14
the attachment shows what happens when I run the updater. I also tried to upgrade to 16.10 and it got stuck in a loop for hours under saving installed packages. I can't uninstall anything or update anything. I'd rather not delete my entire hard drive, but it looks like I might have to try to save my files and do that if no one has a solution.

I'm not sure what are the code tags? where do I find that?

IDK if this helps, I get this when I hit check for updates.

---

### Post by deadflowr on 2017-04-14
Code tags for beginners:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by Impavidus on 2017-04-14
For more readable output, formatted in a standard way, we prefer terminal output on the forum, copy-pasted in code tags from the terminal. The extra bonus is that the terminal gives clearer error messages. We are interested in the output from```
sudo apt update
```and ```
sudo apt upgrade
```This will ask for your password. Just type it and hit enter. Nothing will show up.

Further note: The only error that can be fixed by a release upgrade (like 16.04 &#8594; 16.10) is a driver problem. In all other cases it will make things worse.

---

### Post by agemini68 on 2017-04-15
```
donna@donna-560GE:~$ sudo apt update
[sudo] password for donna: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]     
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Ign:6 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/allvideodownloader/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/allvideodownloader/ubuntu) xenial InRelease
Err:7 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/allvideodownloader/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/allvideodownloader/ubuntu) xenial Release
  404  Not Found
Get:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Sources [2,316 B]
Get:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages [2,960 B]
Get:10 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Translation-en [1,424 B]
Err:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages         
  Hash Sum mismatch
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [500 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [289 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [190 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [443 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 DEP-11 Metadata [160 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [7,720 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 DEP-11 Metadata [2,516 B]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 DEP-11 Metadata [3,324 B]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [54.6 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [42.4 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe i386 DEP-11 Metadata [32.2 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Reading package lists... Error!                                                
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:77
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:108
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:139
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:170
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
E: The repository 'https://private-ppa.launchpad.net/commercial-ppa-uploaders/allvideodownloader/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:77
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:108
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:139
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:170
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
donna@donna-560GE:~$
```

```
donna@donna-560GE:~$ sudo apt upgrade
[sudo] password for donna: 
Reading package lists... Error!
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:77
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:108
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:139
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:170
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:76
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:107
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:138
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:169
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
donna@donna-560GE:~$
```

---

### Post by RobGoss on 2017-04-15
Try removing the following **PPA**, go to** Software & updates** choose **Other software** you will see a list of resources Uncheck the **PPA** indicated below

```
Err:7 https://private-ppa.launchpad.net/co...nloader/ubuntu xenial Release
  404  Not Found
```

Then try running the updater again, You can also try changing your download source, **Software & Updates** click on the drop **Down menu**, then choose other, pick the best location from the list for your area

---

### Post by agemini68 on 2017-04-16
I think the problem is with an app called All Video Downloader I installed from the software center. I did try unchecking it, and it didn't work. The other one you listed isn't there. I got there is a serious problem when I tried to udpate.

Good Lord, I can't uninstall it. All Video Downloader

---

### Post by howefield on 2017-04-16
Try unchecking all the repositories shown in the above image.

Open a terminal and try the following command..

```
sudo apt update
``` 

does it complete without error, if not post the output back here ?

---

### Post by agemini68 on 2017-04-16
That did it, thank you!

---

### Post by RobGoss on 2017-04-16
I know you stated that did it, but what exactly did it do? would you like to share your results with us is might help others with this same issue

---

### Post by howefield on 2017-04-16
> **agemini68 said:**
> That did it, thank you!

Cool, well done.

Now you need to decide if you need the PPAs that have been deselected, so if you have installed anything from the Partners repository recheck the first one (you won't need the source repository enabling) and you can right click on the other Partners sources and remove.

The private commercial-ppa-uploaders repo I know nothing of but if that is where the allvideodownloader came from you will need to find out if there is a Xenial repository for it, you won't get any updates for the package if you don't, if indeed there are any.

---

