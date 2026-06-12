---
title: "Installing CodeBlocks nightmare!!!!!"
date: 2008-01-10
forum: General Help
---

### Post by RudolfMDLT on 2008-01-10
Hi there,

I'm really struggling to get codeblocks installed. I'm actually willing to donate a kidney or a testicle! 

I have followed a HowTo here and on the code blocks website. No matter what I do I can't download it via apt and when I download the deb from a sister website I get dependency issues.

**If you are running codeblocks, how did you install it!?**

I will be REALLY greatful for any help!

Thanks,

Rudolf

PS: Here are the HowTo's I have followed and the error's I am stuck with now. 

[http://ubuntuforums.org/showthread.php?t=558030](http://ubuntuforums.org/showthread.php?t=558030)  post 11
[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

The above don't work so I then downloaded the deb manually here:
[http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)

and I also downloaded and compiled form source the latest wxwidgets.

I still get the dependancy error.

---

### Post by taurus on 2008-01-10
Can you at least post the whole error message when you try to compile it?

---

### Post by RudolfMDLT on 2008-01-10
Thanks for the reply.

I don't get any errors when compiling from source. I do get the following errors though:

When following these instruction:
> add these repositories:

Code:

deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) distname1 universe
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) distname2 main

replace distname1 with either gutsy, feisty, or edgy.
replace distname2 with either gutsy-wx, feisty-wx, or edgy-wx.

get the gpg key for the repos:

Code:

wget -q [http://lgp203.free.fr/public.key](http://lgp203.free.fr/public.key) -O- | sudo apt-key add -
wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -

and to install the nightly build of code::blocks use:
Code:
[COLOR="DarkOrange"]
sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib[/COLOR]

This will keep you updated thru update-manager with the newest nightly build.

I get the following errors:

> rudolf@rudolf-laptop:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcodeblocks0


> rudolf@rudolf-laptop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty Release.gpg                                      
Ign [http://apt.tt-solutions.com](http://apt.tt-solutions.com) gusty Release.gpg                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_ZA                    
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release.gpg                 
Ign [http://apt.tt-solutions.com](http://apt.tt-solutions.com) gusty/main Translation-en_ZA                     
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty Release.gpg                                   
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Translation-en_ZA       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_ZA    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_ZA  
Ign [http://apt.tt-solutions.com](http://apt.tt-solutions.com) gusty Release                                    
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release                                 
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty Release                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_ZA              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                       
Ign [http://apt.tt-solutions.com](http://apt.tt-solutions.com) gusty/main Packages                              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages                
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages
Err [http://apt.tt-solutions.com](http://apt.tt-solutions.com) gusty/main Packages
  404 Not Found
Ign [http://lgp203.free.fr](http://lgp203.free.fr) gusty/universe Sources
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty/main Translation-en_ZA
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty Release                                       
Err [http://lgp203.free.fr](http://lgp203.free.fr) gusty/universe Sources                                 
  404 Not Found
Ign [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty/main Packages                                 
Err [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gusty/main Packages                                 
  404 Not Found
Fetched 1B in 9s (0B/s)                                                          
Failed to fetch [http://apt.tt-solutions.com/ubuntu/dists/gusty/main/binary-i386/Packages.gz](http://apt.tt-solutions.com/ubuntu/dists/gusty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://lgp203.free.fr/ubuntu/dists/gusty/universe/source/Sources.gz](http://lgp203.free.fr/ubuntu/dists/gusty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://apt.wxwidgets.org/dists/gusty/main/binary-i386/Packages.gz](http://apt.wxwidgets.org/dists/gusty/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



It seems as if the repositories are down or don't support Gusty?

Giving up on that I downloaded from this site:
[http://lgp203.free.fr/pool/codeblocks/](http://lgp203.free.fr/pool/codeblocks/)
following these instructions:
[http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)


Notice the wxwidget version required - that is why I thought to download the latest version of wxwidgets. That installed fine.

Now when I try to install the downloaded deb:

>  sudo dpkg -i codeblocks-dbg_1.0svn4750_i386.deb  
[sudo] password for rudolf:
Selecting previously deselected package codeblocks-dbg.
(Reading database ... 214481 files and directories currently installed.)
Unpacking codeblocks-dbg (from codeblocks-dbg_1.0svn4750_i386.deb) ...
dpkg: dependency problems prevent configuration of codeblocks-dbg:
 [COLOR="Red"]codeblocks-dbg depends on codeblocks; however:
  Package codeblocks is not installed.[/COLOR]
dpkg: error processing codeblocks-dbg (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks-dbg


This sounds like I need codeblocks to install codeblocks!? Either I'm doing something really stupid or I'm missing something obvious? 

Thanks again for the reply!

Rudolf

---

### Post by RudolfMDLT on 2008-01-10
Just downloaded another Codeblocks archive from a random link in the CodeBlocks Forum:
[http://forums.codeblocks.org/index.php/topic,7572.30.html](http://forums.codeblocks.org/index.php/topic,7572.30.html)
[http://prdownload.berlios.de/codeblocks/CB_20070907_rev4439_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070907_rev4439_Ubuntu6.10+7.04_wx2.8.4.tar.gz)

And it works.... :) 

I still wish I could figger out what the heck I am doing wrong with the SVN apt repo's!!!!??? 

Thanks for your time on the matter taurus, sorry if I wasted it. Can you by looking at my terminal output see whether I'm doing something blatantly wrong?

---

### Post by pasgui on 2008-01-18
Hi,

> 
Failed to fetch [http://lgp203.free.fr/ubuntu/dists/gusty/universe/source/Sources.gz](http://lgp203.free.fr/ubuntu/dists/gusty/universe/source/Sources.gz) 404 Not Found


I think you make an error in source.list file, you wrote **gusty** instead of **gutsy**.

Regards, pasgui

---

### Post by RudolfMDLT on 2008-02-03
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ]

...

thanks - I'll see if that works! :)

---

