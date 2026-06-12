---
title: "Cannot Install MS Core Fonts"
date: 2016-11-17
forum: General Help
---

### Post by sccjono on 2016-11-17
Hello all,

Has anyone else had a problem installing the MS Core Fonts? I was getting errors that are talked about [here]("http://askubuntu.com/questions/829247/cannot-install-the-package-ttf-mscorefonts-installer"). But looking at the output now am I right in thinking the files are no longer available?

```

jono@ubuntu1604-1:~$ sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*
jono@ubuntu1604-1:~$ sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 0 not to upgrade.
Need to get 0 B/29.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 384782 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 13s (15.0 kB/s)                                                            
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arial32.exe [554 kB]
Fetched 554 kB in 1s (350 kB/s)                                                         
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arialb32.exe [168 kB]
Fetched 168 kB in 1s (150 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arialb32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
Get:1 http://downloads.sourceforge.net/corefonts/comic32.exe [246 kB]
Fetched 246 kB in 1s (222 kB/s)                                                         
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/comic32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
Get:1 http://downloads.sourceforge.net/corefonts/courie32.exe [646 kB]
Fetched 646 kB in 1s (395 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/courie32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
Get:1 http://downloads.sourceforge.net/corefonts/georgi32.exe [392 kB]
Fetched 392 kB in 1s (344 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/georgi32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
Get:1 http://downloads.sourceforge.net/corefonts/impact32.exe [173 kB]
Fetched 173 kB in 0s (198 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/impact32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
Get:1 http://downloads.sourceforge.net/corefonts/times32.exe [662 kB]
Fetched 662 kB in 1s (431 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/times32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
Err:1 http://downloads.sourceforge.net/corefonts/trebuc32.exe
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch https://netix.dl.sourceforge.net/project/corefonts/the fonts/final/trebuc32.exe  404  Not Found


E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
jono@ubuntu1604-1:~$ 

```

---

### Post by bearlake on 2016-11-17
Just went through this a week a go.

This is what worked for me.

```
sudo dpkg -P ttf-mscorefonts-installer
sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*
sudo apt-get --purge --reinstall install ttf-mscorefonts-installer
```

---

