---
title: "Failed to fetch archive.ubuntu and security.ubuntu"
date: 2017-11-08
forum: General Help
---

### Post by olivr3 on 2017-11-08
I am getting the following error when trying to push an application to Heroku.

```
Need to get 419 kB of archives.
After this operation, 998 kB of additional disk space will be used.
Err http://archive.ubuntu.com/ubuntu/ trusty-updates/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to archive.ubuntu.com:80 (91.189.91.26), connection timed out [IP: 91.189.91.26 80]
Err http://archive.ubuntu.com/ubuntu/ trusty/main zip amd64 3.0-8
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.26 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out [IP: 91.189.88.149 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-9ubuntu1.5_amd64.deb  Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out [IP: 91.189.88.149 80]


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/z/zip/zip_3.0-8_amd64.deb  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.26 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
The command '/bin/sh -c apt-get -y install wget zip' returned a non-zero code: 100
 &#9656;    Error: docker build exited with 100

```

sources.list
```
# deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://old-releases.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ xenial universe
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial universe
deb http://old-releases.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial multiverse
deb http://old-releases.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://old-releases.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu xenial-security main restricted
deb http://old-releases.ubuntu.com/ubuntu xenial-security universe
# deb-src http://old-releases.ubuntu.com/ubuntu xenial-security universe
deb http://old-releases.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu xenial-security multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
```
I already tried to upgrade ```
 sudo apt-get upgrade ; update 
``` and renaming the files in source.list. 

Any ideas what it could be?

Thx in Advance.

---

### Post by monkeybrain20122 on 2017-11-08
Server is down or you can't connect to it for some reasons. Just wait a bit and do it again. If still not works try to change the server by opening "Software & Updates" and change "Download from" to another server in the dropdown (screenshot shows 'Main server')

Edited: but I notice this does happen a lot more in 17.10 than 16.04 so there maybe some other issues with 17.10

---

### Post by olivr3 on 2017-11-08
thank you for your reply. 

I've been trying since yesterday without success.

"[COLOR=#000000]If still not  works try to change the server by opening "Software & Updates" and change "Download from" to another server in the dropdown (screenshot shows 'Main server')[/COLOR]" I just tried changing the server to different ones but still getting the same error. Very strange.

At least I know that it is nothing to do with my machine.

---

### Post by DuckHook on 2017-11-08
Something is very wrong here. Your *sources.list* points to *[noparse]http://old-releases.ubuntu.com/ubuntu[/noparse]* but refers to *xenial* (which is a mismatch because Xenial is still very much alive and not an old release). Yet apt is still accessing *archive.canonical.com* which is wrong anyways if you want to use an old release. Finally, we have no idea whether your attempt to change servers can even work because you do not give details.

Perhaps you should not start in the middle with incomplete info, and tell us from the beginning what you did, what version, flavour and system you have installed and what your goal is. Right now, it is impossible to help you because you haven't given any context, history, or info and we're just  going by guess-&-golly.

Also, your update command is wrong. It should be:```
sudo apt update
```...*followed* by:```
sudo apt upgrade
```However, until you tell us what you've actually got installed and what you want to achieve, it is probably not a good idea to do that update right now. It could further bork your install and leave you with a broken *dpkg* subsystem.

Last but not least, please enclose all of your output in CODE tags and don't use non-standard formatting. Otherwise, the forum software automatically pollutes the output with URL tags and makes your output difficult to parse.

---

### Post by olivr3 on 2017-11-09
Okay. let start from the beginning.

I am trying to deploy an application to Heroku.

These are the steps I took to do it.

sudo heroku container:login
sudo heroku create
sudo heroku container:push web --app serene-beyond-70774 <--------------------------------------  the problem happens here

