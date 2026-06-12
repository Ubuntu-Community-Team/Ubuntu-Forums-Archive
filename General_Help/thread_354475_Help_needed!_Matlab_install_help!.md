---
title: "Help needed! Matlab install help!"
date: 2007-02-06
forum: General Help
---

### Post by kleinsun on 2007-02-06
Dear guys,

I am a newbie to ubuntu (switched from Red Hat yesterday). My admin helped me to install matlab license manager. But, this time he refused to do so, simply because he only support redhat system. I would really appreciate any help from you guys.

After the installation, I started the license manager by executing "lmstart" under $matlab/etc. Here is what I got:

kleinsun@sunlap:/usr/local/matlab7/etc$ ./lmstart 
 
Checking license file for local hostname and local hostid . . .
 
    Warning: Your local hostname and a SERVER hostname start with
             the same name, but have different full names. One may
             be the fully qualified version of the other which
             usually should work. Your local lmhostid(s) are:
 
             000f1fb9de35
 
             Your hostname is:  sunlap
 
             The SERVER line is:
 
             -----------------------------------------------
             SERVER sunlap.MYDOMAIN ID=215120 27000
             -----------------------------------------------
 
Best to continue, and see what happens . . .
 
Continue to start up license manager? [y]/n) y
 
Taking down any existing license manager daemons . . .
sort: Warning: "+number" syntax is deprecated, please use "-k number"
 
    Killing license manager daemon processes . . . (sunlap)
 
Killed
    process id =  12750 killed . . . (lmgrd)
    process id =  12751 killed . . . (sh)
    process id =  13679 killed . . . (grep)
    process id =  12749 killed . . . (/bin/sh)
 
Starting license manager . . .
 
    Debug logfile = /var/tmp/lm_TMW.log
 


It looks like I did not setup hostname and domain name correctly. However, I have no idea what is correct. If I execute "matlab", here is what I had:

License Manager Error -16.
Cannot read data from license server
 The license server process appears to be running, but is not
responding.  If this persists, notify the System Administrator.
(The lmgrd and vendor daemon processes should be terminated and restarted.)
Feature:       MATLAB
Hostname:      sunlap.caam.rice.edu
License path:  /usr/local/matlab7/etc/license.dat:/usr/local/matlab7 -
   /etc/*.lic
FLEXlm error:  -16,289.  System Error: 104 "Connection reset by peer"
For further information, refer to the FLEXlm End User Manual,
available at "www.macrovision.com".


For more information, see The MathWorks Support page at
[http://www.mathworks.com/support](http://www.mathworks.com/support) and search for
"license manager error -16"
kleinsun@sunlap:/usr/local/matlab7/etc$ cd
kleinsun@sunlap:~$ /usr/local/matlab7/etc/glnx86/lmgrd start
 0:36:51 (lmgrd) -----------------------------------------------
 0:36:51 (lmgrd)   Please Note:
 0:36:51 (lmgrd) 
 0:36:51 (lmgrd)   This log is intended for debug purposes only.
 0:36:51 (lmgrd)   There are many details in licensing policies
 0:36:51 (lmgrd)   that are not reported in the information logged
 0:36:51 (lmgrd)   here, so if you use this log file for any kind
 0:36:51 (lmgrd)   of usage reporting you will generally produce
 0:36:51 (lmgrd)   incorrect results.
 0:36:51 (lmgrd) 
 0:36:51 (lmgrd) -----------------------------------------------
 0:36:51 (lmgrd) 
 0:36:51 (lmgrd) 
 0:36:51 (lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.13902, errno: 2
license manager: can't initialize: 
For further information, refer to the FLEXlm End User Manual,
available at "www.macrovision.com".
 0:36:51 (lmgrd) Can't remove statfile /usr/tmp/.flexlm/lmgrdl.13902: errno No such file or directory

---

