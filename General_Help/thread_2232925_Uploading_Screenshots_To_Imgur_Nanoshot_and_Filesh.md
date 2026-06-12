---
title: "Uploading Screenshots To Imgur: Nanoshot and Fileshare Applet (Xubuntu 14.04)"
date: 2014-07-05
forum: General Help
---

### Post by Kirkx on 2014-07-05
I'm trying to figure out how to quickly upload screenshots to my Imgur account. I have found two small applications that are supposed to do just that but as a Linux newbie I don't know how to install them on Xubuntu 14.04.

1) Fileshare Applet

[http://aikikode.github.io/fileshare/](http://aikikode.github.io/fileshare/)

According to Readme file and their website you are supposed to "run" file ./build_deb.sh. The file is on my hard drive:

[http://i.imgur.com/CsRMMhc.png](http://i.imgur.com/CsRMMhc.png)

but when I try to run it from Terminal I get "command not found":

[http://i.imgur.com/mckAC7b.png](http://i.imgur.com/mckAC7b.png)

[http://i.imgur.com/WzkODq6.png](http://i.imgur.com/WzkODq6.png)

2) Nanoshot

[http://nanoshot.sourceforge.net/](http://nanoshot.sourceforge.net/)

I run the first command as instructed:

sudo add-apt-repository ppa:nanoshot/ppa

so far so good:

[http://i.imgur.com/QXWU0KK.png](http://i.imgur.com/QXWU0KK.png)

[http://i.imgur.com/Z8e9xPa.png](http://i.imgur.com/Z8e9xPa.png)

but the second command results in error messages:

sudo apt-get update

[http://i.imgur.com/NISbTeE.png](http://i.imgur.com/NISbTeE.png)

3) When I googled the subject of screenshot uploading I have also come across Shutter and MediaFire Express. At present Shutter only supports uploading to Imgur as a guest (so the images probably won't last long on the server and you end up with dead links). MediaFire Express, on the other hand, has download links for Ubuntu but they take you to Windows versions.

[http://shutter-project.org/](http://shutter-project.org/)

[https://www.mediafire.com/software/express/tour.php](https://www.mediafire.com/software/express/tour.php)

Another two uploaders are listed below but the installation seems a bit complicated:

[https://github.com/jomo/imgur-screenshot](https://github.com/jomo/imgur-screenshot)

[https://github.com/ceryn/img](https://github.com/ceryn/img)

---

### Post by Toz on 2014-07-05
Hello and welcome to the forums.

> **Kirkx said:**
> 
1) Fileshare Applet

[http://aikikode.github.io/fileshare/](http://aikikode.github.io/fileshare/)

According to Readme file and their website you are supposed to "run" file ./build_deb.sh. The file is on my hard drive:

[http://i.imgur.com/CsRMMhc.png](http://i.imgur.com/CsRMMhc.png)

but when I try to run it from Terminal I get "command not found":

[http://i.imgur.com/mckAC7b.png](http://i.imgur.com/mckAC7b.png)

[http://i.imgur.com/WzkODq6.png](http://i.imgur.com/WzkODq6.png)


The reason why you are getting a "command not found" error is because in Linux, unlike Windows, the current directory isn't necessarily in your PATH variable, meaning that it isn't searched for the command that you are trying to execute. You need to specify the path. The command would be:
```
./build_deb.sh
```
...the "./" meaning 'current directory'.

The complete set of commands to build and install Fileshare are (starting in the directory that build_deb is in):
```
./build_deb.sh
sudo dpkg -i indicator-fileshare-0.5.2.deb
```
You will then find Fileshare in the Accessories sub-menu.

---

### Post by Kirkx on 2014-07-06
Thanks for your reply.

1) When I try to run:

./build_deb.sh

I get "fakeroot: command not found":

[http://i.imgur.com/GsDgMNF.png](http://i.imgur.com/GsDgMNF.png)

[http://i.imgur.com/cCaPVh4.png](http://i.imgur.com/cCaPVh4.png)

2) What is "0.5.2.deb" in the code provided in the post above?

./build_deb.sh
sudo dpkg -i indicator-fileshare-0.5.2.deb

My Fileshare version is actually v0.2.2-29, as indicated by the original zip file name:

aikikode-fileshare-v0.2.2-29-gf94ae6c.zip

---

### Post by Toz on 2014-07-06
> **Kirkx said:**
> 
1) When I try to run:

./build_deb.sh

I get "fakeroot: command not found":

[http://i.imgur.com/GsDgMNF.png](http://i.imgur.com/GsDgMNF.png)

[http://i.imgur.com/cCaPVh4.png](http://i.imgur.com/cCaPVh4.png)
You need to have **build-essential** installed to compile any packages:
```
sudo apt-get install build-essential
```

> 2) What is "0.5.2.deb" in the code provided in the post above?

./build_deb.sh
sudo dpkg -i indicator-fileshare-0.5.2.deb

My Fileshare version is actually v0.2.2-29, as indicated by the original zip file name:

aikikode-fileshare-v0.2.2-29-gf94ae6c.zip
After you run build_dep, that is the name of the deb file that is created for installation. The 0.5.2 is the version that is extracted from the indicator-fileshare executable in the zip file during the build process. I'm don't know why the versions don't match.

---

### Post by Kirkx on 2014-07-11
Thanks, I have installed Fileshare and it works like a charm. A few questions.

1) The original zip file is named:

aikikode-fileshare-v0.2.2-29-gf94ae6c.zip

and after unzipping the new directory is named:

aikikode-fileshare-f94ae6c

Can it be manually renamed just to:

fileshare

2) I have installed Fileshare in a directory on my "test" partition so I'm going to re-install it.

a) how to remove existing package

sudo dpkg --remove indicator-fileshare-0.5.2.deb
# or
sudo dpkg --purge indicator-fileshare-0.5.2.deb

I guess --purge is equivalent of "mark for complete removal" in Synaptic. Is it actually better to remove the package using the Terminal instead of Synaptic, or is it the same thing?

[http://i.imgur.com/8BJs5f4.png](http://i.imgur.com/8BJs5f4.png)

b) what would be the proper place to unzip the fileshare package to, to follow the "best practice" and filesystem hierarchy. Would this be:

/opt/

This seems to be the directory where all third party (non-distro) applications should be placed in.

3) Is there a parameter available that allows assigning a hotkey, like Shift+Print, to start Fileshare applet and automatically go to "select screen area to grab", so that you don't need to click on Fileshare icon in the system tray:

indicator-fileshare -xyz_parameter_here

[http://i.imgur.com/XJFRplh.png](http://i.imgur.com/XJFRplh.png)

---

### Post by Toz on 2014-07-11
> 1) The original zip file is named:

aikikode-fileshare-v0.2.2-29-gf94ae6c.zip

and after unzipping the new directory is named:

aikikode-fileshare-f94ae6c

Can it be manually renamed just to:

fileshare

This is just the distribution uncompressed filename. You can rename if you like.

> 2) I have installed Fileshare in a directory on my "test" partition so I'm going to re-install it.

> a) how to remove existing package

sudo dpkg --remove indicator-fileshare-0.5.2.deb
# or
sudo dpkg --purge indicator-fileshare-0.5.2.deb

I guess --purge is equivalent of "mark for complete removal" in Synaptic. Is it actually better to remove the package using the Terminal instead of Synaptic, or is it the same thing?

[http://i.imgur.com/8BJs5f4.png](http://i.imgur.com/8BJs5f4.png)
I've never used synaptic so I can't comment on it. Both --remove and --purge will uninstall the package. --purge will also remove any system configuraion files.

> b) what would be the proper place to unzip the fileshare package to, to follow the "best practice" and filesystem hierarchy. Would this be:

/opt/

This seems to be the directory where all third party (non-distro) applications should be placed in.
The fileshare package is just a temporary package. When you install the package, the files get installed to the local filesystem. To see where they are installed:
```
dpkg -L indicator-fileshare
```
Best to leave the install files where they are. You can delete the aikikode-fileshare-f94ae6c directory after you have installed the package as it is no longer required.


> 3) Is there a parameter available that allows assigning a hotkey, like Shift+Print, to start Fileshare applet and automatically go to "select screen area to grab", so that you don't need to click on Fileshare icon in the system tray:

indicator-fileshare -xyz_parameter_here

[http://i.imgur.com/XJFRplh.png](http://i.imgur.com/XJFRplh.png)
Reviewing the code (its written in python) at /usr/local/bin/indicator-fileshare, it doesn't look like it supports parameters. You may wish to submit an enhancement request with the fileshare developers for this functionality.

---

