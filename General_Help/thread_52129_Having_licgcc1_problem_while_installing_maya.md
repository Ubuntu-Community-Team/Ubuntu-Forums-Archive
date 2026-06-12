---
title: "Having licgcc1 problem while installing maya"
date: 2005-07-26
forum: General Help
---

### Post by Boggles3 on 2005-07-26
ok i am currently installing maya and i get these wierd dependancy errors.. im kinda new to linux so sorry if its a dumb question.. ..

heres my output when trying to install the docs of maya

Selecting previously deselected package maya6-5-docs.
(Reading database ... 75666 files and directories currently installed.)
Unpacking maya6-5-docs (from maya6-5-docs_6.5-253_i386.deb) ...
dpkg: dependency problems prevent configuration of maya6-5-docs:
 maya6-5-docs depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing maya6-5-docs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 maya6-5-docs


anyone think they can help .. thanx alot.. :???:

---

### Post by Xian on 2005-07-26
[QUOTE=Boggles3]ok i am currently installing maya and i get these wierd dependancy errors.. im kinda new to linux so sorry if its a dumb question.. ..

maya6-5-docs depends on libgcc1 (>= 1:4.0.0-7); however:
Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.[/QUOTE]
It's not a dumb question or weird error at all. 

Apt is telling you that it needs a version of libgcc1 that is not installed.
Specifically, the version must be greater than or equal to 1:4.0.0-7.
You have a 1:4.0-0 libgcc1 series which is not sufficient.

What to do? Try a different maya release or....
You could install the Breezy libgcc1 version which is [libgcc1_4.0.1-2](http://mirrors.dk.telia.net/ubuntu/pool/main/g/gcc-4.0/libgcc1_4.0.1-2ubuntu3_i386.deb).
However, the package _may_ not be compatible with your Hoary installation.

---

### Post by Boggles3 on 2005-07-26
thats so wierd.. because i had maya6.5 installed on hoary.. i just had some xserver problems later on down the road and would up reinstalling ubuntu.. i wonder why it worked the first time ????

         thanx for your help..
any reason why you think this time it is different?

---

### Post by Xian on 2005-07-26
[QUOTE=Boggles3]any reason why you think this time it is different?[/QUOTE]
Sure, the maya6-5-docs version may have changed.

---

