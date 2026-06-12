---
title: "Ukuu will not install on 19.04"
date: 2019-09-06
forum: General Help
---

### Post by Alex_Rodgers on 2019-09-06
I have a new Lenovo P53. Currently 19.04 is using kernel 5.0.0 so my wifi is not working. In 5.2 the wifi problem is fixed. I need to upgrade my linux kernal, but all the guides I have found say to download ukuu. I add the repo ppa:teejee2008/ppa, run ```
sudo apt-get update
```, and try ```
sudo apt-get install ukuu
```, but I receive: ```
unable to locate package: ukuu
```. Does anyone have any ideas how to fix this, or just manually update my kernel? I couldn't figure out how to manually do it because on the [kernel page]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/") it says "apply the following patches on top in order below. I have no idea how to run patches.

---

### Post by pcfan1234 on 2019-09-06
Have you added the PPA?
Post > ls -la /etc/apt/sources.list.d
There should be a files named like the PPA.
Post the content of that file.

---

### Post by deadflowr on 2019-09-06
Apply the patches refers to if you build the kernel from the git source.
Doesn't apply if you install the .deb packages.

Post back the apt update command.
And How you went about to add the ppa to your system.

Seems like something was missed.

---

### Post by Alex_Rodgers on 2019-09-07
So here are the two commands you wanted run.
```
alex@alex-ThinkPad-P53:~$  ls -la /etc/apt/sources.list.d 
total 8
drwxr-xr-x 1 root root 138 Sep  6 10:27 .
drwxr-xr-x 1 root root 180 Sep  6 10:26 ..
-rw-r--r-- 1 root root 334 Sep  6 10:37 teejee2008-ubuntu-ppa-disco.list
-rw-r--r-- 1 root root 266 Sep  6 10:37 teejee2008-ubuntu-ppa-disco.list.save


```
and
```
alex@alex-ThinkPad-P53:~$ sudo apt-get update
[sudo] password for alex: 
Hit:1 http://us.archive.ubuntu.com/ubuntu disco InRelease
Hit:2 http://security.ubuntu.com/ubuntu disco-security InRelease
Hit:3 http://ppa.launchpad.net/teejee2008/ppa/ubuntu disco InRelease         
Hit:4 http://us.archive.ubuntu.com/ubuntu disco-updates InRelease            
Hit:5 http://us.archive.ubuntu.com/ubuntu disco-backports InRelease
Reading package lists... Done  

```

I added the ppa using this, along with trying to install ukuu
```
sudo apt-add-repository ppa:teejee2008/ppa sudo apt-get update sudo apt-get install ukuu
```

---

### Post by deadflowr on 2019-09-07
Looks like ukuu has moved to paid licensing model.
I also see the last build on launchpad failed, so it never built the deb packages.
(Last build was way back in February)

Announcement of change here:
[https://teejeetech.in/2019/01/20/ukuu-v19-01/#more-483]("https://teejeetech.in/2019/01/20/ukuu-v19-01/#more-483")

---

### Post by mörgæs on 2019-09-08
If you have space for another partition you could also install 19.10 though it is still in development.

---

