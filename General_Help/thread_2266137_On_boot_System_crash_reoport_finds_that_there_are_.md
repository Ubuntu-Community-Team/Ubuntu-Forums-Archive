---
title: "On boot System crash reoport finds that there are obsolete packages"
date: 2015-02-20
forum: General Help
---

### Post by Neill_R on 2015-02-20
Hi

I have Ubuntu server 14.04.2 L.T.S. installed and have the Lubuntu-desktop installed on top. 

While I see system-update running and telling me my system is up to dat upon boot I still (sometimes) get a crash report telling me that there obsolete packages. 

This is fixed easily by


 ```

sudo apt-get update
sudo apt-get upgrade

```

```

Hit http://security.ubuntu.com trusty-security/universe Translation-en    
Fetched 627 kB in 9s (64.7 kB/s)                                               
Reading package lists... Done
neill@ubuntu-Server:~$ [COLOR=#ff0000]sudo apt-get upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files bsdutils libblkid1 libmount1 libnss3 libnss3-1d libnss3-nssdb
  libuuid1 libuuid1:i386 mount util-linux uuid-runtime
12 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 1,951 kB of archives.
After this operation, 6,144 B of additional disk space will be used.
Do you want to continue? [Y/n] Y


```


I would like to ask the following questions to increase my understanding of the "updating" process.

[LIST=1]
[*]If my system is up to date then how come the packages like those list above become obsolete and require upgrading? 
[*]Is it that the system update is only doing the lubuntu packages and does not realise there are server packages? 
[*]Have i misset the updating process in some way? 
[/LIST]


[IMG]https://neill-rutherford.co.uk/images/software-updater.jpg[/IMG]

---

### Post by v3.xx on 2015-02-20
> I still (sometimes) get a crash report

Could this be apport?

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by Neill_R on 2015-02-20
yes i beleive you are correct saying it comes via apport

---

### Post by v3.xx on 2015-02-20
Apport can be reset by removing the crash reports in /var/crash/.

---

### Post by Neill_R on 2015-02-20
NO sorry that is not the way I want this thread to go please re-read my questions. Once I have sudo apt-get upgrade I do not get a further system crash messages about the now non-obsolete but upgraded packages. But based on my exerience sometime in the future "other" packages will become obsolete

---

### Post by Neill_R on 2015-02-20
from the crash report in the /var/crash folder

'''
 No symbol table info available.
Title: lxpanel crashed with SIGABRT in plugin_start()
UnreportableReason:
 You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:
 
 libblkid1, libmount1, libuuid1, mount, util-linux, uuid-runtime
UpgradeStatus: No upgrade log present (probably fresh install)
_MarkForUpload: True

---

