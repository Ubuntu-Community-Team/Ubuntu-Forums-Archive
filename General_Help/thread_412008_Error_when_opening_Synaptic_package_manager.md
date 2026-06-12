---
title: "Error when opening Synaptic package manager"
date: 2007-04-17
forum: General Help
---

### Post by brentcee23 on 2007-04-17
I try to run synaptic from the terminal and from System>Admin>..... and I keep getting this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I am a big noob, any help would be appreciated. Thanks!

---

### Post by Naatan on 2007-04-17
run 'dpkg --configure -a' perhaps?

---

### Post by brentcee23 on 2007-04-17
thanks for the quick reply, I did the above and it asked to install a flashplugin from adobe and gave me this.

Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

any suggestions now?

---

### Post by Naatan on 2007-04-17
it sounds like another process is interfearing or you installed something but the installation didn't finnish right, did you reboot? If not I'd give that a try and then run the command again..

if you already did that try 

'ps x | grep dpkg'

and kill all running processes fitting that description (kill -9 "pid"), repeat the step for

'ps x | grep synaptic'

then run the command again (dpkg --configure -a)

---

