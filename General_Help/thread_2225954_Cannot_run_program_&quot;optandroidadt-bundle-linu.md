---
title: "Cannot run program &quot;/opt/android/adt-bundle-linux-x86-20140321/sdk/platform-tools/aap"
date: 2014-05-24
forum: General Help
---

### Post by ridah2 on 2014-05-24
hi all,

I have been struggling with this error for two days. I have Ubuntu 3.13.0-24-generic #47-Ubuntu i686. I installed Oracle jdeveloper 11g. Also i installed android sdk for mobile application development. Now the problem i am encountering is when i try to deploy the application

Cannot run program "/opt/android/adt-bundle-linux-x86-20140321/sdk/platform-tools/aapt": java.io.IOException: error=2, No such file or directory
 
total 2148
drwxr-xr-x 4 root root    4096   18 20:58 ./
drwxr-xr-x 9 root root    4096  18 20:16 ../
lrwxrwxrwx 1 root root      25  18 20:58 aapt -> /build-tools/current/aapt
-rwxr-xr-x 1 root root 1231255  18 20:16 adb*
drwxr-xr-x 2 root root    4096   18 20:16 api/
-rwxr-xr-x 1 root root  197710     18 20:16 fastboot*
lrwxrwxrwx 1 root root      24     18 20:58 lib -> /build-tools/current/lib
-rw-r--r-- 1 root root  727881  18 20:16 NOTICE.txt
-rw-r--r-- 1 root root   16648     18 20:16 source.properties
drwxr-xr-x 2 root root    4096   18 20:1systrace/



There is definitely something that i am missing. Also i googled this error and everywhere  i found ia32-libs missing. I have tried to install it but 

sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs


I know that it is obsolete now but there are several other ways to install it. Kindly point out my mistake

---

### Post by oldos2er on 2014-05-24
Moved to General Help.

---

### Post by ridah2 on 2014-05-26
i am getting this error when i try to deploy an android app on ubuntu 12 (32 bit). Kindly help

---

### Post by steeldriver on 2014-05-26
I have merged your threads since the original one has more information

Can you give some more details about how you built the application and what platform you deployed it on? I don't have any experience with the Android SDK, but I imagine that's the kind of thing people will need to know in order to help you.

---

### Post by brantcgardner on 2014-05-27
This is a really common complaint for 64-bit Ubuntu users trying to run 32-bit software that comes from** outside** the Ubuntu repositories.  I ran into it myself for a project and I researched it out of curiosity; what you need is to understand the change to 'multiarch'.

See [this link]("https://help.ubuntu.com/community/MultiArch") for the complete documentation and the steps to find your own dependencies so you can get the relevant 32-bit packages installed.

---

