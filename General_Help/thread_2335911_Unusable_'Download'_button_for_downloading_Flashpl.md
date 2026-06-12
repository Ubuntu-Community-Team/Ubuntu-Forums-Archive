---
title: "Unusable 'Download' button for downloading Flashplayer for Linux"
date: 2016-09-02
forum: General Help
---

### Post by makem2 on 2016-09-02
I need Adobe Flashplayer to watch embedded video in web pages.

The video states, "Download Flashplayer now" but I am then redirected to:

[https://get.adobe.com/flashplayer/?no_redirect](https://get.adobe.com/flashplayer/?no_redirect)

Where the 'Download' button is not active so I cannot download.

It has been suggested I get an old version of Flashplayer to then update it or install Java script.

Any suggestions?

---

### Post by howefield on 2016-09-02
I'd suggest that you open the Software & Updates application and enable the "Canonical Partners" repository from the "Other Software" tab. Close out and reload your software sources (which you should be prompted to do) then install with

```
sudo apt install adobe-flashplugin
```

---

### Post by mook765 on 2016-09-02
Try this add-on:
[https://addons.mozilla.org/en-US/firefox/addon/video-without-flash/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/video-without-flash/?src=ss)
Maybe better than flashplayer which is out of date for several years.
WOrks just fine for me...

---

### Post by makem2 on 2016-09-02
> **howefield said:**
> I'd suggest that you open the Software & Updates application and enable the "Canonical Partners" repository from the "Other Software" tab. Close out and reload your software sources (which you should be prompted to do) then install with

```
sudo apt install adobe-flashplugin
```

Installed but has no effect either on video or the 'Download' button using Chromium.

---

### Post by Dennis N on 2016-09-02
> **makem2 said:**
> Installed but has no effect either on video or the 'Download' button using Chromium.

On Adobe's page, you must select version to download in the dropdown box at the left. Then the button to download will be active.

That said, if you have just installed adobe-flashplugin, you already have what you need. In addition, you get updates automatically in the future as well.

---

### Post by howefield on 2016-09-03
> **makem2 said:**
> Installed but has no effect either on video or the 'Download' button using Chromium.

Do you get a version number at the following page ?

[http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

If you have installed adobe-flashplugin you should have version 22.0.0.209 in Chromium - the current and up to date version.

---

### Post by makem2 on 2016-09-03
No, I don't get a version number, just a jigsaw piece.

---

### Post by makem2 on 2016-09-03
> **Dennis N said:**
> On Adobe's page, you must select version to download in the dropdown box at the left. Then the button to download will be active.

That said, if you have just installed adobe-flashplugin, you already have what you need. In addition, you get updates automatically in the future as well.

I didn't select the other version which did enable the download button because it had my correct version and Chrome. The othere option was for 'other linux'.

Anyhow, I have downloaded what it gave and now will see if I can find how to deal with the file..

---

### Post by makem2 on 2016-09-03
I have downloaded the file for 'other linux' and extracted the file libpepflashplayer.so

I copied it to usr/lib and installed it as root using # ldconfig -n -v /usr/lib

I still get the request to download flashplayer and using the web page to check if I have a version installed, I get the same jigsaw piece.

Edit: I have also copied the file to firefox plugins folder but get the same result. Maybe a reboot is needed. Will try tomorrow.

---

### Post by makem2 on 2016-09-04
Download the file, extracted and installed libpepflashplayer.so to usr/lib as one method suggested and also to firefox plugins directory suggested by firefox. Neither worked.

---

### Post by howefield on 2016-09-04
> **makem2 said:**
> No, I don't get a version number, just a jigsaw piece.

Hmm.. with a clean machine here is how I installed flash for Chromium (and Firefox).

In terminal install Chromium.

```
hugh@xenial-laptop:~$ sudo apt install chromium-browser
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  chromium-browser-l10n
Suggested packages:
  webaccounts-chromium-extension unity-chromium-extension adobe-flashplugin
The following NEW packages will be installed
  chromium-browser chromium-browser-l10n
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 73.9 MB of archives.
After this operation, 282 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 chromium-browser amd64 51.0.2704.79-0ubuntu0.16.04.1.1242 [70.6 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 chromium-browser-l10n all 51.0.2704.79-0ubuntu0.16.04.1.1242 [3,266 kB]                   
Fetched 73.9 MB in 22s (3,339 kB/s)                                                                                                                               
Selecting previously unselected package chromium-browser.
(Reading database ... 251847 files and directories currently installed.)
Preparing to unpack .../chromium-browser_51.0.2704.79-0ubuntu0.16.04.1.1242_amd64.deb ...
Unpacking chromium-browser (51.0.2704.79-0ubuntu0.16.04.1.1242) ...
Selecting previously unselected package chromium-browser-l10n.
Preparing to unpack .../chromium-browser-l10n_51.0.2704.79-0ubuntu0.16.04.1.1242_all.deb ...
Unpacking chromium-browser-l10n (51.0.2704.79-0ubuntu0.16.04.1.1242) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up chromium-browser (51.0.2704.79-0ubuntu0.16.04.1.1242) ...
Setting up chromium-browser-l10n (51.0.2704.79-0ubuntu0.16.04.1.1242) ...
```

At this stage obviously with no flash installed the [about flash]("https://www.adobe.com/au/software/flash/about/") page shows the "jigsaw" piece. Seeing as I am in terminal anyway, edit apt sources to enable the Partners repository - scrolling down to the Partners line and removing the # sign. Close out with Ctrl + O, enter and Ctrl +X.

```
hugh@xenial-laptop:~$ sudo apt edit-sources
Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.tiny

Choose 1-3 [2]: 
Your '/etc/apt/sources.list' file changed, please run 'apt-get update'.
```

Do a sudo apt update and sudo apt install adobe-flashplugin.

```
hugh@xenial-laptop:~$ sudo apt update
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease               
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                      
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:6 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages [2,712 B]
Get:7 http://archive.canonical.com/ubuntu xenial/partner i386 Packages [3,016 B]
Get:8 http://archive.canonical.com/ubuntu xenial/partner Translation-en [1,424 B]
Hit:9 https://repo.skype.com/deb stable InRelease         
Hit:10 https://deb.opera.com/opera-stable stable InRelease
Fetched 18.6 kB in 0s (23.4 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
hugh@xenial-laptop:~$ sudo apt install adobe-flashplugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera | ttf-dejavu ttf-xfree86-nonfree xfs libnspr4-0d libnss3-1d
The following packages will be REMOVED
  flashplugin-installer
The following NEW packages will be installed
  adobe-flash-properties-gtk adobe-flashplugin
0 to upgrade, 2 to newly install, 1 to remove and 1 not to upgrade.
Need to get 10.4 MB of archives.
After this operation, 38.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.canonical.com/ubuntu xenial/partner amd64 adobe-flashplugin amd64 1:20160712.1-0ubuntu0.16.04.1 [10.3 MB]
Get:2 http://archive.canonical.com/ubuntu xenial/partner amd64 adobe-flash-properties-gtk amd64 1:20160712.1-0ubuntu0.16.04.1 [113 kB]
Fetched 10.4 MB in 3s (2,717 kB/s)                  
(Reading database ... 252415 files and directories currently installed.)
Removing flashplugin-installer (11.2.202.632ubuntu0.16.04.1) ...
Processing triggers for update-notifier-common (3.168.1) ...
Selecting previously unselected package adobe-flashplugin.
(Reading database ... 252395 files and directories currently installed.)
Preparing to unpack .../adobe-flashplugin_1%3a20160712.1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking adobe-flashplugin (1:20160712.1-0ubuntu0.16.04.1) ...
Selecting previously unselected package adobe-flash-properties-gtk.
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20160712.1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20160712.1-0ubuntu0.16.04.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up adobe-flashplugin (1:20160712.1-0ubuntu0.16.04.1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20160712.1-0ubuntu0.16.04.1) ...
hugh@xenial-laptop:~$
```

If the browser is open, close and restart, and the about flash page shows Firefox has version 11,2,202,632 installed and Chromium has 22,0,0,209 installed. Perhaps it might be worth purging all that you have done and starting again.

---

### Post by pqwoerituytrueiwoq on 2016-09-04
You can use pepper flash in both firefox and chrome
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
not sure if this will still work next year though
[http://arstechnica.com/information-technology/2015/10/firefox-dropping-npapi-plugins-by-the-end-of-2016except-for-flash/](http://arstechnica.com/information-technology/2015/10/firefox-dropping-npapi-plugins-by-the-end-of-2016except-for-flash/)

---

### Post by buzzingrobot on 2016-09-04
> **makem2 said:**
> I need Adobe Flashplayer to watch embedded video in web pages.

The video states, "Download Flashplayer now" but I am then redirected to:

[https://get.adobe.com/flashplayer/?no_redirect](https://get.adobe.com/flashplayer/?no_redirect)

Where the 'Download' button is not active so I cannot download.

It has been suggested I get an old version of Flashplayer to then update it or install Java script.

Any suggestions?


Don't use this approach.  It targets Windows and I've never known it to work in any Linux installation.

The correct Flash plugin is installed if you select the option to include additional proprietary material when you install Ubuntu.  If you did not do that, it can be added as outlined earlier in this thread. This will ensure you receive the frequent security updates Adobe release for Flash. Canonical packages these and releases them for Ubuntu very quickly.

Be aware that Adobe distributes multiple, different, versions of Flash.  The version Adobe distributes for Linux receives security fixes but it has seen no feature updates in a few years.  The version Adobe distributes for Windows receives both security and feature updates.  Also, Google has an exclusive arrangement with Adobe that allows it to ship yet another version, with feature and security updates, with Google Chrome. How-to's for cajoling that version to work in Firefox are available around the net.

---

### Post by Dennis N on 2016-09-04
> **makem2 said:**
> Download the file, extracted and installed libpepflashplayer.so to usr/lib as one method suggested and also to firefox plugins directory suggested by firefox. Neither worked.

Well, if you must use the Adobe page download, you do select the ".tar.gz for other linux" option (that's the only option, I think, if you access the page with Chromium). 

Then you have to know where the existing active plugin is installed on your system - if you use some other location, you probably will just keep using the old plugin. Once you know that, close the browser and extract the plugin (libpepflashplayer.so) from the .tar.gz archive and copy it to the same location - overwriting the old one. 

But, as has been suggested, installing adobe-flashplugin is the simple and preferred way to handle this for both Firefox and Chromium.

---

### Post by Desert_Outlaw on 2016-09-08
Are you using a different browser other than Firefox, Opera, or Chrome? There is a Shockwave Flash plugin available for Firefox under addons, and both Opera & Chrome have the feature built in. Vivaldi is pure chance trying to install pepperflash.

---

