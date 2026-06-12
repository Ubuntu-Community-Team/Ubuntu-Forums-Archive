---
title: "[INSTALL HELP] xbuntu - DockBarX Xfce Panel Plugin"
date: 2013-07-02
forum: General Help
---

### Post by WarrenSH on 2013-07-02
I followed this tutorial at [http://xubuntugeek.blogspot.com/2013/06/tip-dockbarx-xfce-panel-plugin.html#comment-form](http://xubuntugeek.blogspot.com/2013/06/tip-dockbarx-xfce-panel-plugin.html#comment-form) 

after doing the ```
sudo add-apt-repository ppa:nilarimogard/webupd8 -y && sudo apt-get update && sudo apt-get install --no-install-recommends xfce4-dockbarx-plugin -y
```

my terminal came back with this

```
gpg: keyring `/tmp/tmproxdqr/secring.gpg' createdgpg: keyring `/tmp/tmproxdqr/pubring.gpg' created
gpg: requesting key F0B5D826 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmproxdqr/trustdb.gpg: trustdb created
gpg: key F0B5D826: public key "Launchpad antigone" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release.gpg
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Get:3 http://dl.google.com stable/main i386 Packages [1,216 B]                 
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Get:4 http://security.ubuntu.com raring-security Release.gpg [933 B]           
Get:5 http://archive.canonical.com raring Release.gpg [933 B]                  
Get:6 http://ppa.launchpad.net raring Release.gpg [316 B]                      
Get:7 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]          
Get:8 http://extras.ubuntu.com raring Release.gpg [72 B]                       
Get:9 http://security.ubuntu.com raring-security Release [40.8 kB]             
Get:10 http://archive.canonical.com raring Release [5,919 B]                   
Get:11 http://ppa.launchpad.net raring Release [9,734 B]                       
Get:12 http://us.archive.ubuntu.com raring-backports Release.gpg [933 B]       
Hit http://extras.ubuntu.com raring Release                                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com raring Release                                
Get:13 http://archive.canonical.com raring/partner Sources [2,048 B]           
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com raring/main Sources                               
Get:14 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]           
Get:15 http://ppa.launchpad.net raring/main i386 Packages [760 B]              
Get:16 http://archive.canonical.com raring/partner i386 Packages [3,799 B]     
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Get:17 http://security.ubuntu.com raring-security/main Sources [27.5 kB]       
Get:18 http://us.archive.ubuntu.com raring-backports Release [40.8 kB]         
Get:19 http://security.ubuntu.com raring-security/restricted Sources [14 B]    
Get:20 http://security.ubuntu.com raring-security/universe Sources [6,506 B]   
Hit http://us.archive.ubuntu.com raring/main Sources                           
Get:21 http://security.ubuntu.com raring-security/multiverse Sources [690 B]   
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Get:22 http://security.ubuntu.com raring-security/main i386 Packages [75.6 kB] 
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Get:23 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Ign http://archive.canonical.com raring/partner Translation-en_US              
Ign http://ppa.launchpad.net raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Get:24 http://security.ubuntu.com raring-security/universe i386 Packages [23.1 kB]
Ign http://archive.canonical.com raring/partner Translation-en                 
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://extras.ubuntu.com raring/main Translation-en                        
Get:25 http://security.ubuntu.com raring-security/multiverse i386 Packages [1,403 B]
Hit http://us.archive.ubuntu.com raring/main Translation-en             
Get:26 http://security.ubuntu.com raring-security/main Translation-en [39.9 kB]
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring/restricted Translation-en
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring/universe Translation-en
Get:27 http://us.archive.ubuntu.com raring-updates/main Sources [43.2 kB]
Get:28 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]
Hit http://security.ubuntu.com raring-security/universe Translation-en 
Get:29 http://us.archive.ubuntu.com raring-updates/universe Sources [61.0 kB]
Get:30 http://us.archive.ubuntu.com raring-updates/multiverse Sources [690 B]
Get:31 http://us.archive.ubuntu.com raring-updates/main i386 Packages [112 kB]
Get:32 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:33 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [109 kB]
Get:34 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [1,403 B]
Get:35 http://us.archive.ubuntu.com raring-updates/main Translation-en [55.5 kB]
Ign http://security.ubuntu.com raring-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en      
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en        
Get:36 http://us.archive.ubuntu.com raring-backports/main Sources [14 B]       
Get:37 http://us.archive.ubuntu.com raring-backports/restricted Sources [14 B] 
Get:38 http://us.archive.ubuntu.com raring-backports/universe Sources [4,365 B]
Get:39 http://us.archive.ubuntu.com raring-backports/multiverse Sources [1,403 B]
Get:40 http://us.archive.ubuntu.com raring-backports/main i386 Packages [14 B] 
Get:41 http://us.archive.ubuntu.com raring-backports/restricted i386 Packages [14 B]
Get:42 http://us.archive.ubuntu.com raring-backports/universe i386 Packages [5,801 B]
Get:43 http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages [1,345 B]
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en          
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US   
Fetched 722 kB in 16s (42.8 kB/s)                                              
W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
wlshafor@V5100US:~$ wget -O awoken.zip http://goo.gl/DeCgI && \
> unzip -x awoken.zip  && \
> cd AwOken-2.5/ && \
> test ! -d ~/.icons && mkdir ~/.icons || \
> for f in $(ls *.tar.gz); do tar -xf $f; done && \
> mv AwOken*/ ~/.icons/ && \
> cd ~/.icons/ && \
> sudo cp -p AwOken/awoken-icon-theme-customization /usr/bin && \
> sudo cp -p AwOken/awoken-icon-theme-customization-clear /usr/bin && \
> sudo cp -p AwOkenDark/awoken-icon-theme-customization-dark /usr/bin && \
> sudo cp -p AwOkenWhite/awoken-icon-theme-customization-white /usr/bin
--2013-07-02 12:58:22--  http://goo.gl/DeCgI
Resolving goo.gl (goo.gl)... 74.125.239.98, 74.125.239.105, 74.125.239.102, ...
Connecting to goo.gl (goo.gl)|74.125.239.98|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://dl.dropbox.com/u/8029324/AwOken-2.5.zip [following]
--2013-07-02 12:58:22--  https://dl.dropbox.com/u/8029324/AwOken-2.5.zip
Resolving dl.dropbox.com (dl.dropbox.com)... 23.21.174.62
Connecting to dl.dropbox.com (dl.dropbox.com)|23.21.174.62|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/u/8029324/AwOken-2.5.zip [following]
--2013-07-02 12:58:23--  https://dl.dropboxusercontent.com/u/8029324/AwOken-2.5.zip
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.235.131.126
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.235.131.126|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 52253948 (50M) [application/zip]
Saving to: &#8216;awoken.zip&#8217;


