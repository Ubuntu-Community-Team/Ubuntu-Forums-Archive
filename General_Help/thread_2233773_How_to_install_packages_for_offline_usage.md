---
title: "How to install packages for offline usage?"
date: 2014-07-10
forum: General Help
---

### Post by thexnightmare on 2014-07-10
Dear,
How can I grab the packages to be able to install them later offline without the need of internet connection everytime?
And does the packages mean the programs in windows world?
Thanks

---

### Post by deadflowr on 2014-07-10
run
```
apt-get download <packagenamehere>
```
this will download the package into your home folder.
then later, you can either move them like any other file, or install them with
```
sudo dpkg -i <packagenamehere>
```

Of course replacing packagenamehere with the actual package name and, if need the path to the package.

If you have a bunch of packages and do not want to have you home folder cluttered, first change into a directory that you would like to have them in.
Personally I would make a directory
```
mkdir Packages-Offline
```
then 
```
cd Packages-Offline
```
Then run the command to download.
The packages will then be saved in that directory, also known as the working directory.

Hope this helps.

---

### Post by Impavidus on 2014-07-10
```
sudo apt-get -d install <package>
#or
sudo apt-get --download-only install <package>
``` should also work. I think it's supposed to store the file in the normal location for these packages (/var/cache/apt/archive/). When installing you can use```
sudo apt-get --no-download install <package>
```

Packages are just any software. Some programs have been divided over several packages (some of which may be optional), some packages contain various related programs (collections of tools), some packages are shared by several programs (libraries) and some packages are meta-packages, which don't contain anything but by their dependencies pull in a collection of other packages.

---

### Post by thexnightmare on 2014-07-11
Amazing, worked perfectly.
Ive downloaded multiple packages, but when trying to install them, the system said the the packages missing some dependencies, any parameter allow downloading them all with dependencies?

---

### Post by Impavidus on 2014-07-11
Did you try apt-get download or apt-get --download-only install?

---

### Post by thexnightmare on 2014-07-12
Yes it seems all of them just download the package without it's dependencies!!!
Any idea?

---

### Post by ian-weisser on 2014-07-12
Apt-get should download dependencies automatically. Not including dependencies is quite unusual.

What, exactly, are those error messages?

---

### Post by thexnightmare on 2014-07-13
there is no error messages.
It tried apt-get with 10 packages, and it downloaded 10 packages.
I tried to install them, few of them shows that they needs packages dependencies.
I downloaded theses dependencies, and when trying to install them, they asked me for others, and so on...

---

### Post by ian-weisser on 2014-07-13
Yes, please show us the set of those *dependency* messages. How can we reproduce the issue?

If you install those same packages without --download-only, do you get the same dependency messages?

---

### Post by thexnightmare on 2014-07-13
I tried all previous commands:
{
sudo apt-get download build-essential libgtk2.0-dev libjpeg-dev libtiff4-dev libjasper-dev libopenexr-dev cmake python-dev python-numpy python-tk libtbb-dev libeigen3-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev libqt4-dev libqt4-opengl-dev sphinx-common texlive-latex-extra libv4l-dev libdc1394-22-dev libavcodec-dev libavformat-dev libswscale-dev default-jdk ant libvtk5-qt4-dev
}
And only those packages are downloaded, when trying to install them from local, dependency errors appears

---

### Post by ian-weisser on 2014-07-13
The apt-get manpage is a great resource

Have you tried *both *methods of downloading using apt?
In the past, --download-only has included dependencies for me.

>     download
           download will download the given binary package into the current
           directory.


Example: **sudo apt-get download foo**


>        -d, --download-only
           Download only; package files are only retrieved, not unpacked or
           installed. Configuration Item: APT::Get::Download-Only.


Example: **sudo apt-get install -d foo**

---

### Post by thexnightmare on 2014-07-13
Dear,
I am trying thi since weeks and read alot without any successfull solution
try sudo apt-get download synaptic.
then sudo dpkg -i synaptic
It will be installed, but it cant be run as it needs dependencies

wait, i tried with d parameter, seems all downloaded and nothing installed, but where they are downloaded?

I found that there are downloaded here with all dependencies "/var/cache/apt/archives/". 
Can I change the download location?

---

### Post by ian-weisser on 2014-07-13
You can change the download directory (see the manpage), but it would be unwise to do so.
Apt expects to find downloaded packages there. It's an appropriate location.

Why do you want to change the download location?

Don't use dpkg to install multiple packages. It cannot do that. Use apt for multiple packages
When you use download-only, try:
**sudo apt-get install --download-only synaptic**  (download, don't install)
**sudo apt-get install --no-download synaptic**  (install the downloaded package at /var/cache/apt/archives/ )

You know, the manpage really does explain all this....

---

### Post by thexnightmare on 2014-07-13
Finally found: 
apt-get -d -o dir::cache=`pwd` install package
Thanks all for help

You know, the manpage really does explain all this....


How to access it?

---

