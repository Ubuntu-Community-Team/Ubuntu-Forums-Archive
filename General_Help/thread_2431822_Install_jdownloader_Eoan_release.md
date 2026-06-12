---
title: "Install jdownloader Eoan release"
date: 2019-11-22
forum: General Help
---

### Post by Automat2 on 2019-11-22
Hello,
I have installed Ubuntu Eoan on a clean install, not updated.
Following the instructions here: [URL="https://www.wikihow.com/Install-Jdownloader-on-Ubuntu"]https://www.wikihow.com/Install-Jdownloader-on-Ubuntu
[/URL]I typed [PHP]sudo add-apt-repository ppa:jd-team/jdownloader[/PHP] in terminal and got the result:
[PHP]JDownloader is open source, platform independent and written completely in Java. It simplifies downloading files from One-Click-Hosters like Rapidshare.com or Megaupload.com - not only for users with a premium account but also for users who don't pay. It offers downloading in multiple parallel streams, captcha recognition, automatic file extraction and much more. Additionally, many "link encryption" sites are supported - so you just paste the "encrypted" links and JDownloader does the rest. JDownloader can import CCF, RSDF and DLC files.

The jdownloader-installer package contains only a desktop file and a script, which will download and launch the latest JDownloader. The downloaded files will be stored in ~/.jdownloader by default.

Run these commands in a terminal to install the jdownloader-installer package:

sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader-installer
 More info: https://launchpad.net/~jd-team/+archive/ubuntu/jdownloader
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://archive.canonical.com/ubuntu eoan InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Ign:3 http://ppa.launchpad.net/jd-team/jdownloader/ubuntu eoan InRelease       
Hit:4 http://gb.archive.ubuntu.com/ubuntu eoan InRelease                       
Hit:5 http://security.ubuntu.com/ubuntu eoan-security InRelease                
Ign:6 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu eoan InRelease  
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:8 http://gb.archive.ubuntu.com/ubuntu eoan-updates InRelease             
Err:9 http://ppa.launchpad.net/jd-team/jdownloader/ubuntu eoan Release   
  404  Not Found [IP: 91.189.95.83 80]
Hit:10 http://gb.archive.ubuntu.com/ubuntu eoan-backports InRelease
Err:11 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu eoan Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/jd-team/jdownloader/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.[/PHP]
The repository has appeared in the "Software & Updates" > "Other Software" menu but I get a warning message about this repository not being available for the Eoan release.
If I continued with the install, errors and warnings appear and can't start the app.
Do I have to wait until jdownloader devs come up with the Eoan release update?
Thanks,

---

