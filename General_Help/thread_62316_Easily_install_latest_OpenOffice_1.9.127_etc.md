---
title: "Easily install latest OpenOffice 1.9.127 etc"
date: 2005-09-04
forum: General Help
---

### Post by Matchless on 2005-09-04
Hi,
   There are a lot of questions as to how to install the latest OpenOffice2 as no further upgrades are appearing in the repositories, latest 1.9.m79. Some nice scripts are available also. Although the one in Breezy is already at 1.9.m129! Maybe Hoary is forgotten in this department! This works in both Breezy and Hoary!
There is an easy way to update to the latest, go to the website and download the latest deb files at [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz)
Extract the deb files into a directory called OpenOffice2 on your desktop. Create your own repository file, install by using Synaptic
Method:
Create a folder i.e Repository and copy the deb file folder OpenOffice2 into it.
Now in the console run:  dpkg-scanpackages .  /dev/null  |  gzip  -9c  >  Packages.gz
This will create the package list.
Now add the line:    deb file:/home/<username>/Desktop/Repository/ ./     in your sources.list or use Synaptic to add.
Open Synaptic, check that your repository is ticked, you may want to untickuncomment all the other repos for the moment. Reload, search for openoffice and you should find all the OpenOffcie 2 version 2.0.0-3 deb files, select for all the files for installation and Bobs your aunty!
You can uninstall 1.9.129 with Synaptic.
Regards
Matchless

---

### Post by delfo on 2005-09-06
Thanks a lot, it works great, except for a little error: 

the line in the sources.list must be 

deb file:/home/<username>/Desktop/Repository/ ./

 :) 

thanks again

delfo

---

### Post by Matchless on 2005-09-09
[QUOTE=delfo]Thanks a lot, it works great, except for a little error: 

the line in the sources.list must be 

deb file:/home/<username>/Desktop/Repository/ ./

 :) 

thanks again

delfo[/QUOTE]

Delfo,
         Thanks, have updated.
Regards
Matchless

---

### Post by panabar on 2005-10-12
Thank You Matchless!
Worked like a charm,  the only problem was associated with the deb files from [http://ftp.linux.cz/pub/localization...org/devel/680/]("http://ftp.linux.cz/pub/localization...org/devel/680/")
Partial install didn't work but installing all of the debs worked.

Thank You again!
:)

---

### Post by pizzipie on 2005-11-13
[quote=Matchless]Hi,
 There are a lot of questions as to how to install the latest OpenOffice2 as no further upgrades are appearing in the repositories, latest 1.9.m79. Some nice scripts are available also. Although the one in Breezy is already at 1.9.m129! Maybe Hoary is forgotten in this department! This works in both Breezy and Hoary!
There is an easy way to update to the latest, go to the website and download the latest deb files at [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz]("http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz")
Extract the deb files into a directory called OpenOffice2 on your desktop. Create your own repository file, install by using Synaptic
Method:
Create a folder i.e Repository and copy the deb file folder OpenOffice2 into it.
Now in the console run:  dpkg-scanpackages .  /dev/null  |  gzip  -9c  >  Packages.gz
This will create the package list.
Now add the line:    deb file:/home/<username>/Desktop/Repository/ ./     in your sources.list or use Synaptic to add.
Open Synaptic, check that your repository is ticked, you may want to untickuncomment all the other repos for the moment. Reload, search for openoffice and you should find all the OpenOffcie 2 version 2.0.0-3 deb files, select for all the files for installation and Bobs your aunty!
You can uninstall 1.9.129 with Synaptic.
Regards
Matchless[/quote]

Hi Matchless. I tried the above with a few changes : Instead of ... -GB_deb.tar.gz I used ... org/devel/680 to download. I opened the application menu => office and found: openoffice.org 2.0 Base, Calc, Draw, and Printer Administration. No writer. There was null response when I clicked on them. Isn't there supposed to be a binary file to run the above modules. i couldn't find one. What does 'repository is ticked' mean?

Thanks for your help. RP

---

