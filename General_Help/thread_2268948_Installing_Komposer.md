---
title: "Installing Komposer"
date: 2015-03-12
forum: General Help
---

### Post by Liamdale on 2015-03-12
New to Linux (one year).

I am still learning the ins and outs of software installation in Ubuntu.  The software center was easy to learn but experience has shown that the repository does not always have the latest version.
I've also used the terminal with the get-apt command but again there are multiple repositories and sometimes the commands can become complicated.

Downloading the "tarball" version of a software is a method I like because we can usually download the latest version, read up on the documentation etc...

I've recently upgraded my LibreOffice from version 4.2 to 4.4 using this method.  I've no problem using the Terminal

Now my problem.  I've downloaded the linux version of Komposer from the site to my Downloads Folder : kompozer-0.8b3.en-US.gcc4.2-i686.tar.gz
Extracted it into this same folder but have found that it is not a Deb folder but a fully functional software setup.
Easy, but it's in the wrong place.  It's a subfolder in my Downloads folder.  Also It does not appear in the Dash.  It works but it is not really installed

My web research on how to correct this problem is in vain for the moment.

Can someone explain how to correct this situation without starting all over.  I want to install this software package correctly onto my computor.  I will undoubtly be in this
same situation in the future, therefore I should learn it now.

If got a "How to" folder on my desktop and everything new is documented in this folder

How do I Install kompozer-0.8b3.en-US.gcc4.2-i686.tar.gz correctly?

Any help would be appreciated.

Liamdale

---

### Post by Liamdale on 2015-03-13
Problem solved !  After my post I continued my search.  Most of the data located dealt with three Bash commands  ./configure, make and make install,  but these are to install the source code which was not my case.  I also found a post at : [http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file), which was promising by JamesTheAwesomeDude dated 2012 which _although it did not work_ gave me a serious clue to the process.  The software must be installed in /opt/ folder.  In that folder I found other software already installed and in researching Eclipse I discovered how to do it.

The steps:

[LIST]
[*]extract the tarball in the /opt/ folder: 
[/LIST]
 ```
cd /opt/
sudo tar -zxvf ~/Downloads/kompozer-0.8b3.en-US.gcc4.2-i686.tar.gz
```
[LIST]
[*]create a launcher shortcut for Kompozer 
[/LIST]
```
gksudo gedit /usr/share/applications/kompozer.desktop
```

The file contents:
[Desktop Entry]
Name=Kompozer
Type=Application
Exec=/opt/kompozer/kompozer
Terminal=false
Icon=/opt/kompozer/icons/mozicon16.xpm
Comment=Website Development Environment
NoDisplay=false
Categories=Development;IDE;
Name[en]=Kompozer

Opened the dash type Kompozer in appication lens and there it is, icon and all.  The program works in ubuntu 14.04.  Haven't done any work yet but the application executes.

Liamdale

---

### Post by Bucky Ball on 2015-03-13
*Thread moved to **General Help**.*

***Installation and Upgrades*** is the installing/upgrading the OS.

Where did you get the file? According to their site, the last stable version was released in 2010. I used to use it but as far as I know it hasn't been developed for ages.

Please keep in mind that the latest is not always the greatest and PPAs can be problematic. The reason a slightly older version of a particular software is in the Ubuntu repositories is that it has been tested, approved and is supported in your installed Ubuntu release.

If you start to add a lot of repos, the onus is on you if something breaks with the latest version of whatever. Tarball installs may not get updated, so while you have the latest (untested by Canonical on your release) version of something now, in six months you will need to manually reinstall the next 'latest' version. Sometimes the changes from one version to the next of a software are a few patches that make no visible difference to the user at all.

If you want the latest available everything, why not try the Ubuntu daily build? That is as close to the edge as you can go. Expect breakage wih the latest everything. Good luck.

---

### Post by Bucky Ball on 2015-03-13
Just getting back this: the PPA is [here]("https://launchpad.net/~giuseppe-iuculano/+archive/ubuntu/ppa"). If the project was active and getting updates/upgrades, installing the PPA would mean that Kompozer would be updated/upgraded automatically, you wouldn't need to do it manually.  As it hasn't seen any action in nearly five years, matters not in your case. It would possibly also appear in Dash with a PPA install.

Enjoy Kompozer. I did, and probably will do again in the future. I can find nothing else in Linux/Ubuntu like it. Shame it is no longer being developed. ;)

---

### Post by Liamdale on 2015-03-13
Thanks for the input Bucky Ball;

> I am still learning the ins and outs of software installation in Ubuntu.   The software center was easy to learn but experience has shown that  the repository does not always have the latest version.
I've also used the terminal with the get-apt command but again there are  multiple repositories and sometimes the commands can become  complicated.

May have been over stated on my part.  What I like about Linux is the controled environment which is lacking in Windows.  Windows does not encourage discipline.  When installing a new app, I generally use the terminal and go through a repository.  The tarball approach and the software center come in second place.  I must admit that in using the terminal, I have messed things up on occasion.  For me, amateur programming and learning Linux are my Video games.  You learn by doing.

I have found the tarballs can in some circumstances be the best approach, example ungrading LibreOffice office suite.

My version of Kompozer is 0.8b3 (2010-02-28) downloaded from [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) .  On the site you have Windows, mac and linux downloads in multiple languages.  There are few choices in Linux for web authoring but even in windows I found Kompozer (even if it is no longer maintained) very good.  Like I've already said, I'm an amateur and for the moment Kompozer suites my purpose.

---

### Post by bmullan2 on 2016-01-06
The last .DEB file for Komposer for x64 bit is here:

[https://launchpad.net/~giuseppe-iuculano/+archive/ubuntu/ppa/+sourcepub/1001050/+listing-archive-extra](https://launchpad.net/~giuseppe-iuculano/+archive/ubuntu/ppa/+sourcepub/1001050/+listing-archive-extra)

---