100%[======================================>] 52,253,948  3.26MB/s   in 15s    


2013-07-02 12:58:40 (3.27 MB/s) - &#8216;awoken.zip&#8217; saved [52253948/52253948]


Archive:  awoken.zip
   creating: AwOken-2.5/
 extracting: AwOken-2.5/AwOken.tar.gz  
  inflating: AwOken-2.5/AwOkenDark.tar.gz  
  inflating: AwOken-2.5/AwOkenWhite.tar.gz  
mv: cannot stat &#8216;AwOken*/&#8217;: No such file or directory
wlshafor@V5100US:~/AwOken-2.5$ 
wlshafor@V5100US:~/AwOken-2.5$ cd..
cd..: command not found
wlshafor@V5100US:~/AwOken-2.5$ cd
wlshafor@V5100US:~$ cd..
cd..: command not found
wlshafor@V5100US:~$ cd
wlshafor@V5100US:~$ sudo add-apt-repository ppa:alecive/antigone -r -y && \
> sudo apt-get remove awoken-icon-theme -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package awoken-icon-theme
wlshafor@V5100US:~$ rm -rf ~/.icons/AwOken*/ && \
> sudo rm AwOken/ /usr/bin/awoken-icon-theme-customization*
rm: cannot remove &#8216;AwOken/&#8217;: No such file or directory
rm: cannot remove &#8216;/usr/bin/awoken-icon-theme-customization*&#8217;: No such file or directory
wlshafor@V5100US:~$ sudo add-apt-repository ppa:nilarimogard/webupd8 -y && sudo apt-get update && sudo apt-get install --no-install-recommends xfce4-dockbarx-plugin -y
gpg: keyring `/tmp/tmpmuzbbw/secring.gpg' created
gpg: keyring `/tmp/tmpmuzbbw/pubring.gpg' created
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpmuzbbw/trustdb.gpg: trustdb created
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release.gpg
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://archive.canonical.com raring Release.gpg                            
Hit http://extras.ubuntu.com raring Release.gpg                                
Get:1 http://ppa.launchpad.net raring Release.gpg [316 B]                      
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                  
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://security.ubuntu.com raring-security Release                         
Hit http://archive.canonical.com raring Release                                
Hit http://extras.ubuntu.com raring Release                                    
Get:2 http://ppa.launchpad.net raring Release [9,739 B]                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com raring-updates Release                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com raring-backports Release                      
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://archive.canonical.com raring/partner Sources                        
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Get:3 http://ppa.launchpad.net raring/main i386 Packages [28.6 kB]             
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://archive.canonical.com raring/partner i386 Packages                  
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Hit http://security.ubuntu.com raring-security/universe Sources                
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://security.ubuntu.com raring-security/multiverse Sources              
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Hit http://security.ubuntu.com raring-security/main i386 Packages              
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Hit http://security.ubuntu.com raring-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Hit http://security.ubuntu.com raring-security/universe i386 Packages          
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en              
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Hit http://security.ubuntu.com raring-security/main Translation-en             
Hit http://us.archive.ubuntu.com raring/universe Translation-en                
Hit http://us.archive.ubuntu.com raring-updates/main Sources                   
Ign http://archive.canonical.com raring/partner Translation-en_US              
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com raring-updates/universe Sources               
Ign http://archive.canonical.com raring/partner Translation-en                 
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources             
Ign http://ppa.launchpad.net raring/main Translation-en_US            
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages    
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Ign http://ppa.launchpad.net raring/main Translation-en               
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://security.ubuntu.com raring-security/universe Translation-en
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://us.archive.ubuntu.com raring-backports/main Sources
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources
Hit http://us.archive.ubuntu.com raring-backports/universe Sources
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US   
Fetched 38.7 kB in 10s (3,746 B/s)                                             
W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
wlshafor@V5100US:~$ ^C
wlshafor@V5100US:~$ ^C
wlshafor@V5100US:~$ ^C
wlshafor@V5100US:~$ clear