```

sudo heroku container:push web --app serene-beyond-70774
[sudo] password for kujim: 
=== Building web (/var/www/software/docker-enonic-app/Dockerfile)
Sending build context to Docker daemon  3.072kB
Step 1/25 : FROM enonic/java8
 ---> d2cf1f29a6ad
Step 2/25 : MAINTAINER Erik Kaareng-sunde <esu@enonic.com>
 ---> Using cache
 ---> f243073b4a8a
Step 3/25 : ENV XP_DISTRO_VERSION 6.12.2
 ---> Using cache
 ---> 5ce191da5d75
Step 4/25 : ENV XP_ROOT /enonic-xp
 ---> Using cache
 ---> eefe62d76fff
Step 5/25 : ENV XP_HOME /enonic-xp/home
 ---> Using cache
 ---> 92ff17a1630f
Step 6/25 : ENV XP_USER enonic-xp
 ---> Using cache
 ---> 33a54ada01c2
Step 7/25 : ENV XP_UID 1337
 ---> Using cache
 ---> f1891e4829e0
Step 8/25 : RUN echo "export XP_DISTRO_VERSION=$XP_DISTRO_VERSION" >> /etc/environment
 ---> Using cache
 ---> 0540a8088ce4
Step 9/25 : RUN echo "export XP_ROOT=$XP_ROOT" >> /etc/environment
 ---> Using cache
 ---> dd1139444bbf
Step 10/25 : RUN echo "export XP_HOME=$XP_HOME" >> /etc/environment
 ---> Using cache
 ---> 4f0b280afdcd
Step 11/25 : RUN echo "export XP_USER=$XP_USER" >> /etc/environment
 ---> Using cache
 ---> 030a5680befe
Step 12/25 : RUN echo "export XP_UID=$XP_UID" >> /etc/environment
 ---> Using cache
 ---> 7def9e2aad24
Step 13/25 : RUN apt-get -y install wget zip
 ---> Running in 7cf79296704a
Reading package lists...
Building dependency tree...
Reading state information...
wget is already the newest version.
wget set to manually installed.
The following NEW packages will be installed:
  unzip zip
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 419 kB of archives.
After this operation, 998 kB of additional disk space will be used.
Err http://archive.ubuntu.com/ubuntu/ trusty-updates/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to archive.ubuntu.com:80 (91.189.88.149), connection timed out [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com/ubuntu/ trusty/main zip amd64 3.0-8
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.149 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-9ubuntu1.5_amd64.deb  Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out [IP: 91.189.88.152 80]

E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/z/zip/zip_3.0-8_amd64.deb  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.149 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
The command '/bin/sh -c apt-get -y install wget zip' returned a non-zero code: 100
 &#9656;    Error: docker build exited with 100


```

Files: 

dockerfile

```

# Base image
FROM enonic/java8

MAINTAINER Erik Kaareng-sunde <esu@enonic.com>

ENV XP_DISTRO_VERSION 6.12.2
ENV XP_ROOT /enonic-xp
ENV XP_HOME /enonic-xp/home
ENV XP_USER enonic-xp
ENV XP_UID 1337

RUN echo "export XP_DISTRO_VERSION=$XP_DISTRO_VERSION" >> /etc/environment
RUN echo "export XP_ROOT=$XP_ROOT" >> /etc/environment
RUN echo "export XP_HOME=$XP_HOME" >> /etc/environment
RUN echo "export XP_USER=$XP_USER" >> /etc/environment
RUN echo "export XP_UID=$XP_UID" >> /etc/environment[/B]

# Install other software
RUN apt-get -y install wget zip

# Extracting Enonic xp
RUN wget -O /tmp/distro-$XP_DISTRO_VERSION.zip http://repo.enonic.com/public/com/enonic/xp/distro/$XP_DISTRO_VERSION/distro-$XP_DISTRO_VERSION.zip
RUN cd /tmp ; unzip distro-$XP_DISTRO_VERSION.zip
RUN mv /tmp/enonic-xp-$XP_DISTRO_VERSION/home /tmp/enonic-xp-$XP_DISTRO_VERSION/home.org
RUN mkdir -p $XP_ROOT
RUN cp -rf /tmp/enonic-xp-$XP_DISTRO_VERSION/* $XP_ROOT/.

# Adding Enonic xp user
RUN adduser --home $XP_ROOT --gecos "" --no-create-home --UID $XP_UID --disabled-password $XP_USER
RUN chown -R $XP_USER $XP_ROOT
# Adding launcher script
ADD launcher.sh /launcher.sh
RUN chmod +x /launcher.sh

USER enonic-xp

# Exposing web port, debug port and telnet port
EXPOSE 8080 5005 5555

CMD /launcher.sh

```

sources.list (original file)

```

# deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable

```

Is the something wrong with my sources.list?

---

### Post by deadflowr on 2017-11-09
> Is the something wrong with my sources.list?
Nope sources are good and Duckhook gave you the right answer.
You're running commands backwards
You needed to run the update command first, then the upgrade or install command.
The packages you are trying to install are no longer at the version you are trying to install so when trying to download those packages it will keep coming up cannot connect.
Running 
```
sudo apt update
``` 
will fix that problem.

Edit:
if apt update comes up with any errors post the output.

---

### Post by olivr3 on 2017-11-09
There is something wrong. 

I ran ```
 sudo apt update 
``` and then ```
 sudo apt upgrade 
``` and I am still getting the same error. 

