---
title: "Could not download all repository indexes"
date: 2008-07-08
forum: General Help
---

### Post by YMS_1975 on 2008-07-08
I've searched for this error message on this site, but what I found didn't help me (I'm hoping **somebody** can help me).

When I try to update Ubuntu I get the error message : 

[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
[/B]

I've tried changing the download server by going to : System > Administration > Software Sources. Then I selected "Select Best Server".

It did some tests (202 to be precise) and advised that "gplsavoirfairelinux.net" was the best option, so I selected that. After making that change, I'm still having the same problems. I then tried other servers (randomly) but still nothing.

Whenever I launch the update manager, I've noticed that it hangs at 49 of 52 updates. This has been going on for the past week.

Any ideas?

---

### Post by YMS_1975 on 2008-07-09
Does nobody know my pain?

---

### Post by Bubba64 on 2008-07-09
I am not an expert at reading errors but it looks like you might have the CD still ticked on in software sources. If not change the download from repository.

---

### Post by YMS_1975 on 2008-07-09
> **Bubba64 said:**
> I am not an expert at reading errors but it looks like you might have the CD still ticked on in software sources. If not change the download from repository.

Actually, the CD is not ticked. HELP!!!!!    :(

Still getting :

[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

---

### Post by Bubba64 on 2008-07-09
you wouldn't have the CD ticked on unless you did a CD install. You say your trying to up date do you mean upgrade to a new distro, and did you change the  the repository download and try what you were trying. If you change the repository and let it reload a new one then open the terminal and paste this
sudo apt-get update and if it downloads the repositories in the apt source list and brings you back to the original place you started at then run 
sudo apt-get upgrade. Try using the main server in the main repository, and try posting your apt source this will elp others see if you have a corrupted setup.

---

### Post by YMS_1975 on 2008-07-09
> **Bubba64 said:**
> you wouldn't have the CD ticked on unless you did a CD install. You say your trying to up date do you mean upgrade to a new distro, and did you change the  the repository download and try what you were trying. If you change the repository and let it reload a new one then open the terminal and paste this
sudo apt-get update and if it downloads the repositories in the apt source list and brings you back to the original place you started at then run 
sudo apt-get upgrade. Try using the main server in the main repository, and try posting your apt source this will elp others see if you have a corrupted setup.


This is what I got.

Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release.gpg
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Translation-en_CA       
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Translation-en_CA         
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Translation-en_CA       
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release.gpg                                
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Translation-en_CA
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security Release.gpg 
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/main Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/restricted Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/universe Translation-en_CA
Ign [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/multiverse Translation-en_CA
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release      
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release              
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security Release     
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Packages               
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Packages  
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
yousaf@yousaf-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
yousaf@yousaf-desktop:~$



**I know this is a JAVA related problem.**

---

### Post by Bubba64 on 2008-07-09
I don't think it is a java problem but I don't know much look in the 3rd party setting in software sources and see if maybe you have extra repositories from your last distribution, if you have some un tick them and they can be removed from there if needed. Have you also tried the main server, the warty stuff I don't know what that is. Were you running Warty Warthog before the hardy update, and is Hardy the only thing you want running on your computer.

---

### Post by YMS_1975 on 2008-07-09
> **Bubba64 said:**
> I don't think it is a java problem but I don't know much look in the 3rd party setting in software sources and see if maybe you have extra repositories from your last distribution, if you have some un tick them and they can be removed from there if needed. Have you also tried the main server, the warty stuff I don't know what that is.

There were 2 instances of Ubuntu 4.10 (Warty Warthog) & both of them were checked off.

I took the checkmark off, and ran the update. It seems to be ok now.:)

---

### Post by Bubba64 on 2008-07-09
If your not running Warty anymore remove them from the 3rd party, that seems to have been the problem I try to help but I am not a true Geek. Glad to hear it's working.

---

### Post by leandromartinez98 on 2008-09-02
> **Bubba64 said:**
> If your not running Warty anymore remove them from the 3rd party, that seems to have been the problem I try to help but I am not a true Geek. Glad to hear it's working.

Good that it is working now, but anyway I will add some information
because I had the same problem. For me it was that the network
connection was not configured for apt the correct way. That is,
go into synaptic -> Settings -> preferences -> network, and check if the proxies are correct. In my case there was a proxy to be used while
I'm now in a direct connection to the network.

---