### Post by sccjono on 2016-11-20
Thank you for the reply but I get exactly the same error messages as above. Unless anyone else has a suggestion, I can only assume that the files are no longer available. :-(

jono

---

### Post by howefield on 2016-11-20
If you want to jump through some "hoops" you could try [https://ubuntuforums.org/showthread.php?t=2343669](https://ubuntuforums.org/showthread.php?t=2343669)

Have to say the easiest way seems to be to get a hold of the 3.6 package and install that.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

---

### Post by CantankRus on 2016-11-20
I just installed on 16.04, so files are available.
Get the same message "W: Can't drop privileges for downloading as file" but I believe this is just a warning not an error message.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sudo apt install ttf-mscorefonts-installer**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  cabextract libmspack0
The following NEW packages will be installed:
  cabextract libmspack0 ttf-mscorefonts-installer
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
Need to get 89.2 kB of archives.
After this operation, 362 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ftp.iinet.net.au/pub/ubuntu xenial/main amd64 libmspack0 amd64 0.5-1 [38.2 kB]
Get:2 http://ftp.iinet.net.au/pub/ubuntu xenial/universe amd64 cabextract amd64 1.6-1 [21.4 kB]
Get:3 http://ftp.iinet.net.au/pub/ubuntu xenial/multiverse amd64 ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29.5 kB]
Fetched 89.2 kB in 0s (94.5 kB/s)                   
Preconfiguring packages ...
Selecting previously unselected package libmspack0:amd64.
(Reading database ... 314959 files and directories currently installed.)
Preparing to unpack .../libmspack0_0.5-1_amd64.deb ...
Unpacking libmspack0:amd64 (0.5-1) ...
Selecting previously unselected package cabextract.
Preparing to unpack .../cabextract_1.6-1_amd64.deb ...
Unpacking cabextract (1.6-1) ...
Selecting previously unselected package ttf-mscorefonts-installer.
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 2s (80.3 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arial32.exe [554 kB]
Fetched 554 kB in 3s (184 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arialb32.exe [168 kB]
Fetched 168 kB in 2s (71.3 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arialb32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
Get:1 http://downloads.sourceforge.net/corefonts/comic32.exe [246 kB]
Fetched 246 kB in 2s (105 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/comic32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
Get:1 http://downloads.sourceforge.net/corefonts/courie32.exe [646 kB]
Fetched 646 kB in 3s (206 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/courie32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
Get:1 http://downloads.sourceforge.net/corefonts/georgi32.exe [392 kB]
Fetched 392 kB in 2s (148 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/georgi32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
Get:1 http://downloads.sourceforge.net/corefonts/impact32.exe [173 kB]
Fetched 173 kB in 2s (79.9 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/impact32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
Get:1 http://downloads.sourceforge.net/corefonts/times32.exe [662 kB]
Fetched 662 kB in 3s (188 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/times32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
Get:1 http://downloads.sourceforge.net/corefonts/trebuc32.exe [357 kB]
Fetched 357 kB in 2s (145 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
Get:1 http://downloads.sourceforge.net/corefonts/verdan32.exe [352 kB]
Fetched 352 kB in 2s (142 kB/s)                                                               
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/verdan32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe
Get:1 http://downloads.sourceforge.net/corefonts/webdin32.exe [185 kB]
Fetched 185 kB in 2s (83.5 kB/s)                                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/webdin32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Setting up libmspack0:amd64 (0.5-1) ...
Setting up cabextract (1.6-1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
```

---

### Post by Autodave on 2016-11-20
This fellow helped fix mine awhile ago: you may want to give it a try.


May 4th, 2016                                                                                                                                                                                                     [#9]("https://ubuntuforums.org/showthread.php?t=2323229&p=13483643#post13483643")                                                                                                                                                                                      		

  		 			 				 				 					 						 	[**[COLOR=#000000]QDR06VV9[/COLOR]**]("https://ubuntuforums.org/member.php?u=27449") 	 
 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						I Ubuntu, Therefore, I Am 					 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateJun 2005BeansHidden!                                                     						 					
 					 					 				
 			 		
 	
  	 		 		 		 		[h=2]Re: ttf-mscorefonts-installer won't run/work[/h] 		 				 				 		 			 				[INDENT] 					This bug was reported fixed [https://answers.launchpad.net/ubuntu/+question/290405](https://answers.launchpad.net/ubuntu/+question/290405)

We may have to get rough with it
 	Code:
 	sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/* 
Followed by
 	Code:
 	sudo apt-get --purge --reinstall install ttf-mscorefonts-installer 
 				[/INDENT] 			
  			   		
 			 			 			[INDENT] 				 					Last edited by QDR06VV9; May 4th, 2016 at 06:54 PM. 				 				 					Reason: Add info 				 			
[/INDENT]

---

### Post by bearlake on 2016-11-21
> **Autodave said:**
> This fellow helped fix mine awhile ago: you may want to give it a try.


May 4th, 2016                                                                                                                                                                                                     [#9]("https://ubuntuforums.org/showthread.php?t=2323229&p=13483643#post13483643")                                                                                                                                                                                              

                                                                                                            [**[COLOR=#000000]QDR06VV9[/COLOR]**]("https://ubuntuforums.org/member.php?u=27449")      
                         [IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]                                                                    I Ubuntu, Therefore, I Am                                                                                                                                                                                                                 
                                      
             
                                                   Join DateJun 2005BeansHidden!                                                                                                  
                                                           
                      
     
                                          **Re: ttf-mscorefonts-installer won't run/work**

                                                                                  [INDENT]                     This bug was reported fixed [https://answers.launchpad.net/ubuntu/+question/290405](https://answers.launchpad.net/ubuntu/+question/290405)

We may have to get rough with it
     Code:
     sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/* 
Followed by
     Code:
     sudo apt-get --purge --reinstall install ttf-mscorefonts-installer 
                 [/INDENT]
            
                         
                                       [INDENT]                                      Last edited by QDR06VV9; May 4th, 2016 at 06:54 PM.                                                       Reason: Add info                              
[/INDENT]


Same as post #2

---

### Post by Bucky Ball on 2016-11-21
The easiest way I know is to install 'ubuntu-restricted-extras'. Done.

You'll find it in the official repositories.

---

### Post by sccjono on 2016-11-22
Thank you all so much for your help. All installed and working now.

jono

---

### Post by Bucky Ball on 2016-11-22
That's good, but please share with the community how you fixed it and mark the thread as 'solved' by using Thread Tools at the top right or have a look at the link in my signature.

Thanks and good luck. ;)

---

### Post by texpat on 2016-12-08
You may also be aware of the [thread over at askubuntu.com]("http://askubuntu.com/questions/852302/failure-to-download-extra-data-files-ttf-mscorefonts-installer")

What worked for me was to [download the .deb]("https://packages.debian.org/jessie/all/ttf-mscorefonts-installer/download") package and install it with software center.

---

### Post by bearlake on 2016-12-09
The error has been corrected and updated. A fully updated system should no longer get that error.

---

