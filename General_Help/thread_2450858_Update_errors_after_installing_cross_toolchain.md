---
title: "Update errors after installing cross toolchain"
date: 2020-09-22
forum: General Help
---

### Post by py-ohayo on 2020-09-22
Hello,


After installing cross toolchain the following error occur upon update:

```
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages)  404  Not Found [IP: 2001:860:f70a::2 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages)  404  Not Found [IP: 2001:860:f70a::2 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]
```

Where is the problem ?


Thanks.

---

### Post by howefield on 2020-09-22
Thread moved to the "*General Help*" forum.

---

### Post by deadflowr on 2020-09-22
> Where is the problem ?


No arm packages in main, you need to change the sources to reflect that.
The arm packages from main are in the special ports repository.

I think you need to set the main archives sources with [arch=amd64,i386]
and probably set the ports to [arch=armhf,arm64]

In the sources.list file change it from
```
deb archive.ubuntu.com stuff
```
to 
```
deb [arch=amd64,i386] archive.ubuntu.com stuff
```

This sets it to only look for those arch types in those particular repositories.

For arm packages you need to add the ports repository.

this link has a good example of what it should look like in the end
[https://gist.github.com/josephlr/5034c933bbcfddc25a9275037821b048]("https://gist.github.com/josephlr/5034c933bbcfddc25a9275037821b048")

---

### Post by HermanAB on 2020-09-23
Note that development work is best done on a virtual machine, so as not to bugger up the host environment.

---

### Post by py-ohayo on 2020-09-23
Thanks,
I added this

[FONT=courier new]deb [arch=arm64,armhf,ppc64el,s390x] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) bionic main restricted universe multiverse[/FONT]

in the **sources.list**
It didn't help.
Should I add whole staff from the link you provided (i.e. 8 lines) ?

Another question: why I can't add these repositories using **Software & Updates** GUI ?
When I try to add something in **Software & Updates --> Other Software**, "Add Source" button remains inactive after adding new repository in "APT line" field.
Regards.

---

### Post by deadflowr on 2020-09-23
> It didn't help.
Should I add whole staff from the link you provided (i.e. 8 lines) ?
I would.
First I'd backup the original.
Then just make a new sources.list with the github entries.
> When I try to add something in Software & Updates --> Other Software, "Add Source" button remains inactive after adding new repository in "APT line" field.
What is the entry you tried adding?
It requires all proper fields to be correct for what their field represents.

---

### Post by py-ohayo on 2020-09-24
> **deadflowr said:**
> I would.
First I'd backup the original.
Then just make a new sources.list with the github entries.

What is the entry you tried adding?
It requires all proper fields to be correct for what their field represents.

I put all of them. Didn't help. 
Here below I highlighted errors in **bold**

