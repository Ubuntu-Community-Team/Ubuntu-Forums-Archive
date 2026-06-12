---
title: "problem opening docs after upgrade of LibreOffice"
date: 2018-07-21
forum: General Help
---

### Post by edstevens on 2018-07-21
Ubuntu 16.04 LTS
Cinnamon desktop GUI

Recently I upgraded my LibreOffice installation from ver. 5 to ver. 6.  Now, when I navigate to a file with Nemo (say, an .odt file) and click on it, I get the splash banner for OL 6, but when it goes away, nothing more happens, the file is not opened.

In addition, if I open LO Write from the desktop icon and use it's menu to 'open', the resulting navigation, starting from "Other locations", "Computer", seems to position me at the root directory but doesn't show all of the directories that I know are there.

In addition (and of less importance right now), when I open the GUI (Cinnamon) "start" menu and the "Office" group, it shows two listings for the various apps (ie: Libre Office Write and Libre Office Write 6.0). If I click, say, Libre Office Write 6, the app comes up.  But if I click Libre Office Write, I get the v6 splash, and then again nothing.

---

### Post by TheFu on 2018-07-21
What happens if you run libreoffice from a terminal?  Any useful messages?

---

### Post by edstevens on 2018-07-21
From a terminal, 'libreoffice somefile.odt' again just gives me th v6 splash banner.

---

### Post by ajgreeny on 2018-07-21
How did you upgrade the LO version from 5 to 6?
Where in the filesystem are the executables of LO sitting at present?

---

### Post by TheFu on 2018-07-21
```
$ libreoffice --version
LibreOffice 5.1.6.2 10m0(Build:2)
```

Is what I see. Patched the system today.  How did you perform the new install, exactly?

---

### Post by The Cog on 2018-07-21
That's the kind of mess you get if you install LibreOffice from the download on the libreoffice.org site without uninstalling the version from the Ubuntu repositories. I did that once. I think you are hitting incompatibilities between the two versions, running bits of each.

If you install synaptic package manager you should be able to search for LibreOffice and see two different versions installed. You might be able to just uninstall the repo version, but it might be better to remove both versions and then reinstall the download (assuming that getting a download from libreoffice.org is what you did). I always remove the repo version before installing the download version.

---

### Post by TheFu on 2018-07-21
> **The Cog said:**
> That's the kind of mess you get if you install LibreOffice from the download on the libreoffice.org site without uninstalling the version from the Ubuntu repositories. I did that once. I think you are hitting incompatibilities between the two versions, running bits of each.

If you install synaptic package manager you should be able to search for LibreOffice and see two different versions installed. You might be able to just uninstall the repo version, but it might be better to remove both versions and then reinstall the download (assuming that getting a download from libreoffice.org is what you did). I always remove the repo version before installing the download version.

Yep.   Package management rules for a happy life, in order of priority:
[LIST=1]
[*]Always use the Canonical Repo
[*]Only if that doesn't functionally meet the requirements, use a trusted, reputable, PPA
[*]If there isn't a PPA, and you absolutely mush use a newer version, get a compatible .deb file from a trusted, reputable, source
[*]Lacking all of the above options, download source and compile/install it yourself, outside the normalinstllation areas.  This is what /usr/local/ is for.
[*]Update and patch every week.  If any parts of the system where installed using .deb or source, manually patch those weekly as well.
[/LIST]

If you use .deb files directly for installation, expect to be in "APT hell" in 3-6 months. If that doesn't happen, it is luck.

---

