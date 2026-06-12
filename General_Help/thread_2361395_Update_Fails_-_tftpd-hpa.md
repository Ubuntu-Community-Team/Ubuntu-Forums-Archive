---
title: "Update Fails - tftpd-hpa"
date: 2017-05-16
forum: General Help
---

### Post by Alan5127 on 2017-05-16
Hi All,

I am getting an update failure on tftpd-hpa on Ubuntu 16.04 LTS.

If I run updates using the GUI, it says that one failed.

I therefore ran the following from the command line:

```
sudo apt-get clean && cd /var/lib/apt && sudo mv lists lists.old_`date '+%Y%m%d_%H%M'` && sudo mkdir -p lists/partial && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

That command sometimes finds additional items that need updating, so I run it fairly regularly anyway.

This time I got the following (looks normal) as the initial output:

```

Get:1 http://nz.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                                       
Get:3 http://nz.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                                                                                        
Get:4 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]                                                                                                      
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                
Get:6 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease [18.1 kB]                                    
Get:7 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]                                                                
Get:8 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]                                                                             
Get:9 http://nz.archive.ubuntu.com/ubuntu xenial/main Sources [868 kB]                                                                        
Get:10 http://archive.canonical.com/ubuntu xenial/partner Sources [2,796 B]                                                             
Get:11 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease [17.6 kB]                                       
Get:12 http://nz.archive.ubuntu.com/ubuntu xenial/universe Sources [7,728 kB]                                                        
Get:13 http://archive.canonical.com/ubuntu xenial/partner i386 Packages [3,620 B]                                                                                 
Get:14 http://archive.canonical.com/ubuntu xenial/partner Translation-en [1,964 B]                                         
Get:15 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial/main i386 Packages [816 B]                         
Get:16 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial/main Translation-en [160 B]
Get:17 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main i386 Packages [952 B]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main Sources [70.5 kB]                           
Get:19 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main Translation-en [460 B]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [26.8 kB]       
Get:21 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources [1,144 B]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources [2,600 B]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [247 kB]           
Get:24 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [109 kB]          
Get:25 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [54.6 kB]        
Get:26 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [45.7 kB]                  
Get:27 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [99.4 kB]                   
Get:28 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [58.0 kB]                
Get:29 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [32.2 kB]      
Get:30 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]               
Get:31 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [2,912 B]            
Get:32 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [1,232 B]       
Get:33 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 DEP-11 Metadata [212 B]    
Get:34 http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Get:35 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [7,432 B]
Get:36 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,428 B]
Get:37 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 DEP-11 Metadata [199 B]
Get:38 http://nz.archive.ubuntu.com/ubuntu xenial/multiverse Sources [179 kB]
Get:39 http://nz.archive.ubuntu.com/ubuntu xenial/restricted Sources [4,808 B]
Get:40 http://nz.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:41 http://nz.archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]
Get:42 http://nz.archive.ubuntu.com/ubuntu xenial/main i386 DEP-11 Metadata [733 kB]
Get:43 http://nz.archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Get:44 http://nz.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,512 kB]
Get:45 http://nz.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,354 kB]                                                                                                                               
Get:46 http://nz.archive.ubuntu.com/ubuntu xenial/universe i386 DEP-11 Metadata [3,407 kB]                                                                                                                         
Get:47 http://nz.archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]                                                                                                                           
Get:48 http://nz.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                                                                                                
Get:49 http://nz.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                                                                                               
Get:50 http://nz.archive.ubuntu.com/ubuntu xenial/multiverse i386 DEP-11 Metadata [62.4 kB]                                                                                                                        
Get:51 http://nz.archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                                                                                           
Get:52 http://nz.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8,684 B]                                                                                                                               
Get:53 http://nz.archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2,908 B]                                                                                                                              
Get:54 http://nz.archive.ubuntu.com/ubuntu xenial/restricted i386 DEP-11 Metadata [185 B]                                                                                                                          
Get:55 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main Sources [248 kB]                                                                                                                                    
Get:56 http://nz.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [153 kB]                                                                                                                                
Get:57 http://nz.archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [5,288 B]                                                                                                                             
Get:58 http://nz.archive.ubuntu.com/ubuntu xenial-updates/restricted Sources [2,996 B]                                                                                                                             
Get:59 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [516 kB]                                                                                                                              
Get:60 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [215 kB]                                                                                                                             
Get:61 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [299 kB]                                                                                                                       
Get:62 http://nz.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [200 kB]                                                                                                                         
Get:63 http://nz.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [450 kB]                                                                                                                          
Get:64 http://nz.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [182 kB]                                                                                                                         
Get:65 http://nz.archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [159 kB]                                                                                                                   
Get:66 http://nz.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]                                                                                                                     
Get:67 http://nz.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [7,724 B]                                                                                                                       
Get:68 http://nz.archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [4,136 B]                                                                                                                      
Get:69 http://nz.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [2,516 B]                                                                                                                
Get:70 http://nz.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [7,765 B]                                                                                                                  
Get:71 http://nz.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages [7,792 B]                                                                                                                       
Get:72 http://nz.archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,548 B]                                                                                                                      
Get:73 http://nz.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 DEP-11 Metadata [156 B]                                                                                                                  
Fetched 38.9 MB in 14s (2,756 kB/s)                                                                                                                                                                                
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 


