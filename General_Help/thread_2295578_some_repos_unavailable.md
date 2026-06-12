---
title: "some repos unavailable?"
date: 2015-09-19
forum: General Help
---

### Post by maxinstuff2 on 2015-09-19
I'm running a fully updated Kubuntu 14.04, and I'm trying to install Calibre using:
```
sudo apt-get install calibre
```
and I get the output:
```
max@max-Z87-D3HP:~$ sudo apt-get install calibre
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  calibre-bin fonts-mathjax libjs-mathjax libjs-sphinxdoc libjs-underscore
  libpodofo0.9.0 python-apsw python-cherrypy3 python-cssselect python-cssutils
  python-feedparser python-markdown python-mechanize python-netifaces
  python-pygments python-repoze.lru python-routes python-utidylib python-webob
Suggested packages:
  fonts-stix fonts-mathjax-extras libjs-mathjax-doc python-apsw-doc
  python-markdown-doc ttf-bitstream-vera python-paste python-webob-doc
The following NEW packages will be installed:
  calibre calibre-bin fonts-mathjax libjs-mathjax libjs-sphinxdoc
  libjs-underscore libpodofo0.9.0 python-apsw python-cherrypy3
  python-cssselect python-cssutils python-feedparser python-markdown
  python-mechanize python-netifaces python-pygments python-repoze.lru
  python-routes python-utidylib python-webob
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 27.6 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  fonts-mathjax libjs-mathjax libjs-underscore libjs-sphinxdoc python-apsw
  python-repoze.lru python-routes python-cherrypy3 python-cssutils
  python-feedparser python-markdown python-netifaces python-pygments
  python-utidylib python-mechanize python-cssselect libpodofo0.9.0 calibre-bin
  calibre python-webob
Install these packages without verification? [y/N] y
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe fonts-mathjax all 2.3-1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe libjs-mathjax all 2.3-1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main libjs-underscore all 1.4.4-2ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty-updates/main libjs-sphinxdoc all 1.2.2+dfsg-1ubuntu1.1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe python-apsw amd64 3.8.2-r1-1ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-repoze.lru all 0.6-4
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-routes all 2.0-1build1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-cherrypy3 all 3.2.2-4ubuntu5
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe python-cssutils all 0.9.10-1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-feedparser all 5.1.3-2
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-markdown all 2.4-1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-netifaces amd64 0.8-3build1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-pygments all 1.6+dfsg-1ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-utidylib all 0.2-9build1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe python-mechanize all 1:0.2.5-3
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe python-cssselect all 0.9.1-1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/universe libpodofo0.9.0 amd64 0.9.0-1.2
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty-updates/universe calibre-bin amd64 1.25.0+dfsg-1ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty-updates/universe calibre all 1.25.0+dfsg-1ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com/ubuntu/ trusty/main python-webob all 1.3.1-1
  404  Not Found [IP: 202.158.214.106 80]
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/m/mathjax/fonts-mathjax_2.3-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/m/mathjax/libjs-mathjax_2.3-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/u/underscore/libjs-underscore_1.4.4-2ubuntu1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/s/sphinx/libjs-sphinxdoc_1.2.2+dfsg-1ubuntu1.1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/p/python-apsw/python-apsw_3.8.2-r1-1ubuntu1_amd64.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-repoze.lru/python-repoze.lru_0.6-4_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/r/routes/python-routes_2.0-1build1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cherrypy3/python-cherrypy3_3.2.2-4ubuntu5_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-cssutils_0.9.10-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/f/feedparser/python-feedparser_5.1.3-2_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-markdown/python-markdown_2.4-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/n/netifaces/python-netifaces_0.8-3build1_amd64.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/pygments/python-pygments_1.6+dfsg-1ubuntu1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/u/utidylib/python-utidylib_0.2-9build1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/p/python-mechanize/python-mechanize_0.2.5-3_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/p/python-cssselect/python-cssselect_0.9.1-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/libp/libpodofo/libpodofo0.9.0_0.9.0-1.2_amd64.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre-bin_1.25.0+dfsg-1ubuntu1_amd64.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre_1.25.0+dfsg-1ubuntu1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-webob/python-webob_1.3.1-1_all.deb  404  Not Found [IP: 202.158.214.106 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

When doing apt-get update I get:

```
max@max-Z87-D3HP:~$ sudo apt-get update
Ign http://au.archive.ubuntu.com trusty InRelease
Ign http://au.archive.ubuntu.com trusty-updates InRelease                      
Ign http://au.archive.ubuntu.com trusty-backports InRelease                    
Ign http://au.archive.ubuntu.com trusty Release.gpg                            
Ign http://au.archive.ubuntu.com trusty-updates Release.gpg                    
Ign http://dl.google.com stable InRelease                                      
Ign http://au.archive.ubuntu.com trusty-backports Release.gpg                  
Ign http://au.archive.ubuntu.com trusty Release                                
Ign http://au.archive.ubuntu.com trusty-updates Release                        
Ign http://au.archive.ubuntu.com trusty-backports Release                      
Ign http://au.archive.ubuntu.com trusty/main Sources/DiffIndex                 
Ign http://au.archive.ubuntu.com trusty/restricted Sources/DiffIndex           
Ign http://dl.google.com stable InRelease                                      
Ign http://linux.dropbox.com trusty InRelease                                  
Ign http://au.archive.ubuntu.com trusty/universe Sources/DiffIndex             
Ign http://au.archive.ubuntu.com trusty/multiverse Sources/DiffIndex           
Ign http://au.archive.ubuntu.com trusty/main amd64 Packages/DiffIndex          
Ign http://au.archive.ubuntu.com trusty/restricted amd64 Packages/DiffIndex    
Ign http://au.archive.ubuntu.com trusty/universe amd64 Packages/DiffIndex      
Hit http://dl.google.com stable Release.gpg                                    
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://linux.dropbox.com trusty Release.gpg                                
Ign http://au.archive.ubuntu.com trusty/multiverse amd64 Packages/DiffIndex    
Ign http://au.archive.ubuntu.com trusty/main i386 Packages/DiffIndex           
Ign http://au.archive.ubuntu.com trusty/restricted i386 Packages/DiffIndex     
Ign http://au.archive.ubuntu.com trusty/universe i386 Packages/DiffIndex       
Ign http://au.archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex     
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://dl.google.com stable Release                                        
Hit http://linux.dropbox.com trusty Release                                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://linux.dropbox.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://au.archive.ubuntu.com trusty-updates/main Sources/DiffIndex         
Ign http://au.archive.ubuntu.com trusty-updates/restricted Sources/DiffIndex   
Ign http://au.archive.ubuntu.com trusty-updates/universe Sources/DiffIndex     
Ign http://au.archive.ubuntu.com trusty-updates/multiverse Sources/DiffIndex   
Ign http://au.archive.ubuntu.com trusty-updates/main amd64 Packages/DiffIndex  
Ign http://au.archive.ubuntu.com trusty-updates/restricted amd64 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-updates/universe amd64 Packages/DiffIndex
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://linux.dropbox.com trusty/main i386 Packages                         
Ign http://au.archive.ubuntu.com trusty-updates/multiverse amd64 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex   
Ign http://au.archive.ubuntu.com trusty-updates/restricted i386 Packages/DiffIndex
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://au.archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://au.archive.ubuntu.com trusty-backports/main Sources/DiffIndex       
Ign http://au.archive.ubuntu.com trusty-backports/restricted Sources/DiffIndex 
Ign http://au.archive.ubuntu.com trusty-backports/universe Sources/DiffIndex   
Ign http://au.archive.ubuntu.com trusty-backports/multiverse Sources/DiffIndex 
Ign http://au.archive.ubuntu.com trusty-backports/main amd64 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-backports/restricted amd64 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-backports/universe amd64 Packages/DiffIndex
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://au.archive.ubuntu.com trusty-backports/multiverse amd64 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-backports/main i386 Packages/DiffIndex 
Ign http://au.archive.ubuntu.com trusty-backports/restricted i386 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-backports/universe i386 Packages/DiffIndex
Ign http://au.archive.ubuntu.com trusty-backports/multiverse i386 Packages/DiffIndex
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Ign http://linux.dropbox.com trusty/main Translation-en_GB                     
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Ign http://linux.dropbox.com trusty/main Translation-en                        
Ign http://linux.dropbox.com trusty/main Translation-zh                        
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://linux.dropbox.com trusty/main Translation-en_AU                     
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-zh                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-zh                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-zh                        
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                     
Ign http://au.archive.ubuntu.com trusty/main Translation-en_GB                 
Ign http://au.archive.ubuntu.com trusty/main Translation-en                    
Ign http://au.archive.ubuntu.com trusty/main Translation-zh                    
Ign http://au.archive.ubuntu.com trusty/main Translation-en_AU                 
Ign http://au.archive.ubuntu.com trusty/multiverse Translation-en_GB           
Ign http://au.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://au.archive.ubuntu.com trusty/multiverse Translation-zh              
Ign http://au.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Ign http://au.archive.ubuntu.com trusty/restricted Translation-en_GB           
Ign http://au.archive.ubuntu.com trusty/restricted Translation-en              
Ign http://au.archive.ubuntu.com trusty/restricted Translation-zh              
Ign http://au.archive.ubuntu.com trusty/restricted Translation-en_AU           
Ign http://au.archive.ubuntu.com trusty/universe Translation-en_GB             
Ign http://au.archive.ubuntu.com trusty/universe Translation-en                
Ign http://au.archive.ubuntu.com trusty/universe Translation-zh
Ign http://au.archive.ubuntu.com trusty/universe Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-updates/main Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-updates/main Translation-en
Ign http://au.archive.ubuntu.com trusty-updates/main Translation-zh
Ign http://au.archive.ubuntu.com trusty-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://au.archive.ubuntu.com trusty-updates/multiverse Translation-zh
Ign http://au.archive.ubuntu.com trusty-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-updates/restricted Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://au.archive.ubuntu.com trusty-updates/restricted Translation-zh
Ign http://au.archive.ubuntu.com trusty-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-updates/universe Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://au.archive.ubuntu.com trusty-updates/universe Translation-zh
Ign http://au.archive.ubuntu.com trusty-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-backports/main Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-backports/main Translation-en
Ign http://au.archive.ubuntu.com trusty-backports/main Translation-zh
Ign http://au.archive.ubuntu.com trusty-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://au.archive.ubuntu.com trusty-backports/multiverse Translation-zh
Ign http://au.archive.ubuntu.com trusty-backports/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-backports/restricted Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://au.archive.ubuntu.com trusty-backports/restricted Translation-zh
Ign http://au.archive.ubuntu.com trusty-backports/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com trusty-backports/universe Translation-en_GB
Ign http://au.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://au.archive.ubuntu.com trusty-backports/universe Translation-zh
Ign http://au.archive.ubuntu.com trusty-backports/universe Translation-en_AU
Err http://au.archive.ubuntu.com trusty/main Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/restricted Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/universe Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/multiverse Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/main amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/restricted amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/universe amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/multiverse amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/main i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/restricted i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/universe i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty/multiverse i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/main Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/restricted Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/universe Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/multiverse Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/main amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/restricted amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/universe amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/main i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/restricted i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/universe i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-updates/multiverse i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/main Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/restricted Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/universe Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/multiverse Sources
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/main amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/restricted amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/universe amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/main i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/restricted i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/universe i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
Err http://au.archive.ubuntu.com trusty-backports/multiverse i386 Packages
  404  Not Found [IP: 202.158.214.106 80]
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 202.158.214.106 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I update a few times a week via command line and this is the first time I have noticed these repos not working. It all looks like it is from the same IP address.

