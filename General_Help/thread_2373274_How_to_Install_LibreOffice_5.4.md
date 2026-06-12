---
title: "How to Install LibreOffice 5.4?"
date: 2017-10-04
forum: General Help
---

### Post by artist-wavenet on 2017-10-04
Because LibreOffice 5.3 regularly crashes on me when handling large files I need to try LibreOffice 5.4. In an attempt to do that I followed the directions on this page:

[http://tipsonubuntu.com/2017/07/31/install-libreoffice-5-4-via-official-ppa-ubuntu/](http://tipsonubuntu.com/2017/07/31/install-libreoffice-5-4-via-official-ppa-ubuntu/)

These instructions do not work. The command:
```
sudo add-apt-repository ppa:libreoffice/ppa
```
Executed with long message, but after after responding to its prompt with the return key it finished without error. The Software Updater's Setting buttons does show in its "Other Software" tab that:
```
http://ppa.launchpad.net/libreoffice/ppa/ubuntu
```
is installed.

But when I use "System => Software Updater" as that web page instructs LibreOffice 5.3, which was installed by the app at System => Software, is not updated to LibreOffice 5.4. If I remove LibreOffice 5.3, and once again execute "System => Software Updater" not version of LibreOffice is installed, at least not one visible in the Office submenu, or the search.

What is the right way to upgrade to LibreOffice 5.4?

I do have OpenOffice installed. When using it to edit the files LibreOffice often crashed on it does not ever crash. But editing those large files in OpenOffice has become unwieldy because it cannot collapse the headings in the tree in its Navigation sidebar.

System information:
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

---

### Post by howefield on 2017-10-04
Which version of Ubuntu are you using ?

An alternative option to using a ppa might be to use the LibreOffice snap package.

```
snap find libreoffice
Name         Version  Developer  Notes  Summary
libreoffice  5.3.4.2  canonical  -      LibreOffice is a powerful office suite including word processing
and creation of spreadsheets, slideshows and databases
```

---

### Post by ajgreeny on 2017-10-04
After running the **sudo add-apt-repository ppa:libreoffice/ppa** command did you run **sudo apt update**?

I presume you did or that repo would not show in your software sources, but I just want to double check.

I use that ppa with no difficulties, also in 16.04, so I am a bit baffled.

---

### Post by artist-wavenet on 2017-10-04
I believe I did execute "sudo apt update" . To make sure I did i just now did it, and followed that with "sudo apt upgrade". This did not make a difference. LibreOffice did not appear in the packages it upgraded, and I still have LibreOffice 5.3 in the menu.

---

### Post by mastablasta on 2017-10-05
from:
[http://www.omgubuntu.co.uk/2017/07/how-to-install-libreoffice-5-4-on-ubuntu](http://www.omgubuntu.co.uk/2017/07/how-to-install-libreoffice-5-4-on-ubuntu)

the ppa is:
```
sudo add-apt-repository ppa:libreoffice/libreoffice**-5-4**
```

---

### Post by deadflowr on 2017-10-05
> **howefield said:**
> Which version of Ubuntu are you using ?

An alternative option to using a ppa might be to use the LibreOffice snap package.

```
snap find libreoffice
Name         Version  Developer  Notes  Summary
libreoffice  5.3.4.2  canonical  -      LibreOffice is a powerful office suite including word processing
and creation of spreadsheets, slideshows and databases
```

There's a new snap candidate for version 5.4.1:
[https://forum.snapcraft.io/t/call-for-testing-libreoffice-5-4-1/2217]("https://forum.snapcraft.io/t/call-for-testing-libreoffice-5-4-1/2217")

---

### Post by artist-wavenet on 2017-10-07
The latest stable version is 5.4.2 according to: [http://www.libreoffice.org/download/download/](http://www.libreoffice.org/download/download/).
The command:
```
sudo snap install try libreoffice
```
installed version  5.3.4.2

Is there a snap command that will install the latest stable version without having to explicitly specify the installation's version number?

I am seeking a configuration, whether by PPA, or Snap, that will always update LibreOffice to that latest stable version made available at the link above, whether that be 5.4, 5.5, 6.0, ... whatever. Is there a way?

---

### Post by artist-wavenet on 2017-10-08
When install LibreOffice using the application at System => Software I get prompted for my Ubuntu One sign in credentials. I just found out that means  System => Software is using Snap to install LibreOffice instead of by means of PPA. And that explains why adding ppa:libreoffice/libreoffice-5-4 or ppa:libreoffice/libreoffice does not make any difference.

How can I get System => Software to use PPA instead of Snap to install LibreOffice?

---

### Post by ajgreeny on 2017-10-08
If you have the ppa enabled as shown at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial) simply use the terminal ```
sudo apt install libreoffice
```
You do not need the libreoffice-5.4 ppa mentioned by [COLOR="#FF0000"]mastablasta[/COLOR] above as the standard (fresh) ppa has the same version already.
If you already have LO installed via apt or dpkg you may get an error saying it can not install it, but the **apt install** command will not see a snap package as far as I'm aware so to simplify your system you need to remove that snap package version first with ```
sudo snap remove libreoffice
```or whatever the libreoffice snap package is called.

Once you have got rid of the snap package you may find that the version of LO that now starts from the menu is already 5.4, but as I've never needed a snap package and have none installed, I do not know if they are added to whatever menu system the OS uses, nor if those launchers are removed when a snap package is removed.

---

### Post by artist-wavenet on 2017-10-08
I finally got LibreOffice 5.4.1.2 installed using the Synaptic Package Manager with ppa:libreoffice/libreoffice-5-4 installed. After this I tested ppa:libreoffice/ppa and found it also installed the same 5.4.1.2 version. It appears these PPAs lag behind what is available at [http://www.libreoffice.org/download/download/](http://www.libreoffice.org/download/download/).

Thanks everyone for your help.

---

### Post by ajgreeny on 2017-10-09
The ppas will always lag a little behind the LO site itself as the maintainer of the ppa has to check that all works as it should, however, I am glad that you eventually managed to get things in the version you wanted.

Please now mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by edwinj08 on 2017-10-09
Thanks For sharing valuable reviews. I found this very useful:D

---