### Post by amanchesterman on 2018-07-22
I had a similar problem some months ago. I downloaded and installed the latest LibreOffice using the Software Centre (I have Xubuntu but I don't think that matters in this issue). What I didn't realise was that the version I installed was a 'snap' package (it's not obvious in the Software Centre unless you scroll down the screen and look at the source of the software).
When I tried to open a file I found, like the OP, that I was looking at the root folder and the familiar layout of folders was gone; I seem to remember the font in the dialogue box was different too, and there were various other things that felt unfamiliar.
I uninstalled it (again using the Software Centre) and then re-installed LibreOffice using Synaptic, and everything was back the way I remembered it.
This may be something for the OP to check?
Best wishes, John.

---

### Post by ajgreeny on 2018-07-22
If you're using the snap version i suggest you remove that with ```
sudo snap remove libreoffice
``` then enable the LO PPA repos, see [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) for all info about them, and finally install LO again in the usual way either with synaptic as mentioned in post #6 or using terminal with command ```
sudo apt install libreoffice
```
I have been using those PPA versions of LO for a very long time with no problems at all; they are very trustworthy, coming from the Ubuntu LO developers themselves, I believe.

---

### Post by edstevens on 2018-07-22
All, thanks for the replies.  In answer to the questions:

1) I don't recall exactly how I installed OL 6.  That was a little over a month ago and package installation/management under Ubuntu is still something I don't have a good grasp on.  Much more familiar with using 'yum' under RHEL/Oracle Linux on my database servers.  I do know that i did not specifically DE-install anything.  Clues may be found in a thread I had as a follow-up to that exercise, at [https://ubuntuforums.org/showthread.php?t=2394025](https://ubuntuforums.org/showthread.php?t=2394025)

2) As regards to feedback from command line 'libreoffice --version', it gives no response:
```
ed@ed-Gazelle-00:~$ libreoffice --version
ed@ed-Gazelle-00:~$ sudo libreoffice --version
[sudo] password for ed: 
ed@ed-Gazelle-00:~$ 

```

All in all, I'd guess that from some of the responses that my best course of action is to completely deinstall LO and re-install just the v6.  So what is the best way to do that, and what would I need to preserve some documents that appear to be under an LO directory:  /home/ed/snap/libreoffice/71/myfile.odt

---

### Post by ajgreeny on 2018-07-22
You obviously installed the snap version of LO according to the final line of your post #10 as that folder would not be in your home if you had installed LO in the normal manner.

No matter; that myfile.odt can be copied or moved to wherever you previously had all your documents from LO, probably /home/ed/Documents or similar.  It should not mastter which version of LO produced the files and they should easily open in the LO v6 from the PPA, which if you really want LO v6 is in my opinion the best way yo get it; much easier than downloading the archive from the LO site and installing the .deb files from that.

See my post #9 for the details of the PPA which has all info about how to enable it.

---

### Post by edstevens on 2018-07-22
Ajgreeny -

Tried that and now things are worse.  

First I tried to remove:

```
ed@ed-Gazelle-00:~$ sudo snap remove libreoffice
[sudo] password for ed: 
libreoffice removed
ed@ed-Gazelle-00:~$ 
```

At that point, I checked my "start" menu and the 'office' group still indicated the presence of the v5 apps, but the icons for the v6 were gone.

Pressing ahead:

```
ed@ed-Gazelle-00:~$ sudo add-apt-repository ppa:libreoffice/ppa
 LibreOffice test builds and backports

This PPA will have what the Document Foundation calls "LibreOffice fresh", the latest release of the newest series (but no alpha/beta releases).

There is a PPA dedicated to specific LibreOffice major series which support a range of older Ubuntu releases too:
https://launchpad.net/~libreoffice/+archive/libreoffice-6-0 ("Fresh")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-4 ("Still")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-3 (EOL)
https://launchpad.net/~libreoffice/+archive/libreoffice-5-1 (EOL)
 (testbed for 16.04 LTS SRUs, EOL upstream)
https://launchpad.net/~libreoffice/+archive/libreoffice-4-2 (EOL)
 (testbed for 14.04 LTS SRUs, EOL upstream)

<snip much verbiage>

Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmph4kz2kbh/secring.gpg' created
gpg: keyring `/tmp/tmph4kz2kbh/pubring.gpg' created
gpg: requesting key 1378B444 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmph4kz2kbh/trustdb.gpg: trustdb created
gpg: key 1378B444: public key "Launchpad PPA for LibreOffice Packaging" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ed@ed-Gazelle-00:~$ 
ed@ed-Gazelle-00:~$ sudo apt install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-stix icoutils kactivities kate-data katepart kde-l10n-engb kde-runtime
<snip lengthy list>
  scrollkeeper snap-confine sonnet-plugins sqlite3
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  fonts-crosextra-caladea fonts-crosextra-carlito fonts-liberation2
  fonts-linuxlibertine fonts-sil-gentium fonts-sil-gentium-basic
  libapache-pom-java libbsh-java libcommons-logging-java
  libcommons-parent-java libhsqldb1.8.0-java libpq5 libreoffice-base
  libreoffice-base-drivers libreoffice-java-common libreoffice-librelogo
  libreoffice-nlpsolver libreoffice-report-builder
  libreoffice-report-builder-bin libreoffice-script-provider-bsh
  libreoffice-script-provider-js libreoffice-script-provider-python
  libreoffice-sdbc-hsqldb libreoffice-sdbc-postgresql
  libreoffice-wiki-publisher libservlet3.1-java
Suggested packages:
  libavalon-framework-java libcommons-logging-java-doc
  libexcalibur-logkit-java liblog4j1.2-java java-virtual-machine
  libhsqldb1.8.0-java-gcj fonts-noto-hinted fonts-noto-mono gpa
  libreoffice-grammarcheck libreoffice-l10n myspell-dictionary
  openclipart2-libreoffice | openclipart-libreoffice pstoedit unixodbc
  libreoffice-officebean libjtds-java libreoffice-mysql-connector | libmyodbc
  | libmysql-java libsqliteodbc | tdsodbc | mdbtools postgresql mediawiki
The following NEW packages will be installed:
  fonts-crosextra-caladea fonts-crosextra-carlito fonts-liberation2
  fonts-linuxlibertine fonts-sil-gentium fonts-sil-gentium-basic
  libapache-pom-java libbsh-java libcommons-logging-java
  libcommons-parent-java libhsqldb1.8.0-java libpq5 libreoffice
  libreoffice-base libreoffice-base-drivers libreoffice-java-common
  libreoffice-librelogo libreoffice-nlpsolver libreoffice-report-builder
  libreoffice-report-builder-bin libreoffice-script-provider-bsh
  libreoffice-script-provider-js libreoffice-script-provider-python
  libreoffice-sdbc-hsqldb libreoffice-sdbc-postgresql
  libreoffice-wiki-publisher libservlet3.1-java
0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 MB of archives.
After this operation, 42.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 fonts-crosextra-caladea all 20130214-1 [82.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 fonts-crosextra-carlito all 20130920-1 [742 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 fonts-linuxlibertine all 5.3.0-2 [1,688 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 fonts-sil-gentium all 20081126:1.03-1 [247 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 fonts-sil-gentium-basic all 1.1-7 [379 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libapache-pom-java all 10-2build1 [4,022 B]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libbsh-java all 2.0b4-17ubuntu1 [264 kB]
Get:8 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 fonts-liberation2 all 2.00.1-5~16.04.1~lo4 [1,458 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libcommons-parent-java all 39-3 [9,380 B]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libcommons-logging-java all 1.2-1+build1 [59.5 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libservlet3.1-java all 8.0.32-1ubuntu1.6 [391 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libhsqldb1.8.0-java all 1.8.0.10+dfsg-6 [724 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpq5 amd64 9.5.13-0ubuntu0.16.04 [78.7 kB]
Get:14 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-base-drivers amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [498 kB]
Get:15 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-base amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [1,723 kB]
Get:16 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-report-builder-bin amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [795 kB]
Get:17 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [89.3 kB]
Get:18 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-java-common all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [1,838 kB]
Get:19 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-script-provider-python all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [12.3 kB]
Get:20 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-librelogo all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [186 kB]
Get:21 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-nlpsolver all 0.9+LibO6.0.5~rc2-0ubuntu0.16.04.1~lo1 [151 kB]
Get:22 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-report-builder all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [2,030 kB]
Get:23 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-script-provider-bsh all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [32.8 kB]
Get:24 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-script-provider-js all 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [614 kB]
Get:25 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-sdbc-hsqldb amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [108 kB]
Get:26 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-sdbc-postgresql amd64 1:6.0.5~rc2-0ubuntu0.16.04.1~lo1 [229 kB]
Get:27 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial/main amd64 libreoffice-wiki-publisher all 1.2.0+LibO6.0.5~rc2-0ubuntu0.16.04.1~lo1 [192 kB]
Fetched 14.6 MB in 2min 36s (93.7 kB/s)                                        
Selecting previously unselected package fonts-crosextra-caladea.
(Reading database ... 285020 files and directories currently installed.)
Preparing to unpack .../fonts-crosextra-caladea_20130214-1_all.deb ...

<snip lengthy verbiage>

Setting up libreoffice-wiki-publisher (1.2.0+LibO6.0.5~rc2-0ubuntu0.16.04.1~lo1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
ed@ed-Gazelle-00:~$ 
```


At this point, the 'start' button menu still only shows the icons for v5.  Clicking on them flashes the v6 splash, but nothing opens.  Double-clicking <filename>.odt in Nemo flashes the v6 splash, but nothing opens.  Right-click <filename>.odt and select "open with LibreOffice Writer" flashes the splash, but nothing opens.  Right click the file name and select 'open with' no longer gives an option for LO, but does have an option for 'other application'.   That, in turn, lists LibreOffice Writer as the default, but choosing it again results in the splash screen, but again no app actually opens.

So it would appear I still have bits of one and bits of the other and broken pointers.  But no idea how to clean it up.  I  am not opposed to completely eradicating LO (any version, any fragment) and reinstalling with a completely clean slate.

---

### Post by ajgreeny on 2018-07-23
Oh boy! You seem to have got in a bit of a mess largely from installing and using the snap package version of LO without first removing the repos version 5.

It appears that you have removed the snap version now, though I have zero experience of snaps so can't help much more with that.

However, having enabled the LO ppa, as you seem to have successfully done, you should have run the upgrade command ```
sudo apt update
sudo apt upgrade
``` commands, not the ```
sudo apt install libreoffice
```.

From the situation you are now in I suggest you do a full LO clear-out by running command ```
sudo apt remove libreoffice*
``` (the asterisk is important; do not remove it from command) which will remove all of the suite packages, followed by ```
sudo apt autoremove
``` to get rid of any dependencies, then finally run command ```
sudo apt install libreoffice
``` to fully install the PPA version.

---

### Post by edstevens on 2018-07-24
The 'remove','autoremove','install' sequence fixed it.  Thank you.

---

### Post by ajgreeny on 2018-07-26
[B]Great news! 
[/B]
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

