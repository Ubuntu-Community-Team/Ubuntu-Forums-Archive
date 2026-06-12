---
title: "How To Upgrade To Latest Nemo (4.0.x) Under Ubuntu 18.04 LTS?"
date: 2019-02-04
forum: General Help
---

### Post by rebeltaz on 2019-02-04
Any idea how to update to 4.0.x under Ubuntu 18.04? 3.6.x is the latest version in the repository and when I try to install the [http://ppa.launchpad.net/webupd8team/nemo/ubuntu](http://ppa.launchpad.net/webupd8team/nemo/ubuntu) PPA, I get this:

```
Err:8 http://ppa.launchpad.net/webupd8team/nemo/ubuntu bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                
E: The repository 'http://ppa.launchpad.net/webupd8team/nemo/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by again? on 2019-02-04
Andrew, from webupd8 has been inactive for well over a year.
You can update using this ppa.

I would add the ppa and then install nemo to pull in only what's needed
and then disable the ppa.
```
sudo add-apt-repository ppa:trebelnik-stefina/cinnamon
sudo apt install nemo
```

Then disable the ppa...
```
software-properties-gtk --open-tab 1
```


Any trouble, install and use ppa-purge to return to ubuntu default packages.
Before using ppa-purge you must re-enable the trebelnik-stefina ppa and then run...
```
sudo ppa-purge ppa:trebelnik-stefina/cinnamon
```
[**HOW TO USE A LAUNCHPAD PPA (ADD, REMOVE, PURGE, DISABLE) IN UBUNTU**]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

I upgraded nemo in Xubuntu 18.04.

---

### Post by rebeltaz on 2019-02-11
I tried this tonight and it seemed to work great. But... when I rebooted the laptop, it kept cycling as if it were stuck in a reboot loop - it would load the BIOS startup screen, go black and reboot. It did this until I turned the computer off and then back on again. Then, it loaded the Ubuntu-colored background but then went to a black screen and threw up this error:

```

error: attempt to read or write outside of disk 'hd0'
Press any key to continue...

```

When I first saw it, well... I did what it said and pressed a key. After a minute, it finally loaded Ubuntu and everything seemed ok. I rebooted again, just to see what was what and this time, I was going to take a picture of the screen. While I was getting my camera, the computer went ahead and booted past that without my having to press any key. 

I did a search on that error and it seems to be a grub issue, but since I am not well verse in grub issues, I don't want to screw it up worse by not knowing what I am doing. Any idea what went wrong and how to fix it? I didn't know if I should try your "if anything goes wrong" suggestion for this issue or not. Nemo upgraded fine, by the way :)

---

