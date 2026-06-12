---
title: "ubuntu without internet"
date: 2008-04-08
forum: General Help
---

### Post by rothot on 2008-04-08
Hello, i have been using Ubuntu for a year but i still have issues with the programs installation.

I'm trying to get Ubuntu to the Math Workshop at the school, in order to do that i have to be able to install some programs. but we don't have internet connection at the Workshop.

I need Apache2, php5, mySQL, sun's JDK and JRE, kile, KDVI and KPDF, Xfig(and transfig), Scilab, Adobe flash player,   

I already tried to install all the programs but i couldn't do it (not a single one!),

Thanks for your time.

George

---

### Post by Jussi Kukkonen on 2008-04-08
Package management works very badly in this case... Take a look here: [http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

That will work if your package lists are up-to-date...
If they are not, and if you happen to have a another ubuntu machine *with exact same sources.list*, you could try this:
1. "apt-get update" on connected machine
2. copy /var/lib/apt/lists/* to the unconnected machine
3. do as instructed in the linked page (start synaptic, mark all software you want and then click "Generate Package Download Script")
4. run the download script on connected machine
5. copy downloaded files to unconnected machine and install

Simple it isn't, but should work.

---

### Post by ibuclaw on 2008-04-08
There are one of several ways to do this.

NOTE:**All** require a **separate Ubuntu PC** with an internet connection. 

First way would be to [create a local copy of the repository where your software is contained.]("http://www.howtoforge.com/dvd_images_of_ubuntu_repositories")
**NOTE**: This requires that you have about 30GB of harddisk space to spare.
And can potentially take up 5 DVDs. But on the up side, if you wish to install further software, you can.


A better way, one that would require less space, would be to do a fresh install of ubuntu on a machine with internet, then do a full upgrade and  then install the packages you wish.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install app1 app2 etc

```
Then install a package called aptoncd
```
 sudo apt-get install aptoncd 
```
Then open it in the menu hierarchy "System>Administration>APTonCD"
Click "create", and all packages that you downloaded will be display in the list to Burn.
So to finalise the process, click on "Burn" and all the packages that **you require** are all burned onto Disc.
**NOTE**: It is recommended that you use a PC with similar hardware and the same architechture.

Then when it you bring it back to the Workshop PC, disable all internet repositories, then use:
```
 apt-cdrom add 
```
To add the newly created DVD/s to the repository. This would have to be done for each CD/DVD.

Then you can use:
```
 apt-get install apache2 
```
for example, and it will ask you to insert the CD/DVD containing that package.

Hope this has been of help to you.

Regards
Iain

[EDIT]
And lastly, if you were to request for permissions from your schoolboard. Then you could take the Workshop PC home with you, or move it to a part of the school that **does** have an internet connection and install everything you need there.

---

### Post by 3rdalbum on 2008-04-08
You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) on your web-enabled machine, and download the apache2 package, and make a note of what packages it depends on. Then go to those pages, and download those packages and what they depend on, etc. Don't download anything that's already on your Ubuntu system.

Transfer the packages to your Ubuntu system, double-click the packages that don't have any dependencies, and install them. Then install the next packages up in the pyramid, and so on and so forth.

It's a slow method and if you forget some packages you can sometimes go back and forth between computers, but at least it's a workable method that doesn't require an Internet-enabled Ubuntu computer.

---

### Post by rothot on 2008-04-09
Thank you all for your help, i hope i can get more people to the linux world soon with this.

Im just have 1 more question...

Where do i get the rest of the programs in the APTonCD?, i only found mySQL


Thanks!!!

---

