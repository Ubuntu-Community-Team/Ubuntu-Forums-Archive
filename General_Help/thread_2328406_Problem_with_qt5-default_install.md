---
title: "Problem with qt5-default install"
date: 2016-06-20
forum: General Help
---

### Post by gage4 on 2016-06-20
Hi this is my first time posting to this forum i hope this thread is in the right section.

I was trying to install dependencies for ckb ([https://github.com/ccMSC/ckb](https://github.com/ccMSC/ckb))

and everything was going smoothly until i had to install qt5 while attempting to install it via apt this was the output


```
_gh0st@~ > sudo apt-get install qt5-defaultReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libandroid-properties1 libhud2 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libqt5feedback5 libqt5organizer5 libqt5positioning5
  libqt5quicktest5 libubuntugestures5 libubuntutoolkit5 libunity-action-qt1
  libx86-1 plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy pm-utils pyotherside python3-checkbox-support
  python3-guacamole python3-jinja2 python3-padme python3-plainbox
  python3-pyparsing python3-xlsxwriter qml-module-io-thp-pyotherside
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtfeedback qml-module-qtquick-layouts qml-module-qtquick-window2
  qml-module-ubuntu-layouts qml-module-ubuntu-performancemetrics qmlscene
  qtdeclarative5-dev-tools qtdeclarative5-unity-action-plugin suru-icon-theme
  ubuntu-mobile-icons ubuntu-ui-toolkit-theme vbetool
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libegl1-mesa-dev libgles2-mesa-dev libmirclient-dev libmircommon-dev
  libmircookie-dev libmircookie2 libprotobuf-dev libqt5concurrent5
  libqt5gui5-gles libqt5opengl5-gles libqt5opengl5-gles-dev libqt5quick5-gles
  libwayland-dev libxkbcommon-dev qt5-qmake-gles qtbase5-gles-dev
Suggested packages:
  libqt5libqgtk2 libmysqlclient-dev libpq-dev libsqlite3-dev unixodbc-dev
The following packages will be REMOVED:
  checkbox-converged checkbox-gui libqt5gui5 libqt5opengl5 libqt5quick5
  libunity-webapps0 qml-module-qtgraphicaleffects qml-module-qtquick2
  qml-module-qttest qml-module-ubuntu-components
  qml-module-ubuntu-onlineaccounts qml-module-ubuntu-test
  qml-module-ubuntu-web qt5-qmake qtdeclarative5-accounts-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin ubuntu-desktop unity-tweak-tool
  unity-webapps-common unity-webapps-qml unity-webapps-service
  webapp-container webbrowser-app wireshark wireshark-qt
The following NEW packages will be installed:
  libegl1-mesa-dev libgles2-mesa-dev libmirclient-dev libmircommon-dev
  libmircookie-dev libmircookie2 libprotobuf-dev libqt5concurrent5
  libqt5gui5-gles libqt5opengl5-gles libqt5opengl5-gles-dev libqt5quick5-gles
  libwayland-dev libxkbcommon-dev qt5-default qt5-qmake-gles qtbase5-gles-dev
0 upgraded, 17 newly installed, 27 to remove and 0 not upgraded.
Need to get 6,512 kB of archives.
After this operation, 2,595 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

Instead of just installing qt5 and its dependencies it also wants to remove ubuntu-desktop along with what i assume are relatively important packages.

I have searched for a possible reason for this but have come up with nothing specific any help at all would be great.

---

### Post by mc4man on 2016-06-20
A few things stand out which you may know why or may have to figure out why. (plus note which Ubuntu release you're using, figure it's not 14.04
1st. -  there is that group of autoremove  packages, what did you do to create that? (could be behind the below..
2nd - many of the packages to be installed are the gles versions, that's not typical & likely behind all the packages being removed. You can see that you had qt5-qmake already installed, now it's being replaces by qt5-qmake-gles, there's an add. 5 qt5 gles packages being installed, normally the non gles one's would be.

---

### Post by gage4 on 2016-06-20
That group of autoremove packages i cannot remove simply with 
```
sudo apt-get autoremove
```

this is the output

```
_gh0st@~ > sudo apt-get autoremove[sudo] password for gh0st: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

not sure if i can remove them

---

### Post by &amp;KyT$0P# on 2016-06-20
> **gage4 said:**
> That group of autoremove packages i cannot remove simply with 
```
sudo apt-get autoremove
```

this is the output

```
_gh0st@~ > sudo apt-get autoremove[sudo] password for gh0st: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

not sure if i can remove them
I think this means those packages are not auto-removable now, but *would be* auto-removable after running [FONT=Courier New]sudo apt-get install qt5-default[/FONT]

---

