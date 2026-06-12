---
title: "Understanding installation error codes"
date: 2013-10-18
forum: General Help
---

### Post by volkerbradley on 2013-10-18
Hi,
I installed software and received the following error codes:
"Setting up icaclient (12.1.0) ...
dpkg: error processing icaclient (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 icaclient
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Where does one look to see what the errors are?

---

### Post by ibjsb4 on 2013-10-18
Since I do not run icaclient, this means nothing to me, but it may to you.

> This installation will likely throw the following error: 
dpkg: error processing icaclient (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing: icaclient

This can be resolved by changing line 2648 in /var/lib/dpkg/info/icaclient.postinst:          
echo $Arch|grep "i[0-9]86" >/dev/null

to:
echo $Arch|grep -E "i[0-9]86|x86_64" >/dev/nullThen execute the following command: 
sudo dpkg --configure icaclient

[https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_Receiver_12.1_on_Ubuntu_13.04_64-bit](https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_Receiver_12.1_on_Ubuntu_13.04_64-bit)

---

### Post by volkerbradley on 2013-10-18
> **ibjsb4 said:**
> Since I do not run icaclient, this means nothing to me, but it may to you.



[https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_Receiver_12.1_on_Ubuntu_13.04_64-bit](https://help.ubuntu.com/community/CitrixICAClientHowTo#Citrix_Receiver_12.1_on_Ubuntu_13.04_64-bit)

Perfect!  Problem solved.
Thank you very much.

---

