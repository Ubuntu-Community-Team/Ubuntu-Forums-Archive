---
title: "Unable to remove app"
date: 2014-10-14
forum: General Help
---

### Post by blackagave on 2014-10-14
I recently upgraded to Ubuntu 14.04.1 and I'm trying to remove Cyberlink PowerDVD Linux using the Ubuntu Software Center. After I click the remove button I get a dialog box saying package operation failed. Here are the details:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 1018253 files and directories currently installed.) 
Removing pdvdlinux (4.52) ... 
No value set for `/desktop/gnome/powerdvd/default_list' 
No value set for `/desktop/gnome/powerdvd/autoplay_dvd' 
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd' 
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command' 
rm: cannot remove /usr/share/app-install/desktop/pdvdlinux.desktop: No such file or directory 
rm: cannot remove /usr/share/app-install/icons/pdvdlinux.xpm: No such file or directory 
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found 
dpkg: error processing package pdvdlinux (--remove): 
 subprocess installed post-removal script returned error exit status 127 
Errors were encountered while processing: 
 pdvdlinux

---

### Post by ian-weisser on 2014-10-14
Did you install it from the Software Center? Or some other way?

---

### Post by blackagave on 2014-10-14
I don't know. It isn't anything I've installed recently.

---

### Post by blackagave on 2014-10-14
My bigger issue is I'm trying to get my wifi to work and when I try running this command I get this:

```
mike@dell-desktop:~$ sudo apt-get install firmware-b43legacy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following packages will be REMOVED:
  pdvdlinux
The following NEW packages will be installed:
  b43-fwcutter firmware-b43legacy-installer
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/28.8 kB of archives.
After this operation, 145 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@dell-desktop:~$ sudo modprobe -r b43
mike@dell-desktop:~$ sudo modprobe b43
mike@dell-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [59.7 kB]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [126 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [86.7 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [3,531 B] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [333 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [211 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,532 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages            
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Fetched 838 kB in 7s (111 kB/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/akirad/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/akirad/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
mike@dell-desktop:~$ sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firmware-b43-lpphy-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firmware-b43-installer

E: Package 'firmware-b43-lpphy-installer' has no installation candidate
mike@dell-desktop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following packages will be REMOVED:
  pdvdlinux
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/29.3 kB of archives.
After this operation, 146 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@dell-desktop:~$ sudo apt-get install b43-fwcutter firmware-b43-installerReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pdvdlinux
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/29.3 kB of archives.
After this operation, 146 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@dell-desktop:~$ sudo apt-get install firmware-b43-installer
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following packages will be REMOVED:
  pdvdlinux
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/29.3 kB of archives.
After this operation, 146 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by blackagave on 2014-10-14
Anything I try to do fails and I see garbage about pdvdlinux.

---

### Post by ian-weisser on 2014-10-14
First, try reinstalling pdvdlinux so it will uninstall properly.
```
sudo apt-get install --reinstall pdvdlinux
sudo apt-get remove pdvdlinux
```

If that doesn't work, you can try a riskier approach:
```
sudo dpkg --remove --force-remove-reinstreq pdvdlinux
```

---

### Post by blackagave on 2014-10-14
```
mike@dell-desktop:~$ sudo apt-get install --reinstall pdvdlinux
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of pdvdlinux is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pdvdlinux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@dell-desktop:~$ sudo apt-get remove pdvdlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bzr bzrtools compiz-plugins-extra compiz-plugins-main flam3 fonts-dzongkha
  fonts-vlgothic gnome-dictionary gnome-search-tool hyphen-en-us kdesudo
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-data
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libgdict-1.0-6 libgdict-common libreoffice-emailmerge
  libreoffice-help-cs libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-fr libreoffice-help-ru
  libreoffice-help-sv libreoffice-l10n-cs libreoffice-l10n-de
  libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-es
  libreoffice-l10n-fr libreoffice-l10n-mk libreoffice-l10n-nb
  libreoffice-l10n-nn libreoffice-l10n-ru libreoffice-l10n-sv
  libreoffice-voikko libreoffice-writer2latex libsdl-net1.2
  printer-driver-hpijs python-bzrlib python-configobj python-desktop-agnostic
  python-gpgme python-pyinotify python-xklavier ubuntu-release-upgrader-qt
  update-manager-kde warmux warmux-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pdvdlinux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@dell-desktop:~$ sudo dpkg --remove --force-remove-reinstreq pdvdlinux
(Reading database ... 1018253 files and directories currently installed.)
Removing pdvdlinux (4.52) ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove &#8216;/usr/share/app-install/desktop/pdvdlinux.desktop&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/share/app-install/icons/pdvdlinux.xpm&#8217;: No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: /var/lib/dpkg/info/pdvdlinux.postrm: update-app-install: not found
dpkg: error processing package pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
```

---

### Post by blackagave on 2014-10-14
I figured it out. I finally entered the right search parameters in google and found this.

[http://ubuntuforums.org/showthread.php?t=2053243](http://ubuntuforums.org/showthread.php?t=2053243)

about midway down the page it shows two files and some lines to comment out.

After doing this I was able to resolve my firmware issue following this.

[http://ubuntuforums.org/showthread.php?t=1595803&page=2](http://ubuntuforums.org/showthread.php?t=1595803&page=2)

$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

---

### Post by jamesisin on 2014-10-14
You may want to consider running *sudo apt-get autoremove && sudo apt-get autoclean* since you may have a lot of fluff lying about now.

---

