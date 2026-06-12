---
title: "How To - Apachetop Install Dapper 6.06 LTS"
date: 2007-07-04
forum: General Help
---

### Post by Wasca on 2007-07-04
Hi All

If your reading this I bet your apachetop install is not working right?

Well good news I worked out how to get it working. It appears the portmap package is not installed with a default Dapper 6.06 LTS install, that's what's missing. Apachetop uses fam and fam uses portmap.

This is the scenario, you have installed Ubuntu Dapper 6.06-LTS and installed apachetop but it's not working. 

The following commands assume you are running as root, if your not you will need to type sudo in front of all the commands e.g. **sudo apt-get install apachetop**

1. Uninstall fam

```
root@server1:# apt-get remove fam
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apachetop fam
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 365kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 18585 files and directories currently installed.)
Removing apachetop ...
Removing fam ...
 * Stopping file alteration monitor...
   ...done.
```

This should remove apachetop also

2. Install Portmap

```
root@sserver1:# apt-get install portmap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  portmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.0kB of archives.
After unpacking 147kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com dapper/main portmap 5-16ubuntu2 [30.0kB]
Fetched 30.0kB in 2s (10.8kB/s)         
Preconfiguring packages ...
Selecting previously deselected package portmap.
(Reading database ... 18572 files and directories currently installed.)
Unpacking portmap (from .../portmap_5-16ubuntu2_i386.deb) ...
Setting up portmap (5-16ubuntu2) ...
 * Starting portmap daemon...
   ...done.
```

3. Install Apachetop

```
root@sserver1:# apt-get install apachetop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  fam
The following NEW packages will be installed:
  apachetop fam
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/97.8kB of archives.
After unpacking 365kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package fam.
(Reading database ... 18567 files and directories currently installed.)
Unpacking fam (from .../fam_2.7.0-8ubuntu1_i386.deb) ...
Selecting previously deselected package apachetop.
Unpacking apachetop (from .../apachetop_0.12.5-7_i386.deb) ...
Setting up fam (2.7.0-8ubuntu1) ...
 * Starting file alteration monitor...
   ...done.

Setting up apachetop (0.12.5-7) ...
```

4. By defualt apachetop looks at /var/log/apache/access.log. To get apachetop to work with apache2 simply run the command like so

```
root@server1:/# apachetop -f /var/log/apache2/access.log
```

5. Now if you still don't get any updates happening when you run this, make sure apache2 is updating the access.log. I needed to add the following line to my /etc/apache2/apache2.conf file to get the logging to work.

```
# Global access log
CustomLog /var/log/apache2/access.log combined.
```

Then reload the apache2 config and all should work.

I'm going to write a short script file that will simply run the modified apachetop command when I try to execute apachetop.

OK, I wrote a very basic script file that runs apachetop with the correct access log. I saved this file in the /usr/sbin folder as apachetop (/usr/sbin/apachetop). I also renamed the original apachetop executable in the folder to apache2top, this is so I could call my script apachetop (it's what we all remember). Here it is below.

```
#!/bin/bash
# Written by Wasca 04/07/2007
# This script runs apachetop with -f variable so it can use the apache2 access log
# I have renamed the apachetop executable to apache2top so I can call this file apachetop (which is the command everyone remembers)

apache2top -f /var/log/apache2/access.log

```

Make sure you set the files permissions to 755

chmod 755 apachetop


I hope this helps someone else.

---

