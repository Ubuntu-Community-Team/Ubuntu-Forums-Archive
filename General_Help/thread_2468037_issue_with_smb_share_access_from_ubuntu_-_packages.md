---
title: "issue with smb share access from ubuntu - packages held back after 20.04 upgrade"
date: 2021-10-16
forum: General Help
---

### Post by fr33z0n3r on 2021-10-16
Any ideas on how I should fix this issue, which appeared after I upgraded from 18.04 to 20.04?  I'm not very savvy with raw package management.  I appear to have previously (while on 18.04) tried to use a third party repo to solve access to newer python versions.

I'm guessing that this was present in my sources with bionic during the 20.04 upgrade.
```
http://ppa.launchpad.net/deadsnakes/ppa/ubuntu 
```


```
~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdb gir1.2-peas-1.0 libpeas-1.0-0 libsmbclient libwbclient0 samba-libs
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```


If I try to upgrade these they complain about python3.8 packages as below:

```
The following packages have unmet dependencies:
 libpython3.8 : Depends: libpython3.8-stdlib (= 3.8.10-0ubuntu1~20.04.1) but 3.8.12-1+bionic1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Any help is appreciated.

---

### Post by monkeybrain20122 on 2021-10-16
Well it looks like you have installed some packages from bionic and it breaks compatibility. What I don't get is how does bionic have python 3.8.12, do you use a ppa for bionic for some reasons?

---

### Post by fr33z0n3r on 2021-10-16
I had come from bionic.  And yes, I think some python script required 3.8+ so this 3rd party repo ppa was the only option I understood.

deadsnakes ppa in particular

---

### Post by monkeybrain20122 on 2021-10-16
You should use ppa-purge to purge the deadsnake ppa then your problem will be resolved. If you need a different version of python use something like [conda]("https://docs.conda.io/en/latest/"), it is a always a bad idea to mess with system's python.

---

### Post by fr33z0n3r on 2021-10-16
That has left me with a few packages still.  I can't recall if there was another source I added in that might do something related to SMB.  From the list I can see of disabled sources, none of them ring a bell.

[IMG]https://i.imgur.com/UIpAXB8.png[/IMG]

I've run autoremove already

```
~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gtksource-4 libamtk-5-0 libamtk-5-common libavdevice57 libavfilter6 libavformat57 libavresample3 libdc1394-22 libfdk-aac1 libluajit-5.1-2 libluajit-5.1-common libmbedcrypto1 libmbedcrypto3
  libmbedtls10 libmbedx509-0 libmysofa0 libopenal-data libopenal1 libpostproc54 libsndio7.0 libswscale4 libtepl-4-0
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libsmbclient libwbclient0 samba-libs
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by fr33z0n3r on 2021-10-18
I found this post,  and the user said they performed the following.  I have just done this for my 3.8 version and it got me past the dependencies issues.  

[https://askubuntu.com/questions/1066823/how-can-i-remove-python-3-6-installed-from-deadsnakes-ppa-after-upgrade-to-ubunt](https://askubuntu.com/questions/1066823/how-can-i-remove-python-3-6-installed-from-deadsnakes-ppa-after-upgrade-to-ubunt)

Any particular concerns with performing this fix?

```
sudo dpkg --remove --force-depends python3.8 python3.8-minimal libpython3.8-minimal libpython3.8-stdlib
sudo apt-get install python3.8 python3.8-minimal libpython3.8-minimal libpython3.8-stdlib
```



I've still not rebooted since making this change.  But there are no longer any package update issues listed.

---

### Post by fr33z0n3r on 2021-10-19
That last change did fix the broken packages shown,but didn't fix my ultimate issue - which is that SMB share access was fully broken. As it turns out the issues above had led to uninstallation or breakage of some SMB related libraries.

This post has my fix, which was to reinstall gvfs-backends **and reboot**

[https://askubuntu.com/questions/1038205/is-it-possible-to-restore-a-missing-gvfsd-smb-file](https://askubuntu.com/questions/1038205/is-it-possible-to-restore-a-missing-gvfsd-smb-file)


**fix:**

```
  sudo apt install --reinstall gvfs-backends
```

---

