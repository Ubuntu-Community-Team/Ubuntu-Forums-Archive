---
title: "update manager error"
date: 2013-12-18
forum: General Help
---

### Post by DeepBlunder on 2013-12-18
I am experiencing a problem with the update manager. The recommended update /proc system utilitles fails to install. 

[ATTACH=CONFIG]248704[/ATTACH][ATTACH=CONFIG]248705[/ATTACH]

Here are the details of the error:
```
installArchives() failed: Setting up procps (1:3.2.8-11ubuntu6.1) ...  
 start: Job failed to start  
 invoke-rc.d: initscript procps, action "start" failed.  
 dpkg: error processing procps (--configure):  
  subprocess installed post-installation script returned error exit status 1  
 No apport report written because MaxReports is reached already  
 dpkg: dependency problems prevent configuration of apport-gtk:  
  apport-gtk depends on procps; however: 
   Package procps is not configured yet. 
 dpkg: error processing apport-gtk (--configure):  
  dependency problems - leaving unconfigured  
 No apport report written because MaxReports is reached already  
 Errors were encountered while processing:  
  procps  
  apport-gtk  
 Error in function:  
 Setting up procps (1:3.2.8-11ubuntu6.1) ...  
 start: Job failed to start  
 invoke-rc.d: initscript procps, action "start" failed.  
 dpkg: error processing procps (--configure):  
  subprocess installed post-installation script returned error exit status 1  
 dpkg: dependency problems prevent configuration of apport-gtk:  
  apport-gtk depends on procps; however: 
   Package procps is not configured yet. 
 dpkg: error processing apport-gtk (--configure):  
  dependency problems - leaving unconfigured  

```
Any assistance would be appreciated.
Ubuntu 12.04 LTS
AMD A6-3500 APU with Radeon(tm) HD Graphics × 3 
32-bit

---

### Post by papibe on 2013-12-18
Hi DeepBlunder.

Did you install SpiderOak?

If so, could you open a terminal run this command and post back its output?
```
tail -n2 /etc/sysctl.d/30-spideroak.conf | od -a
```
Regards.

---

### Post by DeepBlunder on 2013-12-18
I have installed SpiderOak.

The output for the terminal command is:
```
0000000   f   s   .   i   n   o   t   i   f   y   .   m   a   x   _   u
0000020   s   e   r   _   w   a   t   c   h   e   s  sp   =  sp   6   5
0000040   5   3   6
0000043
```

Regards,

---

### Post by papibe on 2013-12-18
Thanks.

It looks like that particular file has brought the same error for several people. It is missing a 'newline'  character at the end.

You could fix it yourself by opening a terminal and running:
```
gksudo gedit /etc/sysctl.d/30-spideroak.conf
```
Go to the end of the file, press enter and the end of the last line, and save the file. To make sure it is fixed. Run the 'tail' command again. Now it should be one or two new lines at the end ([FONT=Courier New]nl[/FONT]).

Then restart your computer and try updating your computer again.

Let us know how it went.
Regards.

---

### Post by DeepBlunder on 2013-12-18
Awesome. That did the trick. Thanks very much for the help.

---

