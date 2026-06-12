---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-10-09
forum: General Help
---

### Post by cellenseres on 2018-10-09
Hey Guys, 

I've tried to install nginx-common to my Ubuntu 18.04 Server and ended up with an error I can't fix :S
```
Errors were encountered while processing:                                                
 /var/cache/apt/archives/nginx-common_1.14.0-0ubuntu1.1_all.deb                          
E: Sub-process /usr/bin/dpkg returned an error code (1)                                  


```

I've tried "sudo apt-get -f install"
and got:
```
Reading package lists... Done                                                            
Building dependency tree                                                                 
Reading state information... Done                                                        
Correcting dependencies... Done                                                          
The following packages were automatically installed and are no longer required:          
  libhiredis0.13 libluajit-5.1-2 libluajit-5.1-common libnginx-mod-http-auth-pam         
  libnginx-mod-http-cache-purge libnginx-mod-http-dav-ext libnginx-mod-http-echo         
  libnginx-mod-http-fancyindex libnginx-mod-http-geoip                                   
  libnginx-mod-http-headers-more-filter libnginx-mod-http-image-filter                   
  libnginx-mod-http-lua libnginx-mod-http-ndk libnginx-mod-http-perl                     
  libnginx-mod-http-subs-filter libnginx-mod-http-uploadprogress                         
  libnginx-mod-http-upstream-fair libnginx-mod-http-xslt-filter libnginx-mod-mail        
  libnginx-mod-nchan libnginx-mod-stream nginx-common                                    
Use 'sudo apt autoremove' to remove them.                                                
The following additional packages will be installed:                                     
  nginx-common                                                                           
Suggested packages:                                                                      
  fcgiwrap nginx-doc                                                                     
The following NEW packages will be installed:                                            
  nginx-common                                                                           
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.                           

18 not fully installed or removed.                                                       
Need to get 0 B/37.3 kB of archives.                                                     
After this operation, 272 kB of additional disk space will be used.                      
Do you want to continue? [Y/n] Y                                                         
Preconfiguring packages ...                                                              
(Reading database ... 204885 files and directories currently installed.)                 
Preparing to unpack .../nginx-common_1.14.0-0ubuntu1.1_all.deb ...                       
Unpacking nginx-common (1.14.0-0ubuntu1.1) ...                                           
dpkg: error processing archive /var/cache/apt/archives/nginx-common_1.14.0-0ubuntu1.1_all
.deb (--unpack):                                                                         
 trying to overwrite '/etc/default/nginx', which is also in package sw-nginx 1.13.8-ubunt
u18.04.18061312                                                                          
Errors were encountered while processing:                                                
 /var/cache/apt/archives/nginx-common_1.14.0-0ubuntu1.1_all.deb                          
E: Sub-process /usr/bin/dpkg returned an error code (1)                                  


```

"sudo apt autoremove" gives me:
```
Reading package lists... Done                                                            
Building dependency tree                                                                 
Reading state information... Done                                                        
You might want to run 'apt --fix-broken install' to correct these.                       
The following packages have unmet dependencies:                                          
 libnginx-mod-http-auth-pam : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not i
nstalled                                                                                 
 libnginx-mod-http-cache-purge : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-http-dav-ext : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not in
stalled                                                                                  
 libnginx-mod-http-echo : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not insta
lled                                                                                     
 libnginx-mod-http-fancyindex : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not
 installed                                                                               
 libnginx-mod-http-geoip : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not inst
alled                                                                                    
 libnginx-mod-http-headers-more-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but 
it is not installed                                                                      
 libnginx-mod-http-image-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is n
ot installed                                                                             
 libnginx-mod-http-lua : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not instal
led                                                                                      
 libnginx-mod-http-ndk : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not instal
led                                                                                      
 libnginx-mod-http-perl : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not insta
lled                                                                                     
 libnginx-mod-http-subs-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-http-uploadprogress : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is
 not installed                                                                           
 libnginx-mod-http-upstream-fair : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is 
not installed                                                                            
 libnginx-mod-http-xslt-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-mail : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installed 
 libnginx-mod-nchan : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installed
 libnginx-mod-stream : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installe
d                                                                                        
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solu
tion).                                                                                   


```


