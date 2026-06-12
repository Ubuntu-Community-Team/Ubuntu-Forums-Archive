---
title: "completely uninstalling Google Chrome"
date: 2018-02-11
forum: General Help
---

### Post by ulissipus on 2018-02-11
Would anyone teach me how to uninstall completely Google Chrome? I did it via Software manager, then Synaptic to delete "Google-Chrome-Stable". But whenever I use a mail programme I get the following error message:

[INDENT][/INDENT] Failed to execute the default Web browser  /  Failed to execute child process "/usr/bin/google-chrome-stable" (no such file or directory)

I never chose it to be my "default Web Browser".

Any guidance very much appreciated.

---

### Post by deadflowr on 2018-02-11
You probably set it without any realization you did.
It'll give the option the first time you start chrome, if you hit the option it sets it as default.
What browser is your actual default?
If firefox, then simply go to the hamburger setting icon then to preferences.
It will have an option to set it as default
(It'll have a line saying firefox is not the default browser, and a "make default" button, click on the button and firefox will be set as the new default.)

---

### Post by ulissipus on 2018-02-12
I thought so too. I use either Firefox or Opera and have made Firefox the default browser. 

I also thought I had wiped out Google Chrome. I didn't obviously. I still get that error message on launching Firefox, for instances.

But I cannot find "google-chrome-stable" in "/usr/bin/"...

---

### Post by vasa1 on 2018-02-12
Try ```
locate google-chrome-stable
```and even```
locate chromium-browser
```just in case.

You wrote> But whenever I use **a mail programme** I get the following error message:

Failed to execute the default Web browser / Failed to execute child process "/usr/bin/google-chrome-stable" (no such file or directory)
Could you share the identity of the mail program? Could it be possible that the mail program is internally set to use a particular browser?

---

### Post by ulissipus on 2018-02-12
Tks. I never touched in Chromium. The commant  --  locate google-chrome-stable --  gave back:

```
lostados@lostados:~$ locate google-chrome-stable
/usr/bin/google-chrome-stable
/usr/share/doc/google-chrome-stable
/usr/share/icons/Moka/16x16/apps/google-chrome-stable.png
/usr/share/icons/Moka/16x16@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/22x22/apps/google-chrome-stable.png
/usr/share/icons/Moka/22x22@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/24x24/apps/google-chrome-stable.png
/usr/share/icons/Moka/24x24@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/256x256/apps/google-chrome-stable.png
/usr/share/icons/Moka/256x256@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/32x32/apps/google-chrome-stable.png
/usr/share/icons/Moka/32x32@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/48x48/apps/google-chrome-stable.png
/usr/share/icons/Moka/48x48@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/64x64/apps/google-chrome-stable.png
/usr/share/icons/Moka/64x64@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/96x96/apps/google-chrome-stable.png
/usr/share/icons/Moka/96x96@2x/apps/google-chrome-stable.png
/usr/share/man/man1/google-chrome-stable.1.gz
/var/cache/apt/archives/google-chrome-stable_64.0.3282.119-1_amd64.deb
/var/lib/dpkg/info/google-chrome-stable.list
/var/lib/dpkg/info/google-chrome-stable.md5sums
/var/lib/dpkg/info/google-chrome-stable.postinst
/var/lib/dpkg/info/google-chrome-stable.postrm
/var/lib/dpkg/info/google-chrome-stable.prerm
lostados@lostados:~$ 
```

How to proceed? Select all and delete?

---

### Post by vasa1 on 2018-02-12
> **ulissipus said:**
> ... How to proceed? Select all and delete?
Run```
sudo apt-get update
```and```
sudo apt-get upgrade
```and```
sudo apt-get purge google-chrome-stable
```and post the complete output here.

---

### Post by ulissipus on 2018-02-13
Thank you. I had thought of that too. However, the output was:

```
lostados@lostados:~$ sudo apt-get purge google-chrome-stable
[sudo] password for lostados: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable
lostados@lostados:~$
```

---

### Post by vasa1 on 2018-02-13
Reminder: please provide the output of ```
sudo apt-get update
```and```
sudo apt-get upgrade
```

---

### Post by ulissipus on 2018-02-13
Sorry. There it goes:

Update:

```
lostados@lostados:~$ sudo apt-get update
[sudo] password for lostados: 
Hit:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:3 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease                              
Get:4 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Ign:7 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial InRelease   
Hit:8 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial InRelease
Hit:9 [http://ppa.launchpad.net/jconti/recent-notifications/ubuntu](http://ppa.launchpad.net/jconti/recent-notifications/ubuntu) xenial InRelease
Hit:10 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease
Hit:11 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease              
Hit:12 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) xenial InRelease       
Get:13 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [715 kB]
Hit:14 [http://ppa.launchpad.net/moka/daily/ubuntu](http://ppa.launchpad.net/moka/daily/ubuntu) xenial InRelease             
Get:15 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [665 kB]
Get:16 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:17 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [221 kB]
Hit:18 [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) xenial InRelease         
Get:19 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [582 kB]
Get:20 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [540 kB]
Get:21 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:22 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [272 kB]
Hit:23 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) xenial InRelease              
Get:24 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5.888 B]
Get:25 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3.328 B]
Get:26 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4.696 B]
Hit:27 [http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu) xenial InRelease
Hit:28 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial InRelease
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67,5 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [72,2 kB]
Ign:31 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial Release    
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51,3 kB]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85,1 kB]
Ign:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Err:34 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:35 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:36 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:37 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_US
Ign:38 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:39 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:40 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 4.089 kB in 22s (183 kB/s)
Reading package lists... Done
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: The repository 'http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/opera-stable.list:4
lostados@lostados:~$ 
```

Upgrade:

```
lostados@lostados:~$ sudo apt-get upgrade
[sudo] password for lostados: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gir1.2-secret-1 git git-man gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-x kde-l10n-engb liberror-perl
  libglib2.0-dev libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libllvm4.0
  libpcre3-dev libpcre32-3 libpcrecpp0v5 libsecret-1-dev libtorrent-rasterbar8
  linux-headers-4.10.0-28 linux-headers-4.10.0-28-generic
  linux-headers-4.10.0-42 linux-headers-4.10.0-42-generic
  linux-headers-4.13.0-26 linux-headers-4.13.0-26-generic
  linux-image-4.10.0-28-generic linux-image-4.10.0-42-generic
  linux-image-4.13.0-26-generic linux-image-extra-4.10.0-28-generic
  linux-image-extra-4.10.0-42-generic linux-image-extra-4.13.0-26-generic
  pkg-config zlib1g-dev
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lostados@lostados:~$
```

---

### Post by deadflowr on 2018-02-13
Let's see what the system has to say about the state of chrome
```
dpkg -l | grep chrome | awk '{print $1,$2,$3}'
```
This will tell us the install state, if any, the names of the installed packages related to chrome, and the versions installed.

---

### Post by ulissipus on 2018-02-13
no result whatsoever.  :confused:

No results whatsoever.

lostados@lostados:~$ dpkg -l | grep chrome | awk '{print $1,$2,$3}'
lostados@lostados:~$:confused:

---

### Post by deadflowr on 2018-02-13
Does locate still show /usr/bin/google-chrome-stable ?

---

### Post by ulissipus on 2018-02-16
Yes. There follows the output:

```
lostados@lostados:~$ locate google-chrome-stable
/usr/share/icons/Moka/16x16/apps/google-chrome-stable.png
/usr/share/icons/Moka/16x16@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/22x22/apps/google-chrome-stable.png
/usr/share/icons/Moka/22x22@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/24x24/apps/google-chrome-stable.png
/usr/share/icons/Moka/24x24@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/256x256/apps/google-chrome-stable.png
/usr/share/icons/Moka/256x256@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/32x32/apps/google-chrome-stable.png
/usr/share/icons/Moka/32x32@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/48x48/apps/google-chrome-stable.png
/usr/share/icons/Moka/48x48@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/64x64/apps/google-chrome-stable.png
/usr/share/icons/Moka/64x64@2x/apps/google-chrome-stable.png
/usr/share/icons/Moka/96x96/apps/google-chrome-stable.png
/usr/share/icons/Moka/96x96@2x/apps/google-chrome-stable.png
/var/cache/apt/archives/google-chrome-stable_64.0.3282.119-1_amd64.deb
lostados@lostados:~$
```

---

### Post by deadflowr on 2018-02-16
The /usr/bin/google-chrome-stable is gone from the locate output.
In stark contrast to the output from post #5.

Is it still erring with the cannot find chrome line?

This
> Failed to execute the default Web browser / Failed to execute child process "/usr/bin/google-chrome-stable" (no such file or directory)

What's the overall status?

---

### Post by ulissipus on 2018-02-17
Yes. It pops up whenever I turn on the computer, before doing anything.

If I were on Windows, Id say that I had a virus of some sort. I didn't say but the reason why I decided to uninstall Google Chrome was that, on turning on the computer, it (Google) would pop up with a screen telling me to sign up or sign in Dropbox! Very annoying. I didn't succeed in stopping this page nor in unmaking GChrome "my default browser".

The browser is gone now but some part of it remains...

---

### Post by deadflowr on 2018-02-17
> Yes. It pops up whenever I turn on the computer, before doing anything.


Since Xubuntu look in the session startup settings.
That seems like a legacy startup issue.
Like it still thinks chrome is there.
[https://askubuntu.com/questions/369406/xubuntu-apps-loading-at-start-up]("https://askubuntu.com/questions/369406/xubuntu-apps-loading-at-start-up")

---

### Post by ulissipus on 2018-02-18
That did it! The culprit was not Chrome but Dropbox. I feel guilty for not stating the problem at the beginning: would have spared you time and work...

Thank you very much.  Best

---

### Post by cubiczx on 2018-05-03
```

sudo apt-get purge google-chrome-stable
sudo apt-get autoremove
rm -rf /home/xavier/.cache/google-chrome/
rm -rf ~/.config/google-chrome/
rm -rf .local/share/applications/chrome-*
rm -rf .local/share/applications/chrome-*
sudo rm -rf locate /usr/bin/google-chrome-stable /usr/share/doc/google-chrome-stable /usr/share/man/man1/google-chrome-stable.1.gz /var/lib/dpkg/info/google-chrome-stable.*

```

---

