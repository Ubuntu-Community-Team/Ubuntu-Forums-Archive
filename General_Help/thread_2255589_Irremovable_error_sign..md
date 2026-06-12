---
title: "Irremovable error sign."
date: 2014-12-06
forum: General Help
---

### Post by IL TRIVELLA on 2014-12-06
Hi everyone,


Since few months now, it appears on my upper bar, an error sign like that:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Italian_traffic_signs_-_old_-_divieto_di_accesso.svg/40px-Italian_traffic_signs_-_old_-_divieto_di_accesso.svg.png[/IMG]

and when I click on it, I receive this message:

[COLOR=#333333][FONT=UbuntuRegular]"*An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Unknown Error:'<class 'KeyError'>' (The cache has no package named 'skype-bin'")'.     'This usually means that your installed packages have unmet dependencies*"

[/FONT][/COLOR]Can anyone help me to understand what is it? I understand that is about Skype, but I don't have skype anymore and I am not very good at Ubuntu, so I don't understand how to fix that, there is no way for me to remove that sign from the bar.

Thanks.

---

### Post by grahammechanical on 2014-12-06
Let me give you my guess.

Skype is proprietary software and it it is not in the Ubuntu Software Centre. How did you install Skype? However you did it there is still a reference to Skype in your list of software sources. How did you remove Skype?

Anyway, you have been advised to run apt-get in a terminal. Have you done that? What error messages did you get? Run

```
sudo apt-get update
```

and post the error messages in quote tags. Then when can be more specific in identifying what is causing this error message.  By the way, Ubuntu will check for updates at regular times. If there are inconsistencies in our software sources list then we will get that error message. Ubuntu is doing its job.

Regards.

---

### Post by Impavidus on 2014-12-06
Skype is available from the partner repositories (in 14.04 at least), which might be (or have been) enabled. Maybe something wrong with the configuration of the skype-bin package, installed using package manager, but no longer available as the partner repo may be disabled. Something like that.

You may be able to simply uninstall the skype-bin package.

---

### Post by IL TRIVELLA on 2014-12-07
> **grahammechanical said:**
> Let me give you my guess.

Skype is proprietary software and it it is not in the Ubuntu Software Centre. How did you install Skype? However you did it there is still a reference to Skype in your list of software sources. How did you remove Skype?

Anyway, you have been advised to run apt-get in a terminal. Have you done that? What error messages did you get? Run

```
sudo apt-get update
```

and post the error messages in quote tags. Then when can be more specific in identifying what is causing this error message.  By the way, Ubuntu will check for updates at regular times. If there are inconsistencies in our software sources list then we will get that error message. Ubuntu is doing its job.

Regards.

That's the result if I do sudo apt-get update:

```
alessandro@SuperAlex:~$ sudo apt-get update[sudo] password for alessandro: 
Ign http://extras.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty Release                          
Hit http://dl.google.com stable Release.gpg                           
Ign http://archive.ubuntu.com trusty-security InRelease               
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable Release                                        
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-updates Release.gpg                       
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-backports Release.gpg                     
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty-security Release.gpg                      
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty-updates Release                           
Hit http://archive.ubuntu.com trusty-backports Release                         
Hit http://archive.ubuntu.com trusty-security Release                          
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://dl.google.com stable/main amd64 Packages                  
Hit http://archive.ubuntu.com trusty/universe Sources                
Hit http://dl.google.com stable/main i386 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse Sources              
Ign http://extras.ubuntu.com trusty/main Translation-en_US           
Ign http://ppa.launchpad.net trusty/main Translation-en_US           
Hit http://archive.ubuntu.com trusty/main amd64 Packages             
Ign http://extras.ubuntu.com trusty/main Translation-en              
Ign http://ppa.launchpad.net trusty/main Translation-en              
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty-updates/main Sources
Hit http://archive.ubuntu.com trusty-updates/restricted Sources
Ign http://dl.google.com stable/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Sources
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-backports/main Sources
Hit http://archive.ubuntu.com trusty-backports/restricted Sources
Hit http://archive.ubuntu.com trusty-backports/universe Sources
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main Sources
Hit http://archive.ubuntu.com trusty-security/restricted Sources
Hit http://archive.ubuntu.com trusty-security/universe Sources
Hit http://archive.ubuntu.com trusty-security/multiverse Sources
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done
alessandro@SuperAlex:~$ 
```

I removed skype from the software center because it wasn't running anymore...

---

### Post by Impavidus on 2014-12-07
What does```
dpkg --list skype\*
```tell you?

---

### Post by IL TRIVELLA on 2014-12-07
```
alessandro@SuperAlex:~$ dpkg --list skype\*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  skype          <none>       <none>       (no description available)
ii  skype-bin      4.2.0.11-0ub i386         client for Skype VOIP and instant
un  skype-common   <none>       <none>       (no description available)
un  skype-mid      <none>       <none>       (no description available)
alessandro@SuperAlex:~$ 
```

---

### Post by Impavidus on 2014-12-08
Skype has been removed, but its dependency skype-bin is still present. The repository from which it came has been disabled. Not sure why it's complaining though, as having obsolete or manually installed packages is valid.

Try removing skype-bin.```
sudo apt-get purge skype-bin
```

---

### Post by IL TRIVELLA on 2014-12-08
> **Impavidus said:**
> Skype has been removed, but its dependency skype-bin is still present. The repository from which it came has been disabled. Not sure why it's complaining though, as having obsolete or manually installed packages is valid.

Try removing skype-bin.```
sudo apt-get purge skype-bin
```

```
alessandro@SuperAlex:~$ sudo apt-get purge skype-bin[sudo] password for alessandro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  baloo gcc-4.8-base:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libcups2:i386
  libdbusmenu-qt2:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libice6:i386 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkfilemetadata4 libkrb5-3:i386 libkrb5support0:i386 libllvm3.4:i386
  libmysqlclient18:i386 libogg0:i386 liborc-0.4-0:i386 libp11-kit0:i386
  libpciaccess0:i386 libpulse0:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386 libqtwebkit4:i386
  libsamplerate0:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtiff5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386 libvorbis0a:i386
  libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxml2:i386 libxrender1:i386 libxshmfence1:i386
  libxslt1.1:i386 libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
  linux-signed-image-3.13.0-24-generic sni-qt:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  skype-bin:i386*
0 upgraded, 0 newly installed, 1 to remove and 445 not upgraded.
After this operation, 39.3 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 359861 files and directories currently installed.)
Removing skype-bin (4.2.0.11-0ubuntu0.12.04.2) ...
Purging configuration files for skype-bin (4.2.0.11-0ubuntu0.12.04.2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
alessandro@SuperAlex:~$
```

Once I've done that, the error sign on the bar disappeared and straight away it appear on the left bar the icon to update the system, which it didn't happened due to this problem for all the summer... so thank you so much Impavidus, you are the best!!!

So now I presume Skype is completely deleted from the system, if I want to reinstall it safely and without problems again, how can I do it?

---

### Post by Impavidus on 2014-12-09
Skype has been completely removed. If you want to reinstall skype, you first have to go to your software sources. You can find the menu from the software centre, amongst others. Enable the Canonical Partners repository. Refresh the catalogue of available software (should happen automatically in the software centre) and skype should be available.

You have a lot of old 32 bits library packages installed. They may have come as dependencies of skype. It seems Microsoft doesn't make a 64 bit version of skype available. As apt-get tells you, they can be autoremoved.

If your problem has been solved, could you mark this thread as solved? Thread tools (near top of page) -> mark as solved.

---

### Post by IL TRIVELLA on 2014-12-09
> **Impavidus said:**
> Skype has been completely removed. If you want to reinstall skype, you first have to go to your software sources. You can find the menu from the software centre, amongst others. Enable the Canonical Partners repository. Refresh the catalogue of available software (should happen automatically in the software centre) and skype should be available.

You have a lot of old 32 bits library packages installed. They may have come as dependencies of skype. It seems Microsoft doesn't make a 64 bit version of skype available. As apt-get tells you, they can be autoremoved.

If your problem has been solved, could you makt this thread as solved? Thread tools (near top of page) -> mark as solved.

I think I've done what you asked me so now I can install it from the Ubuntu Software Center? and is the one called "Client for Skype VOIP and instant messaging service"?

---

### Post by Impavidus on 2014-12-10
I think that's the long name of the package. The actual package name is simply skype, and should be printed below. If in doubt, you can always use the terminal and use the exact package name```
sudo apt-get install skype
```

---

### Post by IL TRIVELLA on 2014-12-10
> **Impavidus said:**
> I think that's the long name of the package. The actual package name is simply skype, and should be printed below. If in doubt, you can always use the terminal and use the exact package name```
sudo apt-get install skype
```

Impavidus you are a very kind and patient person, thanks a lot for all your help, I solved my problem, got back skype and thanks to you I could finally update my OS again and use again my Ubuntu properly, I will straight away after this reply close and [COLOR=#000000]mark this thread as solved.

[/COLOR]All the best... 

):P

---

### Post by Impavidus on 2014-12-11
Always nice to see another happy Ubuntu user.

---