Using "sudo apt-get update && sudo apt-get upgrade" gives me:
```
Hit:1 [http://autoinstall.plesk.com/debian/NODE_0.0.1](http://autoinstall.plesk.com/debian/NODE_0.0.1) all InRelease
Hit:2 [http://autoinstall.plesk.com/ubuntu/PMM_0.1.10](http://autoinstall.plesk.com/ubuntu/PMM_0.1.10) bionic InRelease
Hit:3 [http://autoinstall.plesk.com/ubuntu/PSA_17.8.11](http://autoinstall.plesk.com/ubuntu/PSA_17.8.11) bionic InRelease
Hit:4 [http://autoinstall.plesk.com/ubuntu/PHP70_17](http://autoinstall.plesk.com/ubuntu/PHP70_17) bionic InRelease
Hit:5 [http://autoinstall.plesk.com/ubuntu/PHP71_17](http://autoinstall.plesk.com/ubuntu/PHP71_17) bionic InRelease
Hit:6 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) bionic InRelease
Hit:7 [http://autoinstall.plesk.com/ubuntu/PHP72_17](http://autoinstall.plesk.com/ubuntu/PHP72_17) bionic InRelease
Hit:8 [http://repo.cloudlinux.com/kernelcare-debian/8](http://repo.cloudlinux.com/kernelcare-debian/8) stable InRelease
Hit:9 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:10 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:11 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-security InRelease
Hit:12 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done
Reading package lists... Done                                                            
Building dependency tree                                                                 
Reading state information... Done                                                        
You might want to run 'apt --fix-broken install' to correct these.                       
The following packages have unmet dependencies:                                          
 libnginx-mod-http-auth-pam : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not i
nstalled                                                                                 
 libnginx-mod-http-cache-purge : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-http-dav-ext : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not in
stalled                                                                                  
 libnginx-mod-http-echo : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not insta
lled                                                                                     
 libnginx-mod-http-fancyindex : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not
 installed                                                                               
 libnginx-mod-http-geoip : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not inst
alled                                                                                    
 libnginx-mod-http-headers-more-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but 
it is not installed                                                                      
 libnginx-mod-http-image-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is n
ot installed                                                                             
 libnginx-mod-http-lua : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not instal
led                                                                                      
 libnginx-mod-http-ndk : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not instal
led                                                                                      
 libnginx-mod-http-perl : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not insta
lled                                                                                     
 libnginx-mod-http-subs-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-http-uploadprogress : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is
 not installed                                                                           
 libnginx-mod-http-upstream-fair : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is 
not installed                                                                            
 libnginx-mod-http-xslt-filter : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is no
t installed                                                                              
 libnginx-mod-mail : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installed 
 libnginx-mod-nchan : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installed
 libnginx-mod-stream : Depends: nginx-common (= 1.14.0-0ubuntu1.1) but it is not installe
d                                                                                        
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solu
tion).                                                                                   


```


How can I fix that?

---

### Post by TheFu on 2018-10-09
```
apt --fix-broken install
```
???? That's what the error suggests.

And there's **aptitude**, which will try multiple dependency solutions. Just keep rejecting the offered solution if you don't like it.

---

### Post by Yellow Pasque on 2018-10-09
```
trying to overwrite '/etc/default/nginx', which is also in package sw-nginx 1.13.8-ubuntu18.04.18061312 
```

You have a package from the third party repository (Plesk) that is interfering with the nginx package from Ubuntu's repository. You will probably need to remove the sw-nginx package to get the Ubuntu version of nginx installed. It is also possible that these packages are supposed to coexist peacefully and Plesk made a mistake when creating their package. In that case, you should seek support from Plesk. Maybe this is relevant?: [https://support.plesk.com/hc/en-us/articles/115001645205-Is-it-possible-to-update-nginx-from-custom-repository-on-a-Plesk-server-](https://support.plesk.com/hc/en-us/articles/115001645205-Is-it-possible-to-update-nginx-from-custom-repository-on-a-Plesk-server-)

---