```

The only unusual thing is that it says there is one item 'not fully installed or removed' whereas normally it will tell me that some number of items need to be updated.

So, I hit 'Y' to let it go, and got this output:

```
Do you want to continue? [Y/n] y
Setting up tftpd-hpa (5.2+20150808-1ubuntu1.16.04.1) ...
tftpd user (tftp) already exists, doing nothing.

tftpd-hpa directory (/var/lib/tftpboot) already exists, doing nothing.
Job for tftpd-hpa.service failed because the control process exited with error code. See "systemctl status tftpd-hpa.service" and "journalctl -xe" for details.
invoke-rc.d: initscript tftpd-hpa, action "start" failed.
&#9679; tftpd-hpa.service - LSB: HPA's tftp server
   Loaded: loaded (/etc/init.d/tftpd-hpa; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2017-05-16 12:41:22 NZST; 19ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3599 ExecStart=/etc/init.d/tftpd-hpa start (code=exited, status=71)

May 16 12:41:22 OptiPlex-GX280 systemd[1]: Starting LSB: HPA's tftp server...
May 16 12:41:22 OptiPlex-GX280 tftpd-hpa[3599]:  * Starting HPA's tftpd in.tftpd
May 16 12:41:22 OptiPlex-GX280 in.tftpd[3622]: cannot bind to local IPv4 socket: Address already in use
May 16 12:41:22 OptiPlex-GX280 systemd[1]: tftpd-hpa.service: Control process exited, code=exited status=71
May 16 12:41:22 OptiPlex-GX280 systemd[1]: Failed to start LSB: HPA's tftp server.
May 16 12:41:22 OptiPlex-GX280 systemd[1]: tftpd-hpa.service: Unit entered failed state.
May 16 12:41:22 OptiPlex-GX280 systemd[1]: tftpd-hpa.service: Failed with result 'exit-code'.
dpkg: error processing package tftpd-hpa (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tftpd-hpa
E: Sub-process /usr/bin/dpkg returned an error code (1)

alan_admin@UbuntuPC:/var/lib/apt$ 


```

So, I am seeking advice on the best way to proceed.

If safest, I could uninstall tftpd-hpa, but I am nervous about creating instability on my machine.

Ideally, I'd like to just get it to update if possible.

Thanks,

Alan.

---

### Post by ajgreeny on 2017-05-16
You appear to have the latest version of tftpd-hpa from the 16.04 repos installed already so I am not sure why you believe there is another version to update to, and I do not know the package to be able to advise further on possible reasons for your problem.

You do, however, have a problem with google-chrome on a 32 bit system as that repository is no longer valid or available.
Running an old version of google-chrome on your 32 bit machine is therefore risky and you should remove it and use another browser, such as chromium on which google-chrome is based.

---

### Post by Alan5127 on 2017-07-09
As per my OP, apt is saying that tftpd-hpa was not 'fully updated' and nothing I have tried will persuade apt to either update it or stop saying that it has failed to update, so I decided to just uninstall tftpd-hpa and see what happens.

So far, nothing bad :-)

If necessary, I can always try reinstalling it from scratch, but I don't  intend to use tftp on this machine again, so probably won't be an  issue.

Thanks for all yuor suggestions.

Alan.

---

