---
title: "sudo apt-get upgrade fails"
date: 2015-08-06
forum: General Help
---

### Post by chaaderf on 2015-08-06
Today my desktop compter refused to install updates. Here outputs from terminal commands:

```
user@desktop:~$ sudo apt-get update 
[sudo] password for user: 
Ign http://fi.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://fi.archive.ubuntu.com trusty-updates InRelease                      
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://fi.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security Release [63,5 kB]             
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://deb.opera.com stable InRelease                                      
Hit http://fi.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://fi.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://fi.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://fi.archive.ubuntu.com trusty Release                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://fi.archive.ubuntu.com trusty-updates Release                        
Get:3 http://security.ubuntu.com trusty-security/main Sources [91,1 kB]        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://fi.archive.ubuntu.com trusty-backports Release                      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://fi.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://fi.archive.ubuntu.com trusty/restricted Sources                     
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [2.061 B]  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://fi.archive.ubuntu.com trusty/universe Sources                       
Get:5 http://security.ubuntu.com trusty-security/universe Sources [28,5 kB]    
Hit http://fi.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://fi.archive.ubuntu.com trusty/main amd64 Packages                    
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [2.334 B]  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://fi.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Get:7 http://security.ubuntu.com trusty-security/main amd64 Packages [326 kB]  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://fi.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://fi.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://fi.archive.ubuntu.com trusty/main i386 Packages                 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://fi.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en                     
Hit http://fi.archive.ubuntu.com trusty/universe i386 Packages               
Hit http://fi.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://fi.archive.ubuntu.com trusty/main Translation-en                 
Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8.875 B]
Hit http://fi.archive.ubuntu.com trusty/multiverse Translation-en              
Get:9 http://security.ubuntu.com trusty-security/universe amd64 Packages [112 kB]
Hit http://fi.archive.ubuntu.com trusty/restricted Translation-en              
Get:10 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3.683 B]
Hit http://fi.archive.ubuntu.com trusty/universe Translation-en                
Get:11 http://security.ubuntu.com trusty-security/main i386 Packages [312 kB]
Hit http://fi.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://fi.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://fi.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://fi.archive.ubuntu.com trusty-updates/multiverse Sources           
Hit http://fi.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://fi.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [8.846 B]
Hit http://fi.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [112 kB]
Hit http://fi.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://fi.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://fi.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3.838 B]
Hit http://fi.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://fi.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en 
Hit http://fi.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://fi.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://fi.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://fi.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://fi.archive.ubuntu.com trusty-backports/main Sources
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://fi.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://fi.archive.ubuntu.com trusty-backports/universe Sources
Hit http://fi.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://fi.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://fi.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://fi.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://fi.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://fi.archive.ubuntu.com trusty-backports/main i386 Packages          
Hit http://fi.archive.ubuntu.com trusty-backports/restricted i386 Packages    
Hit http://fi.archive.ubuntu.com trusty-backports/universe i386 Packages  
Hit http://fi.archive.ubuntu.com trusty-backports/multiverse i386 Packages   
Hit http://fi.archive.ubuntu.com trusty-backports/main Translation-en         
Hit http://fi.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://fi.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://fi.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://fi.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://fi.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://fi.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1.076 kB in 3s (293 kB/s)
Reading package lists... Done
```


```
user@desktop:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files bsdutils gir1.2-gtk-3.0 libblkid1 libgail-3-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libmount1 libuuid1 mount oneconf oneconf-common
  python-oneconf python3-oneconf ubuntu-drivers-common util-linux uuid-runtime
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 798 kB/3.250 kB of archives.
After this operation, 7.168 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main mount amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main util-linux amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main bsdutils amd64 1:2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main libblkid1 amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main libmount1 amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main ubuntu-drivers-common amd64 1:0.2.91.11
  404  Not Found [IP: 130.230.54.102 80]
Err http://fi.archive.ubuntu.com/ubuntu/ trusty-updates/main uuid-runtime amd64 2.20.1-5.1ubuntu20.6
  404  Not Found [IP: 130.230.54.102 80]
E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/libuuid1_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/libblkid1_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/libmount1_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-drivers-common/ubuntu-drivers-common_0.2.91.11_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/uuid-runtime_2.20.1-5.1ubuntu20.6_amd64.deb  404  Not Found [IP: 130.230.54.102 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


```
user@desktop:~$ ping -c 15 130.230.54.102
PING 130.230.54.102 (130.230.54.102) 56(84) bytes of data.
64 bytes from 130.230.54.102: icmp_seq=1 ttl=59 time=18.1 ms
64 bytes from 130.230.54.102: icmp_seq=2 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=3 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=4 ttl=59 time=17.6 ms
64 bytes from 130.230.54.102: icmp_seq=5 ttl=59 time=18.0 ms
64 bytes from 130.230.54.102: icmp_seq=6 ttl=59 time=18.1 ms
64 bytes from 130.230.54.102: icmp_seq=7 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=8 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=9 ttl=59 time=17.6 ms
64 bytes from 130.230.54.102: icmp_seq=10 ttl=59 time=17.5 ms
64 bytes from 130.230.54.102: icmp_seq=11 ttl=59 time=18.3 ms
64 bytes from 130.230.54.102: icmp_seq=12 ttl=59 time=18.1 ms
64 bytes from 130.230.54.102: icmp_seq=13 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=14 ttl=59 time=17.8 ms
64 bytes from 130.230.54.102: icmp_seq=15 ttl=59 time=18.3 ms

--- 130.230.54.102 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14023ms
rtt min/avg/max/mdev = 17.597/17.944/18.339/0.256 ms
```

Any ideas what's going on and how to resolve the problem? Network is working when using a browser, but the actual update is not...

---

### Post by dino99 on 2015-08-06
switch to the 'main' server instead of your local one

---

### Post by chaaderf on 2015-08-06
Thank you. Didn't even think about that option... xD

---

