---
title: "OpenOffice.org v2 Beta 2 Released - get debs"
date: 2005-08-30
forum: General Help
---

### Post by fmerenda on 2005-08-30
Hey all,
OO2beta2 was released, and I found the .debs here if you want to install. Please uninstall the previous beta before you install.

[oo2 beta2 debs and other files](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)

---

### Post by Manny C on 2005-08-30
Or, find the closest [openoffice.org mirror](http://download.openoffice.org/2.0beta2/index.html) with the fastest download, download the Linux x86 tarball. 

First remove your previous OO beta install.

Then the following:

```
tar zxvf OOo_2.0beta2_LinuxIntel_install.tar.gz
``` 

```
cd OOo2.0beta2_native_packed_en-US; cd RPMS
```

```
 sudo alien *.rpm; sudo dpkg -i *.deb
```

This should result in you having the latest OO beta installed. Not sure if menu items are automatically installed. In any case OO is installed at /opt/ so linking is as simple as creating a shortcut to (eg. OO Writer)

```
/opt/openoffice.org1.9.125/program/soffice.bin -writer
```

---

### Post by manicka on 2005-08-30
These debs work beautifully ... Thankyou :D

No more need for scripts etc to alianise the rpms :)

For those who've been using the script available at the wiki [https://wiki.ubuntu.com/OpenOffice2Beta](https://wiki.ubuntu.com/OpenOffice2Beta), the following are some notes I went through to ensure a successful install of these debs

Install notes: You must remove the latest beta that you have from your system.
For me I did it through synaptic, then went to /opt and deleted the openoffice 1.9 folder. (apt doesn't completely remove it because the script moves it from where apt installed it at the final step.)
You also need to delete the icons that are created by the script  in /usr/share/applications.
I did all these jobs with 'sudo nautilus' but I'm sure command line people will know a better way.

Once ready I just untared the deb install file. Changed to the created folder and ran:

sudo dpkg -i *.deb

---

### Post by elempoimen on 2005-08-30
Thank you!

---

### Post by bennettg on 2005-08-31
[QUOTE=Manny C]Or, find the closest [openoffice.org mirror](http://download.openoffice.org/2.0beta2/index.html) with the fastest download, download the Linux x86 tarball. 

First remove your previous OO beta install.

Then the following:

```
tar zxvf OOo_2.0beta2_LinuxIntel_install.tar.gz
``` 

```
cd OOo2.0beta2_native_packed_en-US; cd RPMS
```

```
 sudo alien *.rpm; sudo dpkg -i *.deb
```

This should result in you having the latest OO beta installed. Not sure if menu items are automatically installed. In any case OO is installed at /opt/ so linking is as simple as creating a shortcut to (eg. OO Writer)

```
/opt/openoffice.org1.9.125/program/soffice.bin -writer
```[/QUOTE]


how do i get the icons?

---

### Post by Elrohir on 2005-09-01
[here's]("http://cut0ff.blogsome.com/go.php?http://ubuntuforums.org/attachment.php?attachmentid=1535") where you can find them... but beware, these icons were created for 1.9.104, not for 1.9.125 (latest beta 2) so you have to go to /usr/share/applications (as superuser or root) and modify the path to /opt/OpenOffice1.9.125/soffice -<whatever>

cheers!

---

