---
title: "Synaptic Package Manager error while updating packages."
date: 2013-03-28
forum: General Help
---

### Post by rajukakani on 2013-03-28
Hello All,
This is Raju here. I have a problem in updating the packages.
Could you please have a look & help in this regard.

System --> Administration --> Synaptic Package Manager
Settings --> Repositories --> Download from 
Other --> Korea, Republic of --> kr.archive.ubuntu.com
Download from Server for Korea, Republic of 
Reload ( I tried with Main Server as well)  

I am getting the following error.
/*******************************************************************************************************************************
E: linux-image-2.6.32-41-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-42-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-43-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-44-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-46-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-headers-2.6.32-41-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-2.6.32-42-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-2.6.32-43-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-2.6.32-44-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-2.6.32-46-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-generic: dependency problems - leaving unconfigured
****************************************************************************************************************************/

It would be great & appreciate, if some one provide us their valuable inputs.

Thanx & Regards
Raju

---

### Post by slickymaster on 2013-03-28
It seems that **linux-image-generic** is not set up properly on your system, which means that apt won't be able to install/update/configure any other kernels as well. Run the following at a terminal window:
```
sudo apt-get install linux-image-generic
```
```
sudo apt-get -f install
```

---

### Post by rajukakani on 2013-03-28
I am getting the following errors If I run sudo apt-get install linux-image-generic

/**********************************************************************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libdb-je-java junit4 libaccess-bridge-java libecj-java realpath libdb4.7-java eclipse-platform-data libgcj-bc
  gcj-4.4-base libjtidy-java libicu4j-java eclipse-rcp libservlet2.4-java libcommons-beanutils-java junit
  gcj-4.4-jre-lib libcommons-logging-java libcommons-compress-java libgcj10 libaccess-bridge-java-jni default-jdk
  libjsch-java jarwrapper default-jre libxt-dev sat4j libcommons-el-java libservlet2.5-java libcommons-httpclient-java
  libslf4j-java libasm3-java libregexp-java libwxbase2.8-dev fastjar libjasper-java ant-optional-gcj
  libcommons-codec-java libhamcrest-java liblucene2-java libequinox-osgi-java libcommons-collections3-java
  libgcj-common wx2.8-headers openjdk-6-jdk ant-gcj libcommons-digester-java libjetty-java libjline-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-46-generic (2.6.32-46.105) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-46-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-46-generic
Found initrd image: /boot/initrd.img-2.6.32-46-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-46-generic /boot/vmlinuz-2.6.32-46-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-46-generic /boot/vmlinuz-2.6.32-46-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-46-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-46-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-46-generic; however:
  Package linux-image-2.6.32-46-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.46.53); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-46-generic (2.6.32-46.105) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                            Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-46-generic /boot/vmlinuz-2.6.32-46-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-46-generic /boot/vmlinuz-2.6.32-46-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-46-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-46-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-46-generic; however:
  Package linux-headers-2.6.32-46-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
    Errors were encountered while processing:
 linux-image-2.6.32-46-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-46-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by slickymaster on 2013-03-28
Alright, try to run:
```
sudo dpkg --unpack linux-image-generic
```
If you come across an error saying that there's no such package, chose a download mirror from [here]("http://packages.ubuntu.com/lucid-updates/i386/linux-image-generic/download") to download it (this is an example for a european mirror):
```
wget http://ubuntu.mirror.cambrium.nl/ubuntu//pool/main/l/linux-meta/linux-image-generic_2.6.32.46.53_i386.deb
```
After completing the download just run:
```
sudo dpkg -i path/to/the/downloaded/package/
```

---

### Post by rajukakani on 2013-03-28
First of all thank you very much for your kind reply.
I am Sorry unfortunately I am still facing the following issue when I run
"sudo dpkg -i path/to/the/downloaded/package/" ( I don't understand this command, is it something we should provide real path name ?)

Error:
dpkg: error processing path/to/the/downloaded/package/ (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 path/to/the/downloaded/package/

---

### Post by plucky on 2013-03-29
> I am Sorry unfortunately I am still facing the following issue when I run
"sudo dpkg -i path/to/the/downloaded/package/" ( I don't understand this command, is it something we should provide real path name ?)

Yes

The **wget** command should have downloaded the file **linux-image-generic_2.6.32.46.53_i386.deb** to whichever directory you were in when you issued the command,most likely you /home directory.

Open a terminal and type ```
ls -l
``` lowercase L not a 1, and see if you can see the file.

If you can then type ```
sudo dpkg -i linux-image-generic_2.6.32.46.53_i386.deb
``` and it should install it.See if that fixes the problem.

Good Luck

---

