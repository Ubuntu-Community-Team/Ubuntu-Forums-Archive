---
title: "Update Manager in 12.04 not working"
date: 2014-01-06
forum: General Help
---

### Post by donmaz187 on 2014-01-06
Have tried:

apt-get update

then

apt-get upgrade

resulting in following:

dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.3-2ubuntu2.8); however:
  Version of samba-common on system is 2:3.6.3-2ubuntu2.9.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any advice appreciated. I am a novice with linux.

---

### Post by Bucky Ball on 2014-01-06
Welcome. Are you running those commands with 'sudo'? If not, you should be:
```

sudo apt-get update
sudo apt-get upgrade
```

Post any errors from those commands. 

If none, perhaps try:

```
sudo apt-get install samba-common samba
```

---

### Post by deadflowr on 2014-01-06
It says
> [COLOR=#000000]No apport report written because the error message indicates its a followup error from a previous failure.[/COLOR]

Did you run an update sometime before, but close it?
Or something happen during that previous update?

You could look at seeing if fixing broken packages will help
```
sudo apt-get -f install
```
type it as is.
I stress that because sometimes people think they need to add something to the command and it doesn't work as it should.

---

### Post by jeanjd63 on 2014-01-06
Hello
Can you give the returns of the command :
**dpkg  -l  |  grep smbclient**

---

### Post by donmaz187 on 2014-01-06
I had used sudo before the commands and the result was as posted.

I then did as you suggested and ran "sudo apt-get samba-common samba" which resulted in following:

don@don-VirtualBox:~$ sudo apt-getinstall samba-common samba
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newestversion.
You might want to run 'apt-get -finstall' to correct these:
The following packages have unmetdependencies:
 samba : Depends: libwbclient0 (=2:3.6.3-2ubuntu2.9) but 2:3.6.3-2ubuntu2.8 is to be installed
         Recommends: tdb-tools but itis not going to be installed
 smbclient : Depends: samba-common (=2:3.6.3-2ubuntu2.8) but 2:3.6.3-2ubuntu2.9 is to be installed
E: Unmet dependencies. Try 'apt-get -finstall' with no packages (or specify a solution).

So it seems I have a later version of Samba than Update Manager would accept.

Thanks for your input.

---

### Post by donmaz187 on 2014-01-06
I ran the code you suggested which resulted in following:

don@don-VirtualBox:~$ sudo apt-get -finstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages wereautomatically installed and are no longer required:
  linux-headers-3.2.0-52-genericlinux-headers-3.2.0-51 linux-headers-3.2.0-52linux-headers-3.2.0-51-generic
Use 'apt-get autoremove' to removethem.
The following extra packages will beinstalled:
  smbclient
Suggested packages:
  cifs-utils
The following packages will beupgraded:
  smbclient
1 upgraded, 0 newly installed, 0 toremove and 198 not upgraded.
1 not fully installed or removed.
Need to get 0 B/14.0 MB of archives.
After this operation, 9,216 B ofadditional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems preventconfiguration of smbclient:
 smbclient depends on samba-common (=2:3.6.3-2ubuntu2.8); however:
  Version of samba-common on system is2:3.6.3-2ubuntu2.9.
dpkg: error processing smbclient(--configure):
 dependency problems - leavingunconfigured                                                                                                   
No apport report written becauseMaxReports is reached already                                                                                
                                                             Errors were encountered while processing:                                       
 smbclient                                                                                                                                   
E: Sub-process /usr/bin/dpkg returnedan error code (1)          

Thanks for help.

---

### Post by donmaz187 on 2014-01-06
I ran your code with following result:

don@don-VirtualBox:~$ dpkg -l | grepsmbclient                                                                                                
ii  libsmbclient                          2:3.6.3-2ubuntu2.8                      shared library forcommunication with SMB/CIFS servers
ii  python-smbc                           1.0.13-0ubuntu1                         Python bindings for Sambaclients (libsmbclient)
iU  smbclient                             2:3.6.3-2ubuntu2.8                      command-line SMB/CIFSclients for Unix

So it all points to having a later version of Samba than Update Manager will accept.

Thanks for help.

---

### Post by jeanjd63 on 2014-01-07
Hello

The way here is to install manually the package samba with the good version.
If you are on a system 32 bits :
download this file :  [32-bit deb package]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.9_i386.deb")
If you are in 64 bits this one : [64-bit deb package]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.9_amd64.deb")
Then you go to the directory of download (generally Download) and you do :
[B]sudo  dpkg  -i  smbclient*.deb
[/B]and you try :
[B]sudo  apt-get  install  -f

[/B]May be you have to do the same thing with [libsmbclient]("http://www.ubuntuupdates.org/package/core/precise/main/updates/libsmbclient")

---

### Post by donmaz187 on 2014-01-08
Thanks jeanjd63, I downloaded the file as you suggested but it is the same version as the one giving me problems, namely [COLOR=#000000]samba-common 2:3.6.3-2ubuntu2.9 whereas I need [/COLOR][COLOR=#000000] samba-common 2:3.6.3-2ubuntu2.8. If you can advise how I get the dot 8 version instead of the dot 9 which I now have I'd be very grateful.

donmaz187[/COLOR]

---

### Post by jeanjd63 on 2014-01-08
Did you try the commands :
[B]sudo dpkg -i smbclient*.deb
[/B]and 
**sudo dpkg -i libsmbclient*.deb**

Could you give the completes messages of the command :
**[COLOR=#000000]sudo apt-get  -f  install[/COLOR]**

---

### Post by donmaz187 on 2014-01-08
Thanks again jeanjd63. I did as you suggested and first ran  "[B]sudo dpkg -i smbclient*.deb" 
which resulted in the following message

[/B]don@don-VirtualBox:~$ sudo dpkg -ismbclient*.deb
dpkg: error processing smbclient*.deb(--install):
 cannot access archive: No such file ordirectory
Errors were encountered whileprocessing:
 smbclient*.deb

I then ran "[B]sudo dpkg -i libsmbclient*.deb"
which resulted in the following message:

[/B]
don@don-VirtualBox:~$ sudo dpkg -ilibsmbclient*.deb
dpkg: error processinglibsmbclient*.deb (--install):
 cannot access archive: No such file ordirectory
Errors were encountered whileprocessing:
 libsmbclient*.deb

The complete message when I ran "[B][COLOR=#000000]sudo apt-get -f install" was as follows:
[/COLOR][/B][B][COLOR=#000000]
[/COLOR][/B]
don@don-VirtualBox:~$ sudo apt-get -finstall
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages wereautomatically installed and are no longer required:
  linux-headers-3.2.0-52-genericlinux-headers-3.2.0-51 linux-headers-3.2.0-52linux-headers-3.2.0-51-generic
Use 'apt-get autoremove' to removethem.
The following extra packages will beinstalled:
  smbclient
Suggested packages:
  cifs-utils
The following packages will beupgraded:
  smbclient
1 upgraded, 0 newly installed, 0 toremove and 232 not upgraded.
1 not fully installed or removed.
Need to get 0 B/14.0 MB of archives.
After this operation, 9,216 B ofadditional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems preventconfiguration of smbclient:
 smbclient depends on samba-common (=2:3.6.3-2ubuntu2.8); however:
  Version of samba-common on system is2:3.6.3-2ubuntu2.9.
dpkg: error processing smbclient(--configure):
 dependency problems - leavingunconfigured
No apport report written becauseMaxReports is reached already
                                                             Errors were encountered while processing:
 smbclient
E: Sub-process /usr/bin/dpkg returnedan error code (1)
[B][COLOR=#000000]
So I went back to your previous advice and found a site with the dot 8 version of Samba which I downloaded and ran as you suggested with the following result:

[/COLOR][/B]
don@don-VirtualBox:~/Downloads$ sudodpkg -i smbclient*.deb
(Reading database ... 297388 files anddirectories currently installed.)
Preparing to replace smbclient2:3.6.3-2ubuntu2.8 (using smbclient_3.6.3-2ubuntu2.8_i386.deb) ...
Unpacking replacement smbclient ...
dpkg: dependency problems preventconfiguration of smbclient:
 smbclient depends on samba-common (=2:3.6.3-2ubuntu2.8); however:
  Version of samba-common on system is2:3.6.3-2ubuntu2.9.
dpkg: error processing smbclient(--install):
 dependency problems - leavingunconfigured
Processing triggers for man-db ...
Errors were encountered whileprocessing:
smbclient
[B][COLOR=#000000]
So it looks like I can't get anywhere until I get rid of the dot 9 version of Samba now installed.

Thanks again

donmaz187 [/COLOR][/B]

---

### Post by jeanjd63 on 2014-01-08
> **jeanjd63 said:**
> Hello

The way here is to install manually the package samba with the good version.
If you are on a system 32 bits :
download this file :  [32-bit deb package]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.9_i386.deb")
If you are in 64 bits this one : [64-bit deb package]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.9_amd64.deb")
Then you go to the directory of download (generally Download) and you do :
[B]sudo  dpkg  -i  smbclient*.deb
[/B]and you try :
[B]sudo  apt-get  install  -f

[/B]May be you have to do the same thing with [libsmbclient]("http://www.ubuntuupdates.org/package/core/precise/main/updates/libsmbclient")



You need first to download the files with the dot 9 version, and put you in the directory where are the files downloaded.

---

### Post by deadflowr on 2014-01-08
You might try
```
sudo apt-get remove smbclient
```
then clean the package lists out
```
sudo apt-get clean && sudo apt-get autoclean
```
then update the package lists
```
sudo apt-get update
```
then reinstall the smbclient package
```
sudo apt-get install smbclient
```
then if successful, run the update and upgrade commands.
```
sudo apt-get update
sudo apt-get upgrade
```
May or may not work.
If things get harrier, look at this, maybe
[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by donmaz187 on 2014-01-08
Thank you very much [[COLOR=#000000]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577") well done. I used the commands you suggested and now all seems to be in order. Update Manager has even done a final top up and works as it should.

My thanks also to jeanjd63 and others who contributed.

donmaz187

---

