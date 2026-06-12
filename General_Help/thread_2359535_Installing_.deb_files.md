---
title: "Installing .deb files"
date: 2017-04-25
forum: General Help
---

### Post by angel mike on 2017-04-25
Cannot install file 'imagescan-bundle-ubuntu-16.04-1.3.19.x86.deb' which contains the driver for the Epson V39 Scanner.
Tried 
sudo dpkg -i 'file name'
and
chmod a+x 'file name'
sudo ./'file name'

Thanks Mike

---

### Post by monkeybrain20122 on 2017-04-25
Normally you just need to click it and it would install (after asking for password). But since gnome-software-center is not working, see this [thread]("https://ubuntuforums.org/showthread.php?t=2359247&p=13636356#post13636356")

See post #3 and #4.

P.S sudo dpkg -i would work if 
1) "filename" is the full path to the file, or alternatively you first cd into the directory where the file is (e.g, if foo is in Downloads, then either 
```
sudo dpkg -i ~/Downloads/foo.deb

```
or 

```
cd ~/Downloads
sudo dpkg -i foo.deb
```

2) all dependencies are satisfied, dpkg does not pull in missing dependencies like gdebi or apt install.

---

### Post by angel mike on 2017-04-27
Thanks monkeybrain20122 for suggestions but get a systems error report (see below) . Could it be that there are dependencies missing - if so how do I determine which ones. 
```

  	 	 	 	   sudo dpkg -i ~/Downloads/imagescan-bundle-ubuntu-16.04-1.3.19.x86.deb
 [sudo] password for michael:  
 dpkg-split: error: error reading /home/michael/Downloads/imagescan-bundle-ubuntu-16.04-1.3.19.x86.deb: Is a directory

 dpkg:../../src/unpack.c:123:deb_reassemble: internal error: unexpected exit status 2 from dpkg-split

 Aborted (core dumped)

```

---

