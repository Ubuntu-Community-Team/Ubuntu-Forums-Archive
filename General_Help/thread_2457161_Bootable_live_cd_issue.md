---
title: "Bootable live cd issue"
date: 2021-01-27
forum: General Help
---

### Post by shyam1287 on 2021-01-27
Hi. I tried booting into live cd for resolving a booting issue. But even though I have sufficient space on my drive still Im unable to install any debian packages. If I click on install the progress just appears for a brief second and vanishes. What might the actual issue be for this?

---

### Post by yancek on 2021-01-27
You're posting at an Ubuntu forum so do you have Ubuntu installed on your computer?  If so which release?  If not, are you trying to install it and again, which release?    How exactly are you trying to install using a 'live' cd to install packags?  You can't install anything on a 'live' cd unless it is persistent and that would not affect an installed system.  You need to post more details on what you are trying to do and how.

---

### Post by shyam1287 on 2021-01-27
I was using the latest version. But I faced some booting issue. So I needed to use a live OS In my usb drive. So currently its in a flash drive (Ubuntu 19.10, eoan). The problem that Im exactly facing is that, if I click on install on any of the softwares listed, it just shows the progress bar for a brief moment and then there is no kind of progress or even a partial installation happening and just again the progress bar disappears and the install button again is appearing as though nothing has really been done.

---

### Post by CelticWarrior on 2021-01-27
Again, > [COLOR=#000000]You can't install anything on a 'live' cd unless it is persistent and that would not affect an installed system.[/COLOR]
You may use a live session to troubleshoot a problem of an installed system and we often ask people to do just that and Boot Repair to create a summary info but this is a very specific usage and it certainly isn't a "click to install" situation.

Which software are you trying to install and for which purpose?

Probably better to describe and ask for help regarding an actual problem you're having instead of what you think is a solution (it clearly isn't).

---

### Post by shyam1287 on 2021-01-28
The actual problem that I face is Im unable to boot. I had tried the nomodeset option by manually editing the grub config. Once I do that change, then as soon as I press ctrl+x, I sometimes get "esetparams command not found". Mostly the system somehow splitted the words nomodeset as maybe nomod+eset. Then its asking to press any key to continue. Then once I continue its starting to print all the systemd services that are enabled and active. They get printed on the prompt indefinitely, without any stop. I tried rescue boot method also. But none of the methods really goto the final GUI screen of the OS. Im currently using foccal fossa for which it is not booting.

---

### Post by CelticWarrior on 2021-01-28
"nomodeset" isn't for such cases and the "system" doesn't split it anyway, users typing it incorrectly do that. Please do not make things worse.

If you are unable to boot we can take a look at it. Do not add any boot parameter to the installed system and boot a live session instead. Make sure you have internet connection in that live session.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Please use the 2nd option to install (temporarily) and run Boot Repair. Do NOT do any repair at this point, just create a summary info and post here the result.

---

### Post by shyam1287 on 2021-01-29
I also tried installing the boot-repair by directly downloading the .deb file (even that doesnt work). My system doesnt install boot-repair by the following method also. I already tried it on the live usb. I get the following output:


ubuntu@ubuntu:~$  sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Ign:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic InRelease
Hit:3 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Err:4 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease                                                                              
Get:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease [15.4 kB]                                                        
Ign:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                          
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security Release                  
  404  Not Found [IP: 2001:67c:1360:8001::23 80]
Ign:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease
Err:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan Release
  404  Not Found [IP: 2001:67c:1360:8001::24 80]
Err:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates Release
  404  Not Found [IP: 2001:67c:1360:8001::24 80]
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu eoan-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu eoan Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu eoan-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

ubuntu@ubuntu:~$  sudo apt-get update
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Ign:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic InRelease
Hit:3 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Err:4 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                                                                                        
Hit:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease                                                                  
Ign:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease                        
Err:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan Release                                  
  404  Not Found [IP: 2001:67c:1360:8001::23 80]
Ign:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Err:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates Release
  404  Not Found [IP: 2001:67c:1360:8001::23 80]
Err:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security Release
  404  Not Found [IP: 2001:67c:1360:8001::24 80]
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) utopic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu eoan Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu eoan-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu eoan-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

ubuntu@ubuntu:~$  sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

ubuntu@ubuntu:~$

---

### Post by ajgreeny on 2021-01-29
There are no repositories for 19.10 easily available to you as it lost support several months ago, and we believed that you were using 20.04; perhaps that is your installed system not the live system you're using?

If there is any way you can get a live version of 20.04 we may be able to proceed more easily but with 19.10 it will be difficult.
You could download the 20.04 iso and use dd to transfer that image to USB, then boot to 20.04 and try again with boot repair.

---

### Post by shyam1287 on 2021-02-15
I tried boot repair. It did not work out.
I also just wanted to know after executing grub.cfg where does the control go. 
Also from which file is grub.cfg called?

Also when do generally errors like failure to mount disks happen?
Something like the following one:

mount[577]: Failed to write lock '/dev/sd': Resource temporarily unavailable
mount[577]: Error opening '/dev/sd': Resource temporarily unavailable
mount[577]: Failed to mount '/dev/sd': Resource temporarily unavailable

---

