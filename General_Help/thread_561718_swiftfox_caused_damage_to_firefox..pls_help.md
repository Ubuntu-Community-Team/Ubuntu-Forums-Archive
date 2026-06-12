---
title: "swiftfox caused damage to firefox..pls help"
date: 2007-09-27
forum: General Help
---

### Post by parallelogram on 2007-09-27
I had java working nice in firefox. Installed swiftfox and now Java is gone. Instructions at ubuntuguide -(installing java 5 plugin/java 6 plugin etc didn't help fix the issue. Can some one please help me 

Also when I try to install certain stuff, a weird error about some 'miro xml' shows up. Does anyone know why it happens. Giving below the console log

a@a-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts --reinstall
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-jre set to manual installed.
The following packages will be REMOVED:
  sun-java5-fonts
The following NEW packages will be installed:
  sun-java6-fonts
0 upgraded, 1 newly installed, 2 reinstalled, 1 to remove and 0 not upgraded.
Need to get 1814B/6328kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-fonts 6-00-2ubuntu2 [1814B]
Fetched 1814B in 0s (6456B/s)
Preconfiguring packages ...
(Reading database ... 196823 files and directories currently installed.)
Removing sun-java5-fonts ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
(Reading database ... 196811 files and directories currently installed.)
Preparing to replace sun-java6-jre 6-00-2ubuntu2 (using .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
/usr/share/mime/packages/miro.xml:31: parser error : Extra content at the end of the document
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
^
Failed to parse '/usr/share/mime/packages/miro.xml'

Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Preparing to replace sun-java6-plugin 6-00-2ubuntu2 (using .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Unpacking replacement sun-java6-plugin ...
Setting up sun-java6-jre (6-00-2ubuntu2) ...
/usr/share/mime/packages/miro.xml:31: parser error : Extra content at the end of the document
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
^
**[COLOR="Red"]Failed to parse '/usr/share/mime/packages/miro.xml'[/COLOR]**


Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.

Setting up sun-java6-plugin (6-00-2ubuntu2) ...

---

### Post by parallelogram on 2007-09-28
Ok got the firefox part fixed. Can someone help with the other issue...

thx

---

### Post by PatheticMoFo on 2007-09-30
I wouldn't worry about it. That miro.xm thing doesn't look like an actual problem -- just annoying, if anything.

---

