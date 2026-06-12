---
title: "How do I do a recovery cd, partition, directory, whatever..."
date: 2007-09-12
forum: General Help
---

### Post by askander on 2007-09-12
Hi

In the last month I've tried to do some things with my laptop, like testing applications, tried some configurations, etc... and sometimes that led me to reinstall Ubuntu. I like the install process of Ubuntu, because is fat and simple, but is very annoying when I have to download updates, codecs, applications, and other stuff, every time I reinstall.

I have a data partition besides the root and swap ones, so I'd like a way to recover my Ubuntu system the way I like it, and not having to download all my basic stuff everytime I reinstall. 

Is there a way to do this? like a recovery cd or something similar? I'm interested only in the system, because my data is in another partition.

Thanks. :)

---

### Post by Insightfill on 2007-09-12
This [link]("http://www.debianhelp.co.uk/ddcommand.htm") has some good info.  How to dump a partition to a file (with or without compression), etc.

Should be able to do this easily enough - boot from the LiveCD to be sure this is operating with a static disc.  Alternatively, you can use [GParted]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Backup_Restore_Your_Installation").

---

### Post by chrome307 on 2007-09-12
All the packages that you have downloaded you can backtup to a CD or DVD using AptOnCD  (via Add & Remove - Synaptic).

The application once installed can be found under System - Administration.

Once started you can select 'Create AptOnCd' and then it will begin to catalogue all your updates and gives you the option to manually add other DEBS  (eg you might have installed Nero Linux) - at this point make sure you choose 'METAPACKAGE' this way it will include all of the dependencies of the applications required.

Once you've worked you way through all of that burn the disc.

Now I would download AptOnCd as a DEB file and put it onto a floppy/USB stick - the reason for this is once you need to reinstall, you just load up the Ubuntu Cd and then copy over your AptOnCD DEB file - double click to install - then you can load up your backed up AptOnCD Metapackage CD/DVD.

Start up AptOnCd and you can restore, using the CD or if you forget to install AptOnCD on the newly formatted PC, simply go to Synaptic and in the Repositories add the CD/DVD as a Source and it will copy over all the files for you.  To install, use Synaptic and search for the package and mark it for installation.


Full instructions and to download the latest version can be found here

```


http://aptoncd.sourceforge.net/


```

[img]http://aptoncd.sourceforge.net/screenshots/main-create-big.png[/img]

[img]http://aptoncd.sourceforge.net/screenshots/create-opt-big.png[/img]

This is also a useful method of install software on other PC's that just have just need the software updated or applications installed without having to use internet access.

Goodluck :)

---

### Post by askander on 2007-09-12
Looks like aptoncd is exactly what I was looking for... thanks a lot!

---

### Post by chrome307 on 2007-09-12
**Don't forget to read the FAQ's** ....... it's simple to use but a bit of research beforehand helps :)

---

