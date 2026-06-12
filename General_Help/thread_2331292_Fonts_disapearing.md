---
title: "Fonts disapearing"
date: 2016-07-20
forum: General Help
---

### Post by georgesgiralt on 2016-07-20
Hello !
My wife is a big fan of fonts. for two reasons :
1) the first one is that she is a Yoga and Vedic chant teacher and, as such, has to produce documents with Devanagari for her job.
2) she loves making lists, files and loves the look of fonts.
Every other year she complain that the document she created a long time ago has lost all it's various fonts. I spend ages searching why and what happened. Of course the document was produced on an Ubuntu machine using the OpenOffice incarnation of the time.... 
The machine on which she works has never been re-installed using Ubuntu LTS flavour for ages, with upgrades when needed. So the software has evolved from, say version 9, then 12, then 14 ...and so on. Of course, the hardware has followed suit, but without any re-installation, thank GNU/Linux and Ubuntu ! 
As the storage is highly solid (Raid disks with LVM above it) there has been no home directory destruction nor rebuild. Build like a production grade server at work. 
For example she used the font Impact and it is gone. Idem for Arioso, ..... 
I can't remember how and were they came from but I would like for the sake of mindfulness understand what's going on and how I can "permanently" solve the problem...
Many thanks in advance for your help to solve this PITA problem ....

---

### Post by speartip on 2016-07-20
The impact font should be in the package ttf-mscorefonts-installer.
you can install it via synaptic or the command line.

---

### Post by georgesgiralt on 2016-07-20
Yes, but I've this one installed... Well it shows as it is in Synaptic but 
```

$ dpkg -l *ttf-mscorefonts-installe*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
ii  ttf-mscorefonts-installer                     3.4+nmu1ubuntu1             all                         Installer for Microsoft TrueType core fonts
$ 

```
So something is wrong here ! 
I'll try to re-install this one.Thanks.

---

### Post by georgesgiralt on 2016-07-20
So, the wife is surprised ! She has found some fonts which were missing.
But she still miss some fonts for exemple Abadi MT condensd and Lucida Handwriting and more strangely Helvetica... 
She is not  sure the above list is complete, though !

---

