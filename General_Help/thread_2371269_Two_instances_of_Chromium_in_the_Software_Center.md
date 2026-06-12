---
title: "Two instances of Chromium in the Software Center"
date: 2017-09-12
forum: General Help
---

### Post by altesk on 2017-09-12
I just opened the Ubuntu Software Center in my 16.04 LTS computer. After searching for "chromium" it showed three results, two of which have identical text descriptions. The only difference is that one is called "chromium" and has no star rating, while the other is called "Chromium Web Browser" and shows four stars.

Has anyone else noticed this? How do the versions differ?

---

### Post by vasa1 on 2017-09-12
I see```
$ apt list --all-versions | grep -i chromium

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

chromium-browser/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 amd64
chromium-browser/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-browser-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 amd64
chromium-browser-dbg/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-browser-l10n/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 all
chromium-browser-l10n/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 all
chromium-browser-l10n/xenial 49.0.2623.108-0ubuntu1.1233 all
chromium-bsu/xenial 0.9.15.1-1 amd64
chromium-bsu-data/xenial 0.9.15.1-1 all
chromium-chromedriver/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 amd64
chromium-chromedriver/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-chromedriver-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 amd64
chromium-chromedriver-dbg/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-codecs-ffmpeg/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 amd64
chromium-codecs-ffmpeg/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-codecs-ffmpeg-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 amd64
chromium-codecs-ffmpeg-dbg/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-codecs-ffmpeg-extra/xenial-updates,xenial-security,now 60.0.3112.113-0ubuntu0.16.04.1298 amd64 [installed,automatic]
chromium-codecs-ffmpeg-extra/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-codecs-ffmpeg-extra-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 amd64
chromium-codecs-ffmpeg-extra-dbg/xenial 49.0.2623.108-0ubuntu1.1233 amd64
chromium-lwn4chrome/xenial 1.0-2 all
unity-chromium-extension/xenial 3.2.0+15.04.20150119-0ubuntu1 amd64
unity-scope-chromiumbookmarks/xenial 0.1+13.10.20130723-0ubuntu1 all
$ 
```What do you see with the same command and which two have "identical text descriptions?"

---

### Post by altesk on 2017-09-12
After typing in Terminal the command you suggested, I see this:

```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

chromium-browser/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 i386
chromium-browser/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-browser-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 i386
chromium-browser-dbg/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-browser-l10n/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 all
chromium-browser-l10n/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 all
chromium-browser-l10n/xenial 49.0.2623.108-0ubuntu1.1233 all
chromium-bsu/xenial 0.9.15.1-1 i386
chromium-bsu-data/xenial 0.9.15.1-1 all
chromium-chromedriver/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 i386
chromium-chromedriver/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-chromedriver-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 i386
chromium-chromedriver-dbg/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-codecs-ffmpeg/xenial-updates,xenial-security 60.0.3112.113-0ubuntu0.16.04.1298 i386
chromium-codecs-ffmpeg/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-codecs-ffmpeg-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 i386
chromium-codecs-ffmpeg-dbg/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-codecs-ffmpeg-extra/xenial-updates,xenial-security,now 60.0.3112.113-0ubuntu0.16.04.1298 i386 [installed]
chromium-codecs-ffmpeg-extra/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-codecs-ffmpeg-extra-dbg/xenial-updates,xenial-security 51.0.2704.79-0ubuntu0.16.04.1.1242 i386
chromium-codecs-ffmpeg-extra-dbg/xenial 49.0.2623.108-0ubuntu1.1233 i386
chromium-lwn4chrome/xenial 1.0-2 all
unity-chromium-extension/xenial 3.2.0+15.04.20150119-0ubuntu1 i386
unity-scope-chromiumbookmarks/xenial,now 0.1+13.10.20130723-0ubuntu1 all [installed,automatic]
```


Software Center indicates version 60.0.3112.101 for the one labeled "chromium". Software Center indicates version 60.0.3112.113-0ubuntu0.16.04.1298 for the one labeled "Chromium Web Browser".

---

### Post by vasa1 on 2017-09-13
Clarification: I don't use any Software Center nor have I installed chromium-browser. I use the command-line and apt-get to manage software.
```
$ apt policy chromium-browser
chromium-browser:
  Installed: (none)
  Candidate: 60.0.3112.113-0ubuntu0.16.04.1298
  Version table:
     60.0.3112.113-0ubuntu0.16.04.1298 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     49.0.2623.108-0ubuntu1.1233 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
$ 
```indicates that chromium-browser version 60.0.3112.113 would be installed if I ran```
sudo apt-get install chromium-browser
```
You can try a simulation for yourself by using "-s" and *sudo* isn't needed for the simulation:```
$ apt-get install -s chromium-browser
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  chromium-browser-l10n
Suggested packages:
  webaccounts-chromium-extension unity-chromium-extension adobe-flashplugin
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst chromium-browser (60.0.3112.113-0ubuntu0.16.04.1298 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])                          
Inst chromium-browser-l10n (60.0.3112.113-0ubuntu0.16.04.1298 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])                       
Conf chromium-browser (60.0.3112.113-0ubuntu0.16.04.1298 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])                          
Conf chromium-browser-l10n (60.0.3112.113-0ubuntu0.16.04.1298 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])                       
$
```

---

### Post by altesk on 2017-09-13
I tried that "apt policy" command and saw a very similar result (same version number as in your result). Does that imply that I should prefer that version of Chromium instead of the 60.0.3112.101 version shown in Ubuntu Software Center?

The mystery remains: why is Software Center offering me the 60.0.3112.101 option?

---

### Post by vasa1 on 2017-09-13
> **altesk said:**
> I tried that "apt policy" command and saw a very similar result (same version number as in your result). Does that imply that I should prefer that version of Chromium instead of the 60.0.3112.101 version shown in Ubuntu Software Center?

The mystery remains: why is Software Center offering me the 60.0.3112.101 option?Later versions of any software offer bug fixes relating to security and other aspects to fix issues discovered in the previous version.

As to the mystery, I avoid using the software center. Perhaps someone else maybe able to address the point.

Just out of interest, what happens when you search for *chromium-browser* instead of just *chromium*?

---

### Post by mc4man on 2017-09-13
The one named just chromium is a snap, see Source in screenshot

---

### Post by vasa1 on 2017-09-13
> **mc4man said:**
> The one named just chromium is a snap, see Source in screenshot
That should solve OP's mystery :)

---

### Post by altesk on 2017-09-15
> **vasa1 said:**
> Just out of interest, what happens when you search for *chromium-browser* instead of just *chromium*?

Sorry for the delay. Searching for chromium-browser yields just one search result, which is the "Chromium Web Browser" (not Snap). This is the version I decided to install.

I'd never heard of the Snap technology until reading the answers to my post here. Maybe I will try it in the future.

Thanks to the people replying to my posts here.

---