```


kujim@kujim-GS73VR-7RF:/var/www/software/docker-enonic-app$ sudo apt-get update --fix-missing
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease                                                                                    
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                                                                                                    
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                                            
Hit:5 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease                                                                                     
Hit:6 http://packages.microsoft.com/repos/vscode stable InRelease                                                                                     
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                                              
Ign:8 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                  
Ign:9 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial InRelease                                                                 
Hit:10 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease                                                              
Hit:11 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease                                                                     
Hit:12 https://deb.nodesource.com/node_6.x xenial InRelease                                         
Hit:13 https://cli-assets.heroku.com/branches/stable/apt ./ InRelease                               
Hit:14 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease  
Hit:15 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease                             
Ign:16 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial Release                           
Ign:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages                  
Hit:19 http://dl.google.com/linux/chrome/deb stable Release                                          
Hit:20 https://download.sublimetext.com apt/dev/ InRelease                     
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages
Hit:27 https://download.docker.com/linux/ubuntu xenial InRelease
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Ign:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Hit:28 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Err:17 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:18 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main i386 Packages
Ign:21 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main all Packages
Ign:22 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en_GB
Ign:23 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main Translation-en
Ign:24 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:25 http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial/main DEP-11 64x64 Icons
Fetched 204 kB in 2s (68.7 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
kujim@kujim-GS73VR-7RF:/var/www/software/docker-enonic-app$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

kujim@kujim-GS73VR-7RF:/var/www/software/docker-enonic-app$ sudo heroku container:push web --app serene-beyond-70774
[sudo] password for kujim: 
=== Building web (/var/www/software/docker-enonic-app/Dockerfile)
Sending build context to Docker daemon  3.072kB
Step 1/25 : FROM enonic/java8
 ---> d2cf1f29a6ad
Step 2/25 : MAINTAINER Erik Kaareng-sunde <esu@enonic.com>
 ---> Using cache
 ---> f243073b4a8a
Step 3/25 : ENV XP_DISTRO_VERSION 6.12.2
 ---> Using cache
 ---> 5ce191da5d75
Step 4/25 : ENV XP_ROOT /enonic-xp
 ---> Using cache
 ---> eefe62d76fff
Step 5/25 : ENV XP_HOME /enonic-xp/home
 ---> Using cache
 ---> 92ff17a1630f
Step 6/25 : ENV XP_USER enonic-xp
 ---> Using cache
 ---> 33a54ada01c2
Step 7/25 : ENV XP_UID 1337
 ---> Using cache
 ---> f1891e4829e0
Step 8/25 : RUN echo "export XP_DISTRO_VERSION=$XP_DISTRO_VERSION" >> /etc/environment
 ---> Using cache
 ---> 0540a8088ce4
Step 9/25 : RUN echo "export XP_ROOT=$XP_ROOT" >> /etc/environment
 ---> Using cache
 ---> dd1139444bbf
Step 10/25 : RUN echo "export XP_HOME=$XP_HOME" >> /etc/environment
 ---> Using cache
 ---> 4f0b280afdcd
Step 11/25 : RUN echo "export XP_USER=$XP_USER" >> /etc/environment
 ---> Using cache
 ---> 030a5680befe
Step 12/25 : RUN echo "export XP_UID=$XP_UID" >> /etc/environment
 ---> Using cache
 ---> 7def9e2aad24
Step 13/25 : RUN apt-get -y install wget zip
 ---> Running in b71c64399804
Reading package lists...
Building dependency tree...
Reading state information...
wget is already the newest version.
wget set to manually installed.
The following NEW packages will be installed:
  unzip zip
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 419 kB of archives.
After this operation, 998 kB of additional disk space will be used.
Err http://archive.ubuntu.com/ubuntu/ trusty-updates/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out [IP: 91.189.88.152 80]
Err http://archive.ubuntu.com/ubuntu/ trusty/main zip amd64 3.0-8
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main unzip amd64 6.0-9ubuntu1.5
  Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out [IP: 91.189.88.149 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-9ubuntu1.5_amd64.deb  Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out [IP: 91.189.88.149 80]


E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/z/zip/zip_3.0-8_amd64.deb  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.152 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
The command '/bin/sh -c apt-get -y install wget zip' returned a non-zero code: 100
 &#9656;    Error: docker build exited with 100



kujim@kujim-GS73VR-7RF:/var/www/software/docker-enonic-app$ 




```

---

### Post by deadflowr on 2017-11-09
Yep,
apt update gave an error:
> E: Failed to fetch [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found

whenever an error occurs this happens next
> E: Some index files failed to download. They have been ignored, or old ones used instead.
This means it's basically going to ignore what you just tried to fetch and use what you have already had, which in this case is rather old and out-of-date.

But enough with the chit chat, how to fix.
The problem is that there is no ppa for fossfreedom/byzanz for 16.04 (xenial)
So you need to remove that ppa from you system.
Simple way: open a terminal and run
```
sudo add-apt-repository -r ppa:fossfreedom/byzanz
```
then retry the update command.

(alternatively you can remove it through the graphical application *Software and Updates* and go to the Other Software tab and scroll down to the fossfreedom/byzanz ppa listing(s) and uncheck to disable it (them if more than one (there may be an entry for source code, and there may not be)
Software and Updates offers to reload when you close the window, that means it'll automatically run the apt update command, fwiw.

This time it should work without fault.
(Or at least there does not seem to be anything that will cause another issue at this point)

---

### Post by olivr3 on 2017-11-10
Yo,

thank you for your reply.

It worked like a charm.  :guitar:

---