wlshafor@V5100US:~$ sudo add-apt-repository ppa:nilarimogard/webupd8 -y && sudo apt-get update && sudo apt-get install --no-install-recommends xfce4-dockbarx-plugin -y
gpg: keyring `/tmp/tmpu1xhvf/secring.gpg' created
gpg: keyring `/tmp/tmpu1xhvf/pubring.gpg' created
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpu1xhvf/trustdb.gpg: trustdb created
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release.gpg
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted Translation-en
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en_US
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe Translation-en
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                  
Hit http://archive.canonical.com raring Release.gpg                            
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://security.ubuntu.com raring-security Release                         
Hit http://extras.ubuntu.com raring Release                                    
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring-updates Release                        
Hit http://archive.canonical.com raring Release                                
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com raring-backports Release                      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Hit http://archive.canonical.com raring/partner Sources                        
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Hit http://archive.canonical.com raring/partner i386 Packages                  
Hit http://security.ubuntu.com raring-security/universe Sources                
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://security.ubuntu.com raring-security/multiverse Sources              
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Hit http://security.ubuntu.com raring-security/main i386 Packages              
Hit http://security.ubuntu.com raring-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Hit http://security.ubuntu.com raring-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en              
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Get:1 http://security.ubuntu.com raring-security/main Translation-en [40.2 kB] 
Hit http://us.archive.ubuntu.com raring/universe Translation-en                
Ign http://ppa.launchpad.net raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring-updates/main Sources                   
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources             
Ign http://ppa.launchpad.net raring/main Translation-en                        
Ign http://archive.canonical.com raring/partner Translation-en_US              
Hit http://us.archive.ubuntu.com raring-updates/universe Sources               
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources             
Ign http://archive.canonical.com raring/partner Translation-en                 
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages             
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://security.ubuntu.com raring-security/universe Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://us.archive.ubuntu.com raring-backports/main Sources
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources
Hit http://us.archive.ubuntu.com raring-backports/universe Sources
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US   
Fetched 40.2 kB in 10s (3,903 B/s)                                             
W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)/dists/raring/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