Pinging this IP seems fine!?:
```
max@max-Z87-D3HP:~$ ping -c 4 202.158.214.106
PING 202.158.214.106 (202.158.214.106) 56(84) bytes of data.
64 bytes from 202.158.214.106: icmp_seq=1 ttl=49 time=26.0 ms
64 bytes from 202.158.214.106: icmp_seq=2 ttl=49 time=26.5 ms
64 bytes from 202.158.214.106: icmp_seq=3 ttl=49 time=26.5 ms
64 bytes from 202.158.214.106: icmp_seq=4 ttl=49 time=27.5 ms

--- 202.158.214.106 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 26.081/26.690/27.558/0.550 ms

```

The last two days is the first I have noticed these errors returned in apt-get update. I do this in command line a few times per week....

---

### Post by ian-weisser on 2015-09-19
Sometimes a mirror is briefly unavailable while it updates, or may be temporarily overloaded.
Solution: Wait a few minutes and try again.

Sometimes a mirror degrades as the (volunteer) mirror owner changes priorities, or as the network shifts to make the mirror topologically more remote from you.
Solution: Select a different mirror.

You can also [let the Ubuntu Mirrors team know]("https://wiki.ubuntu.com/Mirrors#Communication") about the problem, if it persists.

---

### Post by maxinstuff2 on 2015-09-20
Thanks. 

I just waited and tried again and it is just now working again - all repos working.

Weird that it was broken for so long - 2 full days.

---

