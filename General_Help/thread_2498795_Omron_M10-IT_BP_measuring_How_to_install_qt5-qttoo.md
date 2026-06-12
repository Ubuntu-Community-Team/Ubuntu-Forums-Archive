---
title: "Omron M10-IT BP measuring: How to install qt5-qttools?"
date: 2024-06-27
forum: General Help
---

### Post by makem2 on 2024-06-27
[COLOR=#000000]I have an Omron M10-IT health monitoring machine and would rather not use Windows to install the Omron Blood Pressure Manager.[/COLOR]

[COLOR=#000000]I have followed the instructions at this url and used the AI generated help as this seemed better than other suggestions (Except for the snap option below but that also ended up at a dead end for me.)

[https://search.brave.com/search?q=ubuntu+installing+Omron+Blood+Pressure+Manager&source=desktop](https://search.brave.com/search?q=ubuntu+installing+Omron+Blood+Pressure+Manager&source=desktop)[/COLOR]

[COLOR=#000000]Can anyone assist in installing qt5-qttools please?[/COLOR]

[COLOR=#000000]The below is how far I get when I find that qt5-default appears to have changed name in Noble Ubuntu. I can only find help for AMD machines and mine is Intel i386.[/COLOR]

[COLOR=#000000]I believe this is the new name: [/COLOR]qt5-assistant/noble 5.15.13-1 i386[COLOR=#000000]

From the list below but I am loath to try any further. I am not confident I could carry on with the install and make.

```

[/COLOR]makem@makem-22:~$ cat /proc/cpuinfo  | grep 'name'| uniq
model name	: 11th Gen Intel(R) Core(TM) i7-11700K @ 3.60GHz
makem@makem-22:~$
[COLOR=#000000]
```

```

[/COLOR]makem@makem-22:~$ sudo apt install git
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb git-cvs
  git-mediawiki git-svn
The following NEW packages will be installed
  git git-man liberror-perl
0 to upgrade, 3 to newly install, 0 to remove and 55 not to upgrade.
Need to get 4,804 kB of archives.
After this operation, 24.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu noble/main amd64 liberror-perl all 0.17029-2 [25.6 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu noble-updates/main amd64 git-man all 1:2.43.0-1ubuntu7.1 [1,100 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu noble-updates/main amd64 git amd64 1:2.43.0-1ubuntu7.1 [3,679 kB]
Fetched 4,804 kB in 1s (8,064 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 225028 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17029-2_all.deb ...
Unpacking liberror-perl (0.17029-2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.43.0-1ubuntu7.1_all.deb ...
Unpacking git-man (1:2.43.0-1ubuntu7.1) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.43.0-1ubuntu7.1_amd64.deb ...
Unpacking git (1:2.43.0-1ubuntu7.1) ...
Setting up liberror-perl (0.17029-2) ...
Setting up git-man (1:2.43.0-1ubuntu7.1) ...
Setting up git (1:2.43.0-1ubuntu7.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
makem@makem-22:~$

```

```

makem@makem-22:~$ git clone https://github.com/LazyT/obpm.git
Cloning into 'obpm'...
remote: Enumerating objects: 1028, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 1028 (delta 1), reused 0 (delta 0), pack-reused 1017
Receiving objects: 100% (1028/1028), 70.25 MiB | 16.07 MiB/s, done.
Resolving deltas: 100% (436/436), done.
makem@makem-22:~$

[COLOR=#000000]
```

```

[/COLOR]makem@makem-22:~$ cd obpm[COLOR=#000000]
[/COLOR]makem@makem-22:~/obpm$ sudo apt-get install qt5-default qt5-qttools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package qt5-default is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'qt5-default' has no installation candidate
E: Unable to locate package qt5-qttools
makem@makem-22:~/obpm$
[COLOR=#000000]
```

```
[/COLOR]makem@makem-22:~/obpm$ apt list | grep qt5


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


cyclograph-qt5/noble,noble 1.9.1-1.2 all
dde-qt5integration/noble 5.5.23-1build9 amd64
fcitx-frontend-qt5/noble 1.2.7-2build13 amd64
fcitx5-frontend-qt5/noble 5.1.4-1build5 amd64
gambas3-gb-qt5-ext/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5-opengl/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5-wayland/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5-webkit/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5-webview/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5-x11/noble 3.19.0-2ubuntu10 amd64
gambas3-gb-qt5/noble 3.19.0-2ubuntu10 amd64
gcin-qt5-immodule/noble 2.9.0+dfsg1-3build1 amd64
gimagereader-qt5/noble 3.4.2-2build6 amd64
gstreamer1.0-qt5/noble 1.24.2-1ubuntu1 amd64
gstreamer1.0-qt5/noble 1.24.2-1ubuntu1 i386
hime-qt5-immodule/noble 0.9.11+dfsg-4build6 amd64
kde-style-oxygen-qt5/noble 4:5.27.11-0ubuntu2 amd64
kde-style-qtcurve-qt5/noble 1.9-7build16 amd64
lazarus-ide-qt5-3.0/noble 3.0+dfsg1-8build3 amd64
lazarus-ide-qt5/noble,noble 3.0+dfsg1-8build3 all
lazpaint-qt5/noble 7.2.2.1-1build2 amd64
lcl-qt5-3.0/noble 3.0+dfsg1-8build3 amd64
lcl-qt5/noble 3.0+dfsg1-8build3 amd64
libaccounts-qt5-1/noble 1.16-2build4 amd64
libaccounts-qt5-dev/noble 1.16-2build4 amd64
libappstreamqt5-3/noble 1.0.2-1build6 amd64
libappstreamqt5-dev/noble 1.0.2-1build6 amd64
libcgal-qt5-dev/noble 5.6-1build3 amd64
libdbusextended-qt5-1/noble 0.0.3-6build2 amd64
libdbusextended-qt5-dev/noble 0.0.3-6build2 amd64
libdbusmenu-qt5-2/noble,now 0.9.3+16.04.20160218-2build3 amd64 [installed,automatic]
libdbusmenu-qt5-dev/noble 0.9.3+16.04.20160218-2build3 amd64
libdbusmenu-qt5-doc/noble,noble 0.9.3+16.04.20160218-2build3 all
libdee-qt5-3/noble 3.3+14.04.20140317-0ubuntu8 amd64
libdee-qt5-dev/noble 3.3+14.04.20140317-0ubuntu8 amd64
libfcitx-qt5-1/noble 1.2.7-2build13 amd64
libfcitx-qt5-data/noble,noble 1.2.7-2build13 all
libfcitx-qt5-dev/noble 1.2.7-2build13 amd64
libgwengui-qt5-79t64/noble,now 5.10.2-2.1build4 amd64 [installed,automatic]
libgwengui-qt5-dev/noble 5.10.2-2.1build4 amd64
libjreen-qt5-1/noble 1.2.0+ds-2build3 amd64
libjreen-qt5-dev/noble 1.2.0+ds-2build3 amd64
liblightdm-qt5-3-0/noble 1.30.0-0ubuntu14 amd64
liblightdm-qt5-3-dev/noble 1.30.0-0ubuntu14 amd64
libmarblewidget-qt5-28/noble 4:23.08.5-0ubuntu3 amd64
libmgl-qt5-8t64/noble 8.0.1-7.1build1 amd64
libmpris-qt5-1/noble 1.0.6-2build2 amd64
libmpris-qt5-dev/noble 1.0.6-2build2 amd64
libmygpo-qt5-1/noble 1.1.0-4.1build3 amd64
libpackagekitqt5-1/noble 1.1.1-1build3 amd64
libpackagekitqt5-dev/noble 1.1.1-1build3 amd64
libphonon4qt5-4t64/noble 4:4.12.0-3.1build3 amd64
libphonon4qt5-data/noble,noble 4:4.12.0-3.1build3 all
libphonon4qt5-dev/noble 4:4.12.0-3.1build3 amd64
libphonon4qt5experimental-dev/noble 4:4.12.0-3.1build3 amd64
libphonon4qt5experimental4t64/noble 4:4.12.0-3.1build3 amd64
libpolkit-qt5-1-1/noble,now 0.200.0-1build4 amd64 [installed,automatic]
libpolkit-qt5-1-dev/noble 0.200.0-1build4 amd64
libpoppler-qt5-1t64/noble 24.02.0-1ubuntu9 amd64
libpoppler-qt5-1t64/noble 24.02.0-1ubuntu9 i386
libpoppler-qt5-dev/noble 24.02.0-1ubuntu9 amd64
libpoppler-qt5-dev/noble 24.02.0-1ubuntu9 i386
libportal-qt5-1/noble 0.7.1-5build5 amd64
libportal-qt5-dev/noble 0.7.1-5build5 amd64
libportal-tests-qt5/noble 0.7.1-5build5 amd64
libqaccessibilityclient-qt5-0/noble 0.6.0-1build2 amd64
libqaccessibilityclient-qt5-dev/noble 0.6.0-1build2 amd64
libqca-qt5-2-dev/noble 2.3.8-1build3 amd64
libqca-qt5-2-plugins/noble,now 2.3.8-1build3 amd64 [installed,automatic]
libqca-qt5-2/noble,now 2.3.8-1build3 amd64 [installed,automatic]
libqglviewer-dev-qt5/noble 2.8.0+dfsg1-2.1build4 amd64
libqglviewer2-qt5t64/noble 2.8.0+dfsg1-2.1build4 amd64
libqjdns-qt5-2t64/noble 2.0.3-3.1build3 amd64
libqjdns-qt5-dev/noble 2.0.3-3.1build3 amd64
libqofono-qt5-0/noble 0.122-2 amd64
libqscintilla2-qt5-15/noble 2.14.1+dfsg-1build3 amd64
libqscintilla2-qt5-designer/noble 2.14.1+dfsg-1build3 amd64
libqscintilla2-qt5-dev/noble 2.14.1+dfsg-1build3 amd64
libqscintilla2-qt5-l10n/noble,noble 2.14.1+dfsg-1build3 all
libqt5-ukui-style-dev/noble 1.0.8-1ubuntu3 amd64
libqt5-ukui-style1/noble 1.0.8-1ubuntu3 amd64
libqt53danimation5/noble 5.15.13+dfsg-1 amd64
libqt53dcore5/noble 5.15.13+dfsg-1 amd64
libqt53dextras5/noble 5.15.13+dfsg-1 amd64
libqt53dinput5/noble 5.15.13+dfsg-1 amd64
libqt53dlogic5/noble 5.15.13+dfsg-1 amd64
libqt53dquick5/noble 5.15.13+dfsg-1 amd64
libqt53dquickanimation5/noble 5.15.13+dfsg-1 amd64
libqt53dquickextras5/noble 5.15.13+dfsg-1 amd64
libqt53dquickinput5/noble 5.15.13+dfsg-1 amd64
libqt53dquickrender5/noble 5.15.13+dfsg-1 amd64
libqt53dquickscene2d5/noble 5.15.13+dfsg-1 amd64
libqt53drender5/noble 5.15.13+dfsg-1 amd64
libqt5bluetooth5-bin/noble 5.15.13-1 amd64
libqt5bluetooth5-bin/noble 5.15.13-1 i386
libqt5bluetooth5/noble 5.15.13-1 amd64
libqt5bluetooth5/noble 5.15.13-1 i386
libqt5charts5-dev/noble 5.15.13-1 amd64
libqt5charts5/noble 5.15.13-1 amd64
libqt5concurrent5t64/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5concurrent5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5contacts5a/noble 5.0~git20201102.f9a8f0fc+dfsg1-3build6 amd64
libqt5core5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5core5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5datavisualization5-dev/noble 5.15.13-1 amd64
libqt5datavisualization5/noble 5.15.13-1 amd64
libqt5dbus5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5dbus5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5designer5/noble 5.15.13-1 amd64
libqt5designer5/noble 5.15.13-1 i386
libqt5designercomponents5/noble 5.15.13-1 amd64
libqt5designercomponents5/noble 5.15.13-1 i386
libqt5feedback5-hfd/noble 0.2.2-1build3 amd64
libqt5feedback5/noble 5.0~git20180903.a14bd0b-6build1 amd64
libqt5gamepad5-dev/noble 5.15.13-1 amd64
libqt5gamepad5/noble 5.15.13-1 amd64
libqt5glib-2.0-0/noble 1.2.0-5.2build4 amd64
libqt5gstreamer-1.0-0/noble 1.2.0-5.2build4 amd64
libqt5gstreamer-dev/noble 1.2.0-5.2build4 amd64
libqt5gstreamerquick-1.0-0/noble 1.2.0-5.2build4 amd64
libqt5gstreamerui-1.0-0/noble 1.2.0-5.2build4 amd64
libqt5gstreamerutils-1.0-0/noble 1.2.0-5.2build4 amd64
libqt5gui5-gles/noble 5.15.13+dfsg-1 amd64
libqt5gui5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5gui5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5help5/noble 5.15.13-1 amd64
libqt5help5/noble 5.15.13-1 i386
libqt5hunspellinputmethod5/noble 5.15.13+dfsg-1 amd64
libqt5keychain1/noble 0.14.2-1build5 amd64
libqt5location5-plugin-mapboxgl/noble 5.15.13+dfsg-1 amd64
libqt5location5-plugin-mapboxgl/noble 5.15.13+dfsg-1 i386
libqt5location5-plugins/noble 5.15.13+dfsg-1 amd64
libqt5location5-plugins/noble 5.15.13+dfsg-1 i386
libqt5location5/noble 5.15.13+dfsg-1 amd64
libqt5location5/noble 5.15.13+dfsg-1 i386
libqt5multimedia5-plugins/noble 5.15.13-1 amd64
libqt5multimedia5-plugins/noble 5.15.13-1 i386
libqt5multimedia5/noble 5.15.13-1 amd64
libqt5multimedia5/noble 5.15.13-1 i386
libqt5multimediagsttools5/noble 5.15.13-1 amd64
libqt5multimediagsttools5/noble 5.15.13-1 i386
libqt5multimediaquick5/noble 5.15.13-1 amd64
libqt5multimediaquick5/noble 5.15.13-1 i386
libqt5multimediawidgets5/noble 5.15.13-1 amd64
libqt5multimediawidgets5/noble 5.15.13-1 i386
libqt5network5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5network5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5networkauth5-dev/noble 5.15.13-1 amd64
libqt5networkauth5/noble 5.15.13-1 amd64
libqt5nfc5/noble 5.15.13-1 amd64
libqt5nfc5/noble 5.15.13-1 i386
libqt5opengl5-dev/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5opengl5-dev/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5opengl5t64/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5opengl5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5organizer5a/noble 5.0~git20201102.f9a8f0fc+dfsg1-3build6 amd64
libqt5pas-dev/noble 3.0+dfsg1-1build3 amd64
libqt5pas1/noble 3.0+dfsg1-1build3 amd64
libqt5pdf5/noble 5.15.16+dfsg-3 amd64
libqt5pdfwidgets5/noble 5.15.16+dfsg-3 amd64
libqt5positioning5-plugins/noble 5.15.13+dfsg-1 amd64
libqt5positioning5-plugins/noble 5.15.13+dfsg-1 i386
libqt5positioning5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5positioning5/noble 5.15.13+dfsg-1 i386
libqt5positioningquick5/noble 5.15.13+dfsg-1 amd64
libqt5positioningquick5/noble 5.15.13+dfsg-1 i386
libqt5printsupport5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5printsupport5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5publishsubscribe5/noble 5.0~git20230712.81e08ee+dfsg-1build3 amd64
libqt5qml5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5qml5/noble 5.15.13+dfsg-1 i386
libqt5qmlmodels5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5qmlmodels5/noble 5.15.13+dfsg-1 i386
libqt5qmlworkerscript5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5qmlworkerscript5/noble 5.15.13+dfsg-1 i386
libqt5quick5-gles/noble 5.15.13+dfsg-2 amd64
libqt5quick5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5quick5/noble 5.15.13+dfsg-1 i386
libqt5quickcontrols2-5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5quickparticles5-gles/noble 5.15.13+dfsg-2 amd64
libqt5quickparticles5/noble 5.15.13+dfsg-1 amd64
libqt5quickparticles5/noble 5.15.13+dfsg-1 i386
libqt5quickshapes5/noble 5.15.13+dfsg-1 amd64
libqt5quickshapes5/noble 5.15.13+dfsg-1 i386
libqt5quicktemplates2-5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5quicktest5/noble 5.15.13+dfsg-1 amd64
libqt5quicktest5/noble 5.15.13+dfsg-1 i386
libqt5quickwidgets5/noble,now 5.15.13+dfsg-1 amd64 [installed,automatic]
libqt5quickwidgets5/noble 5.15.13+dfsg-1 i386
libqt5qxlsx-dev/noble 1.4.4-1.1build4 amd64
libqt5qxlsx0t64/noble 1.4.4-1.1build4 amd64
libqt5remoteobjects5-bin/noble 5.15.13-1 amd64
libqt5remoteobjects5-bin/noble 5.15.13-1 i386
libqt5remoteobjects5-dev/noble 5.15.13-1 amd64
libqt5remoteobjects5-dev/noble 5.15.13-1 i386
libqt5remoteobjects5/noble 5.15.13-1 amd64
libqt5remoteobjects5/noble 5.15.13-1 i386
libqt5script5/noble 5.15.13+dfsg-1 amd64
libqt5scripttools5/noble 5.15.13+dfsg-1 amd64
libqt5scxml5-bin/noble 5.15.13-1 amd64
libqt5scxml5-dev/noble 5.15.13-1 amd64
libqt5scxml5-private-dev/noble 5.15.13-1 amd64
libqt5scxml5/noble 5.15.13-1 amd64
libqt5sensors5-dev/noble 5.15.13-1 amd64
libqt5sensors5-dev/noble 5.15.13-1 i386
libqt5sensors5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5sensors5/noble 5.15.13-1 i386
libqt5serialbus5-bin/noble 5.15.13-1 amd64
libqt5serialbus5-dev/noble 5.15.13-1 amd64
libqt5serialbus5-plugins/noble 5.15.13-1 amd64
libqt5serialbus5/noble 5.15.13-1 amd64
libqt5serialport5-dev/noble 5.15.13-1 amd64
libqt5serialport5-dev/noble 5.15.13-1 i386
libqt5serialport5/noble 5.15.13-1 amd64
libqt5serialport5/noble 5.15.13-1 i386
libqt5serviceframework5/noble 5.0~git20230712.81e08ee+dfsg-1build3 amd64
libqt5sql5-ibase/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5sql5-ibase/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5-mysql/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5sql5-mysql/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5-odbc/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5sql5-odbc/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5-psql/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5sql5-psql/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5-sqlite/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5sql5-sqlite/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5-tds/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5sql5-tds/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5sql5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5sql5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5svg5-dev/noble 5.15.13-1 amd64
libqt5svg5-dev/noble 5.15.13-1 i386
libqt5svg5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5svg5/noble 5.15.13-1 i386
libqt5systeminfo5/noble 5.0~git20230712.81e08ee+dfsg-1build3 amd64
libqt5test5t64/noble 5.15.13+dfsg-1ubuntu1 amd64
libqt5test5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5texttospeech5-dev/noble 5.15.13-1 amd64
libqt5texttospeech5-dev/noble 5.15.13-1 i386
libqt5texttospeech5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5texttospeech5/noble 5.15.13-1 i386
libqt5versit5a/noble 5.0~git20201102.f9a8f0fc+dfsg1-3build6 amd64
libqt5versitorganizer5a/noble 5.0~git20201102.f9a8f0fc+dfsg1-3build6 amd64
libqt5virtualkeyboard5-dev/noble 5.15.13+dfsg-1 amd64
libqt5virtualkeyboard5/noble 5.15.13+dfsg-1 amd64
libqt5waylandclient5-dev/noble 5.15.13-1 amd64
libqt5waylandclient5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5waylandcompositor5-dev/noble 5.15.13-1 amd64
libqt5waylandcompositor5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5webchannel5-dev/noble 5.15.13-1 amd64
libqt5webchannel5-dev/noble 5.15.13-1 i386
libqt5webchannel5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5webchannel5/noble 5.15.13-1 i386
libqt5webengine-data/noble,noble 5.15.16+dfsg-3 all
libqt5webengine5/noble 5.15.16+dfsg-3 amd64
libqt5webenginecore5/noble 5.15.16+dfsg-3 amd64
libqt5webenginewidgets5/noble 5.15.16+dfsg-3 amd64
libqt5webkit5-dev/noble 5.212.0~alpha4-36 amd64
libqt5webkit5-dev/noble 5.212.0~alpha4-36 i386
libqt5webkit5/noble,now 5.212.0~alpha4-36 amd64 [installed,automatic]
libqt5webkit5/noble 5.212.0~alpha4-36 i386
libqt5websockets5-dev/noble 5.15.13-1 amd64
libqt5websockets5-dev/noble 5.15.13-1 i386
libqt5websockets5/noble 5.15.13-1 amd64
libqt5websockets5/noble 5.15.13-1 i386
libqt5webview5-dev/noble 5.15.13-1 amd64
libqt5webview5/noble 5.15.13-1 amd64
libqt5widgets5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5widgets5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5x11extras5-dev/noble 5.15.13-1 amd64
libqt5x11extras5-dev/noble 5.15.13-1 i386
libqt5x11extras5/noble,now 5.15.13-1 amd64 [installed,automatic]
libqt5x11extras5/noble 5.15.13-1 i386
libqt5xdg-dev/noble 3.12.0-0ubuntu6 amd64
libqt5xdg3/noble 3.12.0-0ubuntu6 amd64
libqt5xdgiconloader-dev/noble 3.12.0-0ubuntu6 amd64
libqt5xdgiconloader3/noble 3.12.0-0ubuntu6 amd64
libqt5xml5t64/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
libqt5xml5t64/noble 5.15.13+dfsg-1ubuntu1 i386
libqt5xmlpatterns5-dev/noble 5.15.13-1 amd64
libqt5xmlpatterns5-dev/noble 5.15.13-1 i386
libqt5xmlpatterns5/noble 5.15.13-1 amd64
libqt5xmlpatterns5/noble 5.15.13-1 i386
libqtspell-qt5-1/noble 1.0.1-2build2 amd64
libqtspell-qt5-data/noble,noble 1.0.1-2build2 all
libqtspell-qt5-dev/noble 1.0.1-2build2 amd64
libqtspell-qt5-html/noble,noble 1.0.1-2build2 all
libquazip1-qt5-1t64/noble 1.4-1.1build3 amd64
libquazip1-qt5-dev/noble 1.4-1.1build3 amd64
libquazip1-qt5-doc/noble,noble 1.4-1.1build3 all
libqwt-qt5-6/noble 6.1.4-2build2 amd64
libqwt-qt5-dev/noble 6.1.4-2build2 amd64
libqwtmathml-qt5-6/noble 6.1.4-2build2 amd64
libqwtmathml-qt5-dev/noble 6.1.4-2build2 amd64
libqwtplot3d-qt5-0/noble 0.2.7+svn191+gcc7-3ubuntu2 amd64
libqwtplot3d-qt5-dev/noble 0.2.7+svn191+gcc7-3ubuntu2 amd64
libqxmppomemoqt5-4t64/noble 1.5.5-0.4build4 amd64
libqxmppqt5-4t64/noble 1.5.5-0.4build4 amd64
libqxmppqt5-dev/noble 1.5.5-0.4build4 amd64
libreoffice-qt5/noble-updates 4:24.2.4-0ubuntu0.24.04.1 amd64
libsignon-qt5-1/noble 8.61-1ubuntu5 amd64
libsignon-qt5-dev/noble 8.61-1ubuntu5 amd64
libsoqt520-dev/noble 1.6.0+ds1-3.1build4 amd64
libsoqt520t64/noble 1.6.0+ds1-3.1build4 amd64
libsysstat-qt5-0-dev/noble 0.4.6-2ubuntu3 amd64
libsysstat-qt5-0/noble 0.4.6-2ubuntu3 amd64
libtelepathy-logger-qt5/noble 17.09.0-1build4 amd64
libtelepathy-qt5-0/noble 0.9.8+ds-4build4 amd64
libtelepathy-qt5-dev/noble 0.9.8+ds-4build4 amd64
libtelepathy-qt5-farstream0/noble 0.9.8+ds-4build4 amd64
libu1db-qt5-3/noble 0.1.7-1build2 amd64
libu1db-qt5-dev/noble 0.1.7-1build2 amd64
libu1db-qt5-doc/noble,noble 0.1.7-1build2 all
libu1db-qt5-examples/noble,noble 0.1.7-1build2 all
libudisks2-qt5-0/noble 5.0.6-1build2 amd64
libudisks2-qt5-dev/noble 5.0.6-1build2 amd64
phonon4qt5-backend-gstreamer/noble 4:4.10.0-2build3 amd64
phonon4qt5-backend-null/noble 4:4.12.0-3.1build3 amd64
phonon4qt5-backend-vlc/noble 0.12.0-3build3 amd64
phonon4qt5/noble 4:4.12.0-3.1build3 amd64
phonon4qt5settings/noble 4:4.12.0-3.1build3 amd64
pyqt5-dev-tools/noble 5.15.10+dfsg-1build6 amd64
pyqt5-dev-tools/noble 5.15.10+dfsg-1build6 i386
pyqt5-dev/noble,noble 5.15.10+dfsg-1build6 all
pyqt5-examples/noble,noble 5.15.10+dfsg-1build6 all
pyqt5.qsci-dev/noble,noble 2.14.1+dfsg-1build3 all
pyqt5chart-dev/noble,noble 5.15.6+dfsg-1build2 all
python-pyqt5.qwt-doc/noble,noble 1.02.02-2build7 all
python3-dbus.mainloop.pyqt5/noble 5.15.10+dfsg-1build6 amd64
python3-dbus.mainloop.pyqt5/noble 5.15.10+dfsg-1build6 i386
python3-poppler-qt5/noble 21.3.0-3build3 amd64
python3-pyqt5.qsci/noble 2.14.1+dfsg-1build3 amd64
python3-pyqt5.qtbluetooth/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtbluetooth/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtchart/noble 5.15.6+dfsg-1build2 amd64
python3-pyqt5.qtmultimedia/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtmultimedia/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtnfc/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtnfc/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtopengl/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtopengl/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtpositioning/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtpositioning/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtquick/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtquick/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtremoteobjects/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtremoteobjects/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtsensors/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtsensors/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtserialport/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtserialport/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtsql/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtsql/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtsvg/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtsvg/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qttexttospeech/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qttexttospeech/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtwebchannel/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtwebchannel/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtwebengine/noble 5.15.6-1build2 amd64
python3-pyqt5.qtwebkit/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtwebkit/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtwebsockets/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtwebsockets/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtx11extras/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtx11extras/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qtxmlpatterns/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5.qtxmlpatterns/noble 5.15.10+dfsg-1build6 i386
python3-pyqt5.qwt/noble 1.02.02-2build7 amd64
python3-pyqt5.sip/noble 12.13.0-1build3 amd64
python3-pyqt5.sip/noble 12.13.0-1build3 i386
python3-pyqt5/noble 5.15.10+dfsg-1build6 amd64
python3-pyqt5/noble 5.15.10+dfsg-1build6 i386
python3-qt5reactor/noble,noble 0.6.1-2 all
python3-qwt3d-qt5/noble 0.1.8-6build7 amd64
qca-qt5-2-utils/noble 2.3.8-1build3 amd64
qcoro-qt5-dev/noble 0.10.0-1.1build3 amd64
qdbus-qt5/noble 5.15.13-1 amd64
qdbus-qt5/noble 5.15.13-1 i386
qdoc-qt5/noble 5.15.13-1 amd64
qdoc-qt5/noble 5.15.13-1 i386
qgnomeplatform-qt5/noble 0.9.2-1build6 amd64
qhelpgenerator-qt5/noble 5.15.13-1 amd64
qhelpgenerator-qt5/noble 5.15.13-1 i386
qml6-module-qt5compat-graphicaleffects/noble 6.4.2-4build3 amd64
qt5-assistant/noble 5.15.13-1 amd64
qt5-assistant/noble 5.15.13-1 i386
qt5-avif-image-plugin/noble 0.7.1+dfsg-1build2 amd64
qt5-doc-html/noble,noble 5.15.13-1 all
qt5-doc/noble,noble 5.15.13-1 all
qt5-gtk-platformtheme/noble,now 5.15.13+dfsg-1ubuntu1 amd64 [installed,automatic]
qt5-gtk-platformtheme/noble 5.15.13+dfsg-1ubuntu1 i386
qt5-gtk2-platformtheme/noble 5.0.0+git23.g335dbec-6build5 amd64
qt5-image-formats-plugin-pdf/noble 5.15.16+dfsg-3 amd64
qt5-image-formats-plugins/noble 5.15.13-1 amd64
qt5-qmake-bin/noble 5.15.13+dfsg-1ubuntu1 amd64
qt5-qmake-bin/noble 5.15.13+dfsg-1ubuntu1 i386
qt5-qmake/noble 5.15.13+dfsg-1ubuntu1 amd64
qt5-qmake/noble 5.15.13+dfsg-1ubuntu1 i386
qt5-qmltooling-plugins/noble 5.15.13+dfsg-1 amd64
qt5-qmltooling-plugins/noble 5.15.13+dfsg-1 i386
qt5-quick-demos/noble 5.15.13-1 amd64
qt5-style-kvantum-l10n/noble,noble 1.0.10-1build3 all
qt5-style-kvantum-themes/noble,noble 1.0.10-1build3 all
qt5-style-kvantum/noble 1.0.10-1build3 amd64
qt5-style-plugin-cleanlooks/noble 5.0.0+git23.g335dbec-6build5 amd64
qt5-style-plugin-motif/noble 5.0.0+git23.g335dbec-6build5 amd64
qt5-style-plugin-plastique/noble 5.0.0+git23.g335dbec-6build5 amd64
qt5-style-plugins/noble 5.0.0+git23.g335dbec-6build5 amd64
qt5-styles-ukui/noble 1.0.8-1ubuntu3 amd64
qt5-ukui-platformtheme/noble 1.0.8-1ubuntu3 amd64
qt5-xdgdesktopportal-platformtheme/noble 5.15.13+dfsg-1ubuntu1 amd64
qt5-xdgdesktopportal-platformtheme/noble 5.15.13+dfsg-1ubuntu1 i386
qt5ct/noble 1.5-1build11 amd64
qt5dxcb-plugin/noble 5.0.65-1build9 amd64
qt5keychain-dev/noble,noble 0.14.2-1build5 all
qt5serialport-examples/noble 5.15.13-1 amd64
qt5serialport-examples/noble 5.15.13-1 i386
qtattributionsscanner-qt5/noble 5.15.13-1 amd64
qtattributionsscanner-qt5/noble 5.15.13-1 i386
qtgstreamer-plugins-qt5/noble 1.2.0-5.2build4 amd64
qtkeychain-qt5-dev/noble 0.14.2-1build5 amd64
uim-qt5-immodule/noble 1:1.8.8-9.3ubuntu2 amd64
uim-qt5/noble 1:1.8.8-9.3ubuntu2 amd64
makem@makem-22:~/obpm$
[COLOR=#000000]
```

[/COLOR][COLOR=#000000]The web page I used also suggested a snap alternative route but as I have said that had a problem for me too:

```

[/COLOR]makem@makem-22:~/obpm$ sudo snap install ubpm
[sudo] password for makem: 
ubpm 1.10.0 from Thomas Löwe (lazyt) installed
makem@makem-22:~/obpm$
[COLOR=#000000]
```[/COLOR]
[COLOR=#000000]
```

[/COLOR]makem@makem-22:~$ sudo snap run ubpm
Authorization required, but no authorization protocol specified
qt.qpa.xcb: could not connect to display :0.0
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.


Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vkkhrdisplay, vnc, wayland-egl, wayland, xcb.


Aborted
makem@makem-22:~$

[COLOR=#000000]
```
[/COLOR]

---

### Post by makem2 on 2024-06-27
I don't know why the blank Code entries but I cannot edit the post!

There is nothing missing.

EDIT: At least I can edit this!

I read the README (as I should have done earlier) and It points to the solution: [https://codeberg.org/LazyT/ubpm](https://codeberg.org/LazyT/ubpm)

---

