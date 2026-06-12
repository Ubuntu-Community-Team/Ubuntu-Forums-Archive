---
title: "Synaptic Search shows no results"
date: 2016-06-01
forum: General Help
---

### Post by mikodo on 2016-06-01
Hi,

Xubuntu 14.04.1 install. I don't know when this started happening or, if it has been like this since fresh install. I have been installing/removing/purging/etc with apt-get and pretty much know what I want to install so, I haven't used Synaptic to see what apps might be available to install.

I did install USC this install and only used it for installing debs. I don't have installed now.

Recently, I noticed I have no search functionality for Synaptic. Not the quick filter, which I have tended to regard as a bit flaky. I mean "Search". But when I try to search, I get no results, with the same poverty of results for apps/libraries I know are installed and ones I know are not.

I went into  Synaptic > Settings > Filters > Search Filter and ticked them for all in the field. I don't remember ever having to do this before but tried it, with no benefit.

My google-fu has not shown a solution yet. I have tried below with it not helping.

Any ideas?

```
mikodo@mikodo:~$ sudo apt-get install apt-xapian-index
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apt-xapian-index is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-85 linux-headers-3.13.0-85-generic
  linux-image-3.13.0-85-generic linux-image-extra-3.13.0-85-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mikodo@mikodo:~$ sudo update-apt-xapian-index -vf
Reading plugin /usr/share/apt-xapian-index/plugins/aliases.py.
Reading plugin /usr/share/apt-xapian-index/plugins/app-install.py.
Reading plugin /usr/share/apt-xapian-index/plugins/apttags.py.
Reading plugin /usr/share/apt-xapian-index/plugins/cataloged_time.py.
Reading plugin /usr/share/apt-xapian-index/plugins/debtags.py.
Reading plugin /usr/share/apt-xapian-index/plugins/descriptions.py.
Reading plugin /usr/share/apt-xapian-index/plugins/display_name.py.
Reading plugin /usr/share/apt-xapian-index/plugins/origin.py.
Reading plugin /usr/share/apt-xapian-index/plugins/relations.py.
Reading plugin /usr/share/apt-xapian-index/plugins/sections.py.
Reading plugin /usr/share/apt-xapian-index/plugins/sizes.py.
Reading plugin /usr/share/apt-xapian-index/plugins/software_center.py.
Reading plugin /usr/share/apt-xapian-index/plugins/template.py.
Reading plugin /usr/share/apt-xapian-index/plugins/translated-desc.py.
Most recent dataset:    Wed Jun  1 10:56:34 2016.
Most recent update for: Wed Jun  1 10:56:34 2016.
The index /var/lib/apt-xapian-index is up to date, but rebuilding anyway as requested.
Aggregating value information.
Initializing plugins.
Reading .desktop files from /usr/share/app-install/desktop/: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-updates_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_yannubuntu_booReading en translations from /var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_trusty_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-security_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/archive.canonical.com_ubuntu_disReading en translations from /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-updates_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_uReading en translations from /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_trusty-security_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_bit-team_stablReading en translations from /var/lib/apt/lists/ppa.launchpad.net_bit-team_stable_ubuntu_dists_trusty_main_i18n_Translation-en: done.  
Rebuilding Xapian index... 0% 
androidsdk-ddms:ddms.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
androidsdk-ddms:ddms.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
androidsdk-ddms:ddms.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
androidsdk-hierarchyviewer:hierarchyviewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
androidsdk-hierarchyviewer:hierarchyviewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
androidsdk-hierarchyviewer:hierarchyviewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 1% 
artikulate:kde4__artikulate.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
artikulate:kde4__artikulate.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
artikulate:kde4__artikulate.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 3% 
bossa:bossa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
bossa:bossa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
bossa:bossa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 3%
camitk-imp:camitk-imp.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
camitk-imp:camitk-imp.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
camitk-imp:camitk-imp.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 4%
checkbox-gui:checkbox-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
checkbox-gui:checkbox-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
checkbox-gui:checkbox-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 4%
colobot:colobot.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
colobot:colobot.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
colobot:colobot.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
core-network-gui:core-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
core-network-gui:core-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
core-network-gui:core-gui.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 6%
cyclograph-gtk2:cyclograph-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
cyclograph-gtk2:cyclograph-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
cyclograph-gtk2:cyclograph-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
cyclograph-qt4:cyclograph-qt.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
cyclograph-qt4:cyclograph-qt.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
cyclograph-qt4:cyclograph-qt.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 9% 
fcitx-qimpanel-configtool:fcitx-qimpanel-configtool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
fcitx-qimpanel-configtool:fcitx-qimpanel-configtool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
fcitx-qimpanel-configtool:fcitx-qimpanel-configtool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 16% 
gromit-mpx:gromit-mpx.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
gromit-mpx:gromit-mpx.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
gromit-mpx:gromit-mpx.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 18% 
hyperrogue:hyperrogue.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
hyperrogue:hyperrogue.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
hyperrogue:hyperrogue.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 18%
idle-python3.4:idle-python3.4.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
idle-python3.4:idle-python3.4.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
idle-python3.4:idle-python3.4.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 20% 
kde-developer-sdk:kde4__kde-developer-sdk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kde-developer-sdk:kde4__kde-developer-sdk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kde-developer-sdk:kde4__kde-developer-sdk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 20%
kritagemini:kde4__kritagemini.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kritagemini:kde4__kritagemini.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kritagemini:kde4__kritagemini.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kritasketch:kde4__kritasketch.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kritasketch:kde4__kritasketch.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
kritasketch:kde4__kritasketch.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 25% 
libcamitk3-dev:camitk-wizard.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
libcamitk3-dev:camitk-wizard.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
libcamitk3-dev:camitk-wizard.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 59% 
libunity-mir-tests:unity-mir-test-helper-app.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
libunity-mir-tests:unity-mir-test-helper-app.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
libunity-mir-tests:unity-mir-test-helper-app.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 63% 
light-locker-settings:light-locker-settings.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
light-locker-settings:light-locker-settings.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
light-locker-settings:light-locker-settings.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 68% 
ltrsift:ltrsift.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
ltrsift:ltrsift.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
ltrsift:ltrsift.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 69% 
mialmpick:mia-lmpick.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
mialmpick:mia-lmpick.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
mialmpick:mia-lmpick.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 72% 
noblenote:noblenote.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
noblenote:noblenote.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
noblenote:noblenote.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 72%
nrefactory-samples:nrefactory-demo-swf.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nrefactory-samples:nrefactory-demo-swf.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nrefactory-samples:nrefactory-demo-swf.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nrefactory-samples:nrefactory-demo-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nrefactory-samples:nrefactory-demo-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nrefactory-samples:nrefactory-demo-gtk.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 73%
nvpy:nvpy.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nvpy:nvpy.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
nvpy:nvpy.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 75% 
pixelmed-webstart-apps:DicomImageBlackout.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomImageBlackout.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomImageBlackout.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomImageViewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomImageViewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomImageViewer.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:WatchFolderAndSend.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:WatchFolderAndSend.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:WatchFolderAndSend.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:MediaImporter.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:MediaImporter.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:MediaImporter.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DoseUtility.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DoseUtility.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DoseUtility.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:ConvertAmicasJPEG2000FilesetToDicom.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:ConvertAmicasJPEG2000FilesetToDicom.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:ConvertAmicasJPEG2000FilesetToDicom.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomCleaner.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomCleaner.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pixelmed-webstart-apps:DicomCleaner.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 76%
plm:plm.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
plm:plm.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
plm:plm.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 77% 
postbooks-updater:postbooks-updater.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
postbooks-updater:postbooks-updater.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
postbooks-updater:postbooks-updater.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 78% 
pumpa:pumpa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pumpa:pumpa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pumpa:pumpa.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pycorrfit:pycorrfit.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pycorrfit:pycorrfit.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pycorrfit:pycorrfit.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pylang:pylang.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pylang:pylang.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
pylang:pylang.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 83% 
python3-windowmocker:window-mocker3.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
python3-windowmocker:window-mocker3.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
python3-windowmocker:window-mocker3.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 88% 
seahorse-adventures:seahorse-adventures.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
seahorse-adventures:seahorse-adventures.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
seahorse-adventures:seahorse-adventures.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 88% 
sonic-visualiser:sonic-visualiser.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
sonic-visualiser:sonic-visualiser.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
sonic-visualiser:sonic-visualiser.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 90% 
sugar-emulator-0.98:sugar-emulator.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
sugar-emulator-0.98:sugar-emulator.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
sugar-emulator-0.98:sugar-emulator.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 93% 
uhexen2:uhexen2.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
uhexen2:uhexen2.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
uhexen2:uhexen2.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 94% 
unity-scope-tool:unity-scope-tool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
unity-scope-tool:unity-scope-tool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
unity-scope-tool:unity-scope-tool.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 95% 
view3dscene:view3dscene.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
view3dscene:view3dscene.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
view3dscene:view3dscene.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 98% 
yi:yi-vim.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
yi:yi-vim.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
yi:yi-vim.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
yi:yi-emacs.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
yi:yi-emacs.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
yi:yi-emacs.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index... 99% 
zita-bls1:zita-bls1.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
zita-bls1:zita-bls1.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
zita-bls1:zita-bls1.desktop: parsing X-AppInstall-Popcon: invalid literal for int() with base 10: ''
Rebuilding Xapian index: done.  
Installing the new index.
Removing old index /var/cache/apt-xapian-index/index.1.
Writing value information to /var/lib/apt-xapian-index/values.
Writing prefix information to /var/lib/apt-xapian-index/prefixes.
Writing documentation to /var/lib/apt-xapian-index/README.
mikodo@mikodo:~$ 

```

