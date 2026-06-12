---
title: "I can't seem to successfully install SLPD"
date: 2015-05-20
forum: General Help
---

### Post by mike_m2 on 2015-05-20
Hey everyone!

So I'm trying to install slpd by using the command [FONT=courier new][SIZE=2]*sudo apt-get install slpd*[/SIZE][/FONT] however, before it even has the chance to install, it looks like it's getting hung up just unpacking the package. Below is the output I always seem to get. After I "install" the slpd package, and run an [SIZE=2][FONT=courier new]*aptitude show slpd | grep State*[/FONT][/SIZE] command, It shows that slpd is 'partially configured.' I've tried to uninstall and reinstall it without any luck. If anyone has any suggestions I am all ears because I am not having ANY luck figuring this out.:confused:

Output after I run the command *sudo apt-get install slpd*
```

  	 	 	 	   dependency tree        
 Reading state information... Done 
 Suggested packages: 

   openslp-doc 
 The following NEW packages will be installed: 
   slpd 
 0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded. 
 Need to get 0 B/67.8 kB of archives. 
 After this operation, 187 kB of additional disk space will be used. 
 Selecting previously unselected package slpd. 
 (Reading database ... 194917 files and directories currently installed.) 
 Preparing to unpack .../slpd_1.2.1-9_amd64.deb ... 
 Unpacking slpd (1.2.1-9) ... 
 Processing triggers for ureadahead (0.100.0-16) ... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
 Setting up slpd (1.2.1-9) ... 
 + [ configure = configure ] 
 + dpkg --compare-versions  le 1.2.1-7.6 
 + echo Reinstalling init script for new priorities ... 
 Reinstalling init script for new priorities ... 
 + update-rc.d slpd remove 
 update-rc.d: /etc/init.d/slpd exists during rc.d purge (use -f to force) 
 dpkg: error processing package slpd (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 Processing triggers for ureadahead (0.100.0-16) ... 
 Errors were encountered while processing: 
  slpd 
 E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bashiergui on 2015-05-24
It's a bug that appears unresolved. [https://bugs.launchpad.net/ubuntu/+source/openslp-dfsg/+bug/1047561](https://bugs.launchpad.net/ubuntu/+source/openslp-dfsg/+bug/1047561)

Install it from the tarball.

---

