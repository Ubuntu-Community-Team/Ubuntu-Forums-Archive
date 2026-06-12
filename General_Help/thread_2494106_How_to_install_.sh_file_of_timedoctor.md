---
title: "How to install .sh file of timedoctor?"
date: 2024-01-05
forum: General Help
---

### Post by nilovsergey on 2024-01-05
I try to install timedoctor time tracker from 
[https://2.timedoctor.com/activate?authorized=](https://2.timedoctor.com/activate?authorized=)


on my kubuntu 22.04 
But I downloaded timedoctor2-setup-3.12.77-linux-x86_64.run file in 129 Mib
and script td2-ubuntu-interactive-v3.12.77 .sh with lines:




```


    #!/bin/bash
    
    UBUNTU="https://download.timedoctor.com/3.12.77/linux/ubuntu-18.04/interactive/timedoctor2-setup-3.12.77-linux-x86_64.run"
    
    wget -O /tmp/timedoctor-$$.run $UBUNTU
    
    if [ -e /tmp/timedoctor-$$.run ] ; then 
      chmod a+x /tmp/timedoctor-$$.run 
      /tmp/timedoctor-$$.run --nox11 -- ; retval=$?
      rm -fv /tmp/timedoctor-$$.run
      exit $retval
    fi
    exit 255



```I tried to run it under Downloads directory, but got errors :


```
    master@master-at-home:~/Downloads$ ./td2-ubuntu-interactive-v3.12.77.sh
    bash: ./td2-ubuntu-interactive-v3.12.77.sh: Permission denied
    master@master-at-home:~/Downloads$ sudo ./td2-ubuntu-interactive-v3.12.77.sh
    [sudo] password for master: 
    sudo: ./td2-ubuntu-interactive-v3.12.77.sh: command not found



```







I tried to apply chmod at first and installed it twice , as root and non root user, but failed to install :


```
    master@master-at-home:~/Downloads$ chmod +x td2-ubuntu-interactive-v3.12.77.sh
    master@master-at-home:~/Downloads$ sudo ./td2-ubuntu-interactive-v3.12.77.sh
    [sudo] password for master: 
    --2024-01-05 13:35:29--  https://download.timedoctor.com/3.12.77/linux/ubuntu-18.04/interactive/timedoctor2-setup-3.12.77-linux-x86_64.run
    Resolving download.timedoctor.com (download.timedoctor.com)... 34.111.222.85
    Connecting to download.timedoctor.com (download.timedoctor.com)|34.111.222.85|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 135458476 (129M) [application/octet-stream]
    Saving to: ‘/tmp/timedoctor-64396.run’
    
    /tmp/timedoctor-64396.run                            100%[====================================================================================================================>] 129,18M  9,56MB/s    in 13s     
    
    2024-01-05 13:35:43 (9,91 MB/s) - ‘/tmp/timedoctor-64396.run’ saved [135458476/135458476]
    
    Creating directory bitrock-3.12.77
    Verifying archive integrity...  100%   MD5 checksums are OK. All good.
    Uncompressing bitrock 3.12.77 Package  100%  
    ERROR: This script can't be executed as root user, login as regular user and provide root password if required.
    removed '/tmp/timedoctor-64396.run'
    master@master-at-home:~/Downloads$ ./td2-ubuntu-interactive-v3.12.77.sh
    --2024-01-05 13:36:00--  https://download.timedoctor.com/3.12.77/linux/ubuntu-18.04/interactive/timedoctor2-setup-3.12.77-linux-x86_64.run
    Resolving download.timedoctor.com (download.timedoctor.com)... 34.111.222.85
    Connecting to download.timedoctor.com (download.timedoctor.com)|34.111.222.85|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 135458476 (129M) [application/octet-stream]
    Saving to: ‘/tmp/timedoctor-64787.run’
    
    /tmp/timedoctor-64787.run                            100%[====================================================================================================================>] 129,18M  10,7MB/s    in 13s     
    
    2024-01-05 13:36:13 (10,2 MB/s) - ‘/tmp/timedoctor-64787.run’ saved [135458476/135458476]
    
    Creating directory bitrock-3.12.77
    Verifying archive integrity...  100%   MD5 checksums are OK. All good.
    Uncompressing bitrock 3.12.77 Package/tmp/timedoctor-64787.run: 663: cd: can't cd to bitrock-3.12.77
      100%  
    /tmp/timedoctor-64787.run: 678: cd: can't cd to bitrock-3.12.77
    SUDO_USER is not set. Running uninstall as master
    No TimeDoctor2 instance running!
    cp: cannot stat 'bitrock-3.12.77/*': No such file or directory
    bash: /home/master/timedoctor2/sys_packagers/install_packages.sh: No such file or directory
    find: ‘/home/master/timedoctor2/lib’: No such file or directory
    find: ‘./plugins’: No such file or directory
    ./makeself-setup.sh: line 79: /home/master/timedoctor2/make_symlinks: No such file or directory
    removed '/tmp/timedoctor-64787.run'



```What is wrong ?

---

### Post by TheFu on 2024-01-05
Seems pretty clear to me.
> ERROR: This script can't be executed as root user, login as regular user

Don't use sudo or root when it isn't needed.  I bet there's a README or INSTALL file that explains exactly which commands to run.

Running with **sudo** earlier could have screwed over some things that you need to clean up.  IDK.  By running with sudo before, it could have created some root-only access.  Don't run as root or use sudo when it isn't specifically required.  The clean up - will need sudo.  I'm guessing this command might help, 
```
sudo rm -rf /home/master/timedoctor2
```

The script is all you needed, with execute permissions, BTW.  It downloads the package and runs it, which should do the install, my guess. No sudo needed.

---

### Post by norvel4 on 2024-01-05
Have you made that .sh file executable for regular use and tried it as regular user? If you go into properties and look through them you may find "allow running as program" or similar maybe or maybe not, maybe. I am with that other one that posted, do not run as root or sudo unless asked ever, unless it is a very trusted script maybe or maybe not, maybe.

---

