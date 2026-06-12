---
title: "sudo apt-get update &amp;&amp; sudo apt-get upgrade behaving odd"
date: 2019-07-31
forum: General Help
---

### Post by sujitsphatak on 2019-07-31
Until this afternoon, I was able to check for new updates with the apt-get update and upgrade commands in a normal manner. However, now I am suddenly seeing messages I didn't see before and the overall update process seems to have slowed down significantly. A brief history with this behavior is I had seen similar behavior at least two times before on both Ubuntu 18.04 and Ubuntu 16.04 (now) and eventually I started facing bootup problems forcing me to wipe and reinstall ubuntu along with my other toolchain. Please see the attachment and let me know your thoughts. Thanks in advance.

---

### Post by ajgreeny on 2019-07-31
Sorry, but I find your screenshot impossible to read, so am not able to help at the present time.

Please copy the text from terminal and paste it (using code tags - See my signature below for a How-to) back here where it will make things a lot easier and give us much more detailed information about what is going on.

---

### Post by jiang765 on 2019-07-31
I met the same problem several days ago. And I fixed it using the method from [https://askubuntu.com/questions/1109982/e-could-not-get-lock-var-lib-dpkg-lock-frontend-open-11-resource-temporari](https://askubuntu.com/questions/1109982/e-could-not-get-lock-var-lib-dpkg-lock-frontend-open-11-resource-temporari)

Hope it can help you as well!

---

### Post by sujitsphatak on 2019-08-01
Sorry about the unclear attachment. Here is the copy pasted log from this morning. I am particularly curious about the lines "gpgv: Good signature from "Ubuntu Archive Automatic Signing Key" <ftpmaster@ubuntu.com>" that repeatedly get printed. This didn't happen earlier. Please see the complete log below.

```
sujitsphatak@XPS13-9333:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for sujitsphatak: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [109 kB]
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                  
0% [1 InRelease gpgv 109 kB] [Connecting to ca.archive.ubuntu.com]gpgv: Signature made Thu Aug  1 08:47:44 2019 EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu Aug  1 08:47:44 2019 EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease        
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [710 kB]
0% [3 InRelease gpgv 247 kB] [Waiting for headers] [4 Packages 5,556 B/710 kB 1%]gpgv: Signature made Thu Apr 21 19:25:09 2016 EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu Apr 21 19:25:09 2016 EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [576 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [73.7 kB]
Get:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]            
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [73.2 kB]      
0% [5 Packages store 0 B] [7 InRelease gpgv 109 kB] [Waiting for headers]gpgv: Signature made Thu Aug  1 09:05:41 2019 EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu Aug  1 09:05:41 2019 EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [450 kB]
Get:10 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]
0% [9 Packages store 0 B] [10 InRelease gpgv 107 kB] [Waiting for headers] [Waiting for headers]gpgv: Signature made Thu Aug  1 06:47:26 2019 EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu Aug  1 06:47:26 2019 EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [391 kB]        
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [183 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [124 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [188 kB] 
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [1,000 kB]      
Get:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [845 kB]
Get:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [324 kB]
Get:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [231 kB]
Get:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [758 kB]
Get:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [692 kB]
Get:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [317 kB]
Get:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [274 kB]
Get:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [405 kB]
Get:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,968 B] 
Get:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]    
Get:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]     
Get:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,104 B] 
Hit:29 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                          
99% [Release.gpg gpgv 943 B]gpgv: Signature made Tue Jul 30 13:54:14 2019 EDT using RSA key ID 997C215E
gpgv: Good signature from "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>"
Fetched 7,972 kB in 4min 0s (33.2 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  usb-creator-common usb-creator-gtk
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

### Post by wildmanne39 on 2019-08-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