why do I have so many errors? How can I fix them?

---

### Post by WarrenSH on 2013-07-02
The laptop I'm using is a Compaq - Presario V5100us

---

### Post by Toz on 2013-07-02
A couple of issues:

**1.**
> Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release.gpg
Ign cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring Release
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/multiverse i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1) raring/universe i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
...You have the CD enabled in your sources. Disable it by running:
```
software-properties-gtk
```
...going to the "Other Sources" tab and unchecking the cdrom entry. Then re-run:
```
sudo apt-get update && sudo apt-get install --no-install-recommends xfce4-dockbarx-plugin -y
```
...to install xfce4-dockbarx-plugin.


**2.**
> wlshafor@V5100US:~$ wget -O awoken.zip [http://goo.gl/DeCgI](http://goo.gl/DeCgI) && \
> unzip -x awoken.zip  && \
> cd AwOken-2.5/ && \
> test ! -d ~/.icons && mkdir ~/.icons || \
> for f in $(ls *.tar.gz); do tar -xf $f; done && \
> mv AwOken*/ ~/.icons/ && \
> cd ~/.icons/ && \
> sudo cp -p AwOken/awoken-icon-theme-customization /usr/bin && \
> sudo cp -p AwOken/awoken-icon-theme-customization-clear /usr/bin && \
> sudo cp -p AwOkenDark/awoken-icon-theme-customization-dark /usr/bin && \
> sudo cp -p AwOkenWhite/awoken-icon-theme-customization-white /usr/bin
...and
> mv: cannot stat &#8216;AwOken*/&#8217;: No such file or directory
It appears that you are trying to install the awoken icon set using a series of commands that you copied and pasted from somewhere. Unfortunately, that script won't work copied/pasted (looks like a line wrap got in the way). Instead you should run the commands individually like this to ensure it works:
```
wget -O awoken.zip http://goo.gl/DeCgI
```
```
unzip -x awoken.zip
```
```
cd AwOken-2.5/
```
```
test ! -d ~/.icons && mkdir ~/.icons || for f in $(ls *.tar.gz); do tar -xf $f; done
```
^^^^^this was the problem line
```
mv AwOken*/ ~/.icons/
```
```
cd ~/.icons/
```
```
sudo cp -p AwOken/awoken-icon-theme-customization /usr/bin
```
```
sudo cp -p AwOken/awoken-icon-theme-customization-clear /usr/bin
```
```
sudo cp -p AwOkenDark/awoken-icon-theme-customization-dark /usr/bin
```
```
sudo cp -p AwOkenWhite/awoken-icon-theme-customization-white /usr/bin
```

EDIT: Also please refer to [this post]("http://www.webupd8.org/2013/03/dockbarx-available-as-xfce-panel-plugin.html") for further instructions including:
- installing optional plugins
- restarting xfce4-panel

---

### Post by WarrenSH on 2013-07-05
fixed thx

---