```
pavel@ALABAMA:~$ sudo apt update
[sudo] password for pavel: 
Hit:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]    
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InRelease                    
Hit:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease                     
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates InRelease [88,7 kB]  
Get:6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88,7 kB]   
Get:7 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic InRelease [64,4 kB]      
Hit:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Get:9 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB] 
Hit:10 [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease
Get:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-backports InRelease [74,6 kB]
Hit:12 [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease
Hit:13 [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease     
Get:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security InRelease [88,7 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88,7 kB]  
Ign:16 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  InRelease
Hit:17 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  Release
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB]
Ign:19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
Ign:20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Ign:21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages
Ign:22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages
Ign:19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
Ign:20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [545 kB]
Ign:21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages      
Ign:22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages    
Ign:19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
Ign:20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [472 kB]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [472 kB]
Ign:21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages  
Ign:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages   
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [868 kB]
Ign:22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages    
[B]Err:19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages          
  404  Not Found [IP: 194.158.119.186 80][/B]
Get:28 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main arm64 Packages [734 kB]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [269 kB]
[B]Err:10 [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>[/B]
Ign:20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages    
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [48,9 kB]
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [642 kB]
[B]Err:12 [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>[/B]
Get:33 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [1&#8239;089 kB]
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [708 kB]
[B]Err:13 [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease     
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>[/B]
Get:36 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [236 kB]
Get:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [56,0 kB]
Ign:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Get:40 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Ign:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages   
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Get:41 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main armhf Packages [668 kB]
Ign:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Ign:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages   
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Ign:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Get:42 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [1&#8239;089 kB]
[B]Err:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages   
  404  Not Found [IP: 2001:67c:1360:8001::23 80][/B]
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Ign:43 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages  
Ign:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Get:44 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main ppc64el Packages [652 kB]
Get:45 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [748 kB]
Get:46 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [360 kB]
Get:47 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main s390x Packages [629 kB]
Get:48 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [748 kB]
Get:49 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [360 kB]
Get:50 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main Translation-en [360 kB]
Get:51 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [294 kB]
Get:52 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:53 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:54 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1&#8239;113 kB]
Get:55 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe ppc64el Packages [921 kB]
Get:56 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1&#8239;034 kB]
Get:57 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [107 kB]
Get:58 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [348 kB]
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages
Get:60 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [12,0 kB]
Get:61 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [23,0 kB]
Get:62 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [285 kB]
Ign:63 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages
Get:64 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [461 kB]
Get:65 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1&#8239;033 kB]
Get:66 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]
Get:67 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;288 B]
Get:68 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe s390x Packages [864 kB]
Get:69 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe armhf Packages [929 kB]
Get:70 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe arm64 Packages [986 kB]
Get:71 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe Translation-en [348 kB]
Get:72 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe amd64 DEP-11 Metadata [285 kB]
Get:73 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/universe DEP-11 64x64 Icons [461 kB]
Get:74 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1&#8239;112 kB]
Get:75 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]
Get:76 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;288 B]
Get:77 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main ppc64el Packages [457 kB]
Get:78 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main s390x Packages [435 kB]
Get:79 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main arm64 Packages [533 kB]
Get:80 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main armhf Packages [472 kB] 
Get:81 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main Translation-en [269 kB]      
Get:82 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/main amd64 DEP-11 Metadata [48,9 kB]  
Get:83 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe arm64 Packages [621 kB]                  
Get:84 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe s390x Packages [517 kB]          
Get:85 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe ppc64el Packages [568 kB]
Get:86 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe armhf Packages [569 kB]  
Get:87 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe Translation-en [236 kB]    
Get:88 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/universe amd64 DEP-11 Metadata [56,0 kB]      
Get:89 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]      
Get:90 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [348 kB]
Get:91 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [285 kB]                                               
Get:92 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [21,7 kB]                                                   
Get:93 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [9&#8239;432 B]                                                    
Ign:94 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages                                                             
Get:95 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]                                            
Ign:96 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages                                                                 
Ign:97 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages                                                             
Get:98 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;288 B]                                            
Ign:43 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages                                                                   
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages                                                             
Ign:63 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages                                                               
Ign:94 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages                                                             
Ign:96 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages                                                                 
Ign:97 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages                                                             
Ign:43 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages                                                                   
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages                                                             
Ign:63 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages                                                               
Ign:94 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages                                                             
Ign:96 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages                                                                 
Ign:97 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages                                                             
[B]Err:43 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages                                                                   
  404  Not Found [IP: 194.158.119.186 80][/B]
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages                                                             
Ign:63 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages                                                               
Ign:94 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages                                                             
[B]Err:96 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages                                                                 
  404  Not Found [IP: 2001:860:f70a::2 80][/B]
Ign:97 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages                                                             
Fetched 28,1 MB in 7s (4&#8239;100 kB/s)                                                                                                              
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
[B]E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages)  404  Not Found [IP: 2001:67c:1360:8001::23 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages)  404  Not Found [IP: 2001:860:f70a::2 80][/B]
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list:60
pavel@ALABAMA:~$
```

---

### Post by deadflowr on 2020-09-24
Please post the sources.list


Edit: Also, it seems all your nvidia github repository keys are either broken or out of date.
Looking at the repository instructions here (as an example of one of them): [https://nvidia.github.io/nvidia-container-runtime/]("https://nvidia.github.io/nvidia-container-runtime/")
at the bottom it tells of how to update the repository keys.
This seems to be mentioned in all of these nvidia github repos you have added.
So you'll need to try to update the keys as mentioned for each of the repos you have added.

---