---

### Post by QDR06VV9 on 2016-06-01
What dose this do after installing "apt-xapian-index" or reinstalling

```
sudo update-apt-xapian-index -vf
```

---

### Post by mikodo on 2016-06-01
> **runrickus said:**
> What dose this do after installing "apt-xapian-index" or reinstalling

```
sudo update-apt-xapian-index -vf
```

I apologize. Do you mean, do I have Synaptic Search now, or to run those commands again. Synaptic Search still does not work and when I run the commands again, I get the same results as before. Did I miss something?

---

### Post by QDR06VV9 on 2016-06-01
Nope.. badly worded on my part sorry.
Lets try this
```
sudo apt-get install --reinstall synaptic
sudo dpkg-reconfigure synaptic

```
Making sure synaptic is closed first of course:)

---

### Post by mc4man on 2016-06-01
Try resetting synaptic to default, (copy & paste so no unfortunate ..
```
sudo rm -rf /root/.synaptic
```

---

### Post by mikodo on 2016-06-01
Thank you, runrickus.

I ran those commands with Synaptic closed and, it had no effect on Synaptic Search results when I opened it and tried again.

---

### Post by mikodo on 2016-06-01
> **mc4man said:**
> Try resetting synaptic to default
```
sudo rm -rf /root/.synaptic
```

That worked! Was it not default possibly as I had installed USC earlier?

---

### Post by QDR06VV9 on 2016-06-01
> **mc4man said:**
> Try resetting synaptic to default
```
sudo rm -rf /root/.synaptic
```
+1

I just built a VB and just ran these two commands
```
sudo apt-get install apt-xapian-index
sudo update-apt-xapian-index -vf

```
And here are the results before and after.
Follow mc4mans advice.
EDIT I see now SUCCESS! Nice!

---

### Post by mc4man on 2016-06-01
> **mikodo said:**
> That worked! Was it not default possibly as I had installed USC earlier?It's possible you messed up the filters or Search > "Look in"  setting. This was a bit of a sledge hammer fix but seemed no reason to beat around the bush in this case
(- the big downside to a blanket resetting is you lose your history...

---

### Post by mikodo on 2016-06-01
Yes! Thanks for the trouble of trying it for me in a vm.

Thank you, mc4man.

I wonder if Synaptic will need to be reset for default again on fresh installs?

Edit: Oh, just saw your earlier response on "look in setting". I will

Edit1: Seems, I have the same settings in Settings as before but, there are a lot and, I cannot be sure. That's okay for losing history. I was not that involved with it really anyway.

---

### Post by mc4man on 2016-06-01
Just so you're clear - by 'default' I meant set synaptic back to the _default settings of synaptic,_ not setting synaptic as the default whatever.
The look in is by default set to Name and Description, the other choices are very specific & only of use in certain situations.

---

### Post by mikodo on 2016-06-01
I had to look where "Description and Name" was. I found it:

Search > below "look in", > and had the choices:

Name
Description and Name
Maintainer
Version
Dependencies
Provided packages

I am a little shamed faced to have bothered you all. I don't recall ever seeing those options before but, I must have been playing with them at sometime as no doubt that was my problem.

Now, I am going to play with them, to see what it can show me. So, all is not in vain. I will learn something here.

Addendum: After playing with the different settings, I must have set it for "Version" as, I get nothing reported on the same searches I had tried before with no results. With all the others, like Dependencies et al, there are descriptions offered.

Thanks, again!

---

### Post by uRock on 2016-06-01
This made my life better! Thank you!

---

### Post by vasa1 on 2016-06-01
What was the reasoning behind ```
sudo apt-get install apt-xapian-index ? 
```

I use Lubuntu which, in 14.04 and 16.04 (and probably even in earlier versions), comes with Synaptic but doesn't have **apt-xapian-index** installed by default. I don't particularly miss apt-xapian-index because I don't have a powerful laptop.

The search box in Synaptic seems to work just fine in Lubuntu 16.04.

---

### Post by mc4man on 2016-06-01
> **vasa1 said:**
> What was the reasoning behind ```
sudo apt-get install apt-xapian-index ? 
```

I use Lubuntu which, in 14.04 and 16.04 (and probably even in earlier versions), comes with Synaptic but doesn't have **apt-xapian-index** installed by default. I don't particularly miss apt-xapian-index because I don't have a powerful laptop.

The search box in Synaptic seems to work just fine in Lubuntu 16.04.

If apt-xapian-index is installed then synaptic gets that additional quick filter search box, without it being installed then just the normal search via the search icon.
apt-xapian-index was included in  Ubuntu's image because of Software-center, now that it's gone it's no longer on the image.
Some users like the quick filter search, some don't,   myself  I'm leaving it gone.

---

### Post by vasa1 on 2016-06-01
> **mc4man said:**
> If apt-xapian-index is installed then synaptic gets that additional quick filter search box, without it being installed then just the normal search via the search icon.
apt-xapian-index was included in  Ubuntu's image because of Software-center, now that it's gone it's no longer on the image.
Some users like the quick filter search, some don't,   myself  I'm leaving it gone.Thanks for the explanation. I also read that having apt-xapian-index around can lead to its database growing and growing. I don't how far that's true.

---

### Post by mikodo on 2016-06-02
Thanks folks. I just looked into this thread again and saw your posts.
> **mc4man said:**
> If apt-xapian-index is installed then synaptic gets that additional quick filter search box, without it being installed then just the normal search via the search icon.
apt-xapian-index was included in  Ubuntu's image because of Software-center, now that it's gone it's no longer on the image.
Some users like the quick filter search, some don't,   myself  I'm leaving it gone.

> **vasa1 said:**
> Thanks for the explanation. I also read that having apt-xapian-index around can lead to its database growing and growing. I don't how far that's true.

I tried Synaptic's quick filter search with a couple of larger things. Gnome and then KDE. It was very fast in reporting both. Then:

```
mikodo@mikodo:~$ sudo apt-get purge apt-xapian-index
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-85 linux-headers-3.13.0-85-generic
  linux-image-3.13.0-85-generic linux-image-extra-3.13.0-85-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apt-xapian-index*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
**After this operation, 336 kB disk space will be freed**.
Do you want to continue? [Y/n] y                      
(Reading database ... 215572 files and directories currently installed.)
Removing apt-xapian-index (0.45ubuntu4) ...
Removing index /var/lib/apt-xapian-index...
Purging configuration files for apt-xapian-index (0.45ubuntu4) ...
Removing index /var/lib/apt-xapian-index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
mikodo@mikodo:~$

```

And then, the quick search feature was gone when I opened Synaptic. I tried the regular way I would search with the Search button and it might have taken between 1-2 seconds longer to provide the same information as quick search. I'll leave it uninstalled.

---

