---
title: "unable to update"
date: 2017-01-01
forum: General Help
---

### Post by addaffinity on 2017-01-01
I am trying to update firefox but my computer will not.
I tried every suggestion that would possably help me update but everytime it goes through it does not.
This is what I get when I try to update to ubuntu 11.10 in termanal:
```
m@m-System-Product-Name:~$ sudo apt-get install -f
[sudo] password for m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cabextract curl icoutils libcurl3 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-socket-ssl-perl liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libnet-http-perl
  libnet-ssleay-perl libtimedate-perl liburi-perl libwww-perl
  libwww-robotrules-perl libwxbase2.8-0 libwxgtk2.8-0 p7zip-full playonlinux
  python-central python-wxgtk2.8 python-wxversion
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl libdata-dump-perl
  libio-socket-inet6-perl libcrypt-ssleay-perl libauthen-ntlm-perl
  libgnomeprintui2.2-0 p7zip-rar wx2.8-doc wx2.8-examples python-wxtools ruby
  wish tk8.5 tcsh csh octave3.0 mksh pdksh python-xml editra
The following NEW packages will be installed:
  cabextract curl icoutils libcurl3 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-socket-ssl-perl liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libnet-http-perl
  libnet-ssleay-perl libtimedate-perl liburi-perl libwww-perl
  libwww-robotrules-perl libwxbase2.8-0 libwxgtk2.8-0 p7zip-full
  python-central python-wxgtk2.8 python-wxversion
The following packages will be upgraded:
  playonlinux
1 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 16.4 MB/19.4 MB of archives.
After this operation, 60.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  python-central python-wxversion libwxbase2.8-0 libwxgtk2.8-0 python-wxgtk2.8
  cabextract libencode-locale-perl libtimedate-perl libhttp-date-perl
  libfile-listing-perl liburi-perl libhtml-tagset-perl libhtml-parser-perl
  libhtml-tree-perl liblwp-mediatypes-perl libhttp-message-perl
  libhttp-cookies-perl libhttp-negotiate-perl libnet-http-perl
  libnet-ssleay-perl libio-socket-ssl-perl liblwp-protocol-https-perl
  libwww-robotrules-perl libwww-perl icoutils p7zip-full libcurl3 curl
  libfont-afm-perl libhtml-form-perl libhtml-format-perl libhttp-daemon-perl
  libmailtools-perl
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated
m@m-System-Product-Name:~$  sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cabextract curl icoutils libcurl3 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-socket-ssl-perl liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libnet-http-perl
  libnet-ssleay-perl libtimedate-perl liburi-perl libwww-perl
  libwww-robotrules-perl libwxbase2.8-0 libwxgtk2.8-0 p7zip-full playonlinux
  python-central python-wxgtk2.8 python-wxversion
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl libdata-dump-perl
  libio-socket-inet6-perl libcrypt-ssleay-perl libauthen-ntlm-perl
  libgnomeprintui2.2-0 p7zip-rar wx2.8-doc wx2.8-examples python-wxtools ruby
  wish tk8.5 tcsh csh octave3.0 mksh pdksh python-xml editra
The following NEW packages will be installed:
  cabextract curl icoutils libcurl3 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-socket-ssl-perl liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libnet-http-perl
  libnet-ssleay-perl libtimedate-perl liburi-perl libwww-perl
  libwww-robotrules-perl libwxbase2.8-0 libwxgtk2.8-0 p7zip-full
  python-central python-wxgtk2.8 python-wxversion
The following packages will be upgraded:
  playonlinux
1 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 16.4 MB/19.4 MB of archives.
After this operation, 60.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  python-central python-wxversion libwxbase2.8-0
  libwxgtk2.8-0 python-wxgtk2.8 cabextract
  libencode-locale-perl libtimedate-perl
  libhttp-date-perl libfile-listing-perl liburi-perl
  libhtml-tagset-perl libhtml-parser-perl
  libhtml-tree-perl liblwp-mediatypes-perl
  libhttp-message-perl libhttp-cookies-perl
  libhttp-negotiate-perl libnet-http-perl
  libnet-ssleay-perl libio-socket-ssl-perl
  liblwp-protocol-https-perl libwww-robotrules-perl
  libwww-perl icoutils p7zip-full libcurl3 curl
  libfont-afm-perl libhtml-form-perl
  libhtml-format-perl libhttp-daemon-perl
  libmailtools-perl
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
m@m-System-Product-Name:~$ python-central
python-central: command not found
m@m-System-Product-Name:~$ sudo apt-get install python-central
[sudo] password for m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-stable but it is not installable or
                        wine-unstable but it is not installable
               Depends: python-wxgtk2.8 but it is not going to be installed
               Depends: cabextract but it is not going to be installed
               Depends: icoutils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
m@m-System-Product-Name:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty InRelease       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg      
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg       
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources 
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources     
  404  Not Found [IP: 91.189.88.149 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources      
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_US
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
m@m-System-Product-Name:~$ sudo apt-get clean
m@m-System-Product-Name:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
m@m-System-Product-Name:~$ sudo apt-get install python-central
m@m-System-Product-Name:~$ sudo apt-get install python-central
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-stable but it is not installable or
                        wine-unstable but it is not installable
               Depends: python-wxgtk2.8 but it is not going to be installed
               Depends: cabextract but it is not going to be installed
               Depends: icoutils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
What would you suggest I do to fix this problem?

---

### Post by ian-weisser on 2017-01-01
Ubuntu 11.10 is many years past end-of-life, and its software repositories are long retired.
You have not received any security patches in 3.5 years. If online, your system has been vulnerable to published exploits for a very long time.

My advice is to back up your data and do a fresh install of 16.04, which is supported for 5 years.
It is much quicker, simpler, and more secure than kludging an upgrade path on a perhaps-already-compromised system from 11.10 to 12.04 to 14.04 to 16.04.

---

