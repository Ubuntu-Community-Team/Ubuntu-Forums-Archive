---
title: "Fresh install, customize it then create a live CD/USB?"
date: 2016-09-10
forum: General Help
---

### Post by PopsTheSailor on 2016-09-10
Is it not possible to do a fresh install, then make changes (add / remove packages, update firefox and flash, etc) and then create a Live CD or USB? I've been searching and it seems like the threads I can find talk about creating branches of Ubuntu / Debian, etc. Very complicated for a newbie and don't seem to be updated recently (at least the ones I found). I just want to create an updated "master config" that I can then create a Live CD or USB. 

Easy easy easy please.....

---

### Post by Bucky Ball on 2016-09-10
Well ... You could [give this a go]("http://www.remastersys.org/"). There are other ways, but if this works, looks like it might be easy. It is a respin of the very popular but no longer supported Remastersys.

Download the Ubuntu .deb file, double-click it and it should install.

PS: You might have better luck with your search if you go for something like 'create iso ubuntu install' rather than create cd/dvd. You want to create an .iso file of your install and then create whatever install media, USB/disk.

You can also use things like dd, mkusb, Clonezilla, fsarchiver to create a clone of your partition then clone that to another partition, but don't think that is what you're looking for.

---

### Post by &amp;KyT$0P# on 2016-09-10
What you want to do is possible.

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

Or, if you would rather "just install" Ubuntu and then make your customisations directly a live CD, [https://help.ubuntu.com/community/LiveCDCustomization#System_Requirements]("https://help.ubuntu.com/community/LiveCDCustomization#System_Requirements")
This one I have tried in 16.04 and it should work.

The only real issue I hit is, due to something about ISO filesystem, there is a size limit on the .squashfs file, if I'm remembering right it's about 4 GB but not sure on that.  But as long as you don't install too many additional packages you should be fine.

---

### Post by Bucky Ball on 2016-09-10
> **PopsTheSailor]Easy easy easy please..... [/QUOTE]

[QUOTE=halogen2 said:**
> What you want to do is possible.

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

This is not easy. :| ;)

---

### Post by Keith_Helms on 2016-09-10
After you get everything installed you could backup the entire system to a tar file on a USB drive.  You could then restore from that file to a new system somewhere else, but you'd have to initially install that system the normal way.  If you want an actual bootable live cd or usb that works just like the one you downloaded but has extra "stuff" in it, sorry that won't be easy at all.  You would have to edit the original iso file that you downloaded.  Getting new binaries for commands or applications into that file would be a medium to large effort.  Getting them in there so that the package manager, once installed to a hard drive, knows about them would be an extremely larger pain.

I poked through the innards of the iso file to install Xubuntu 16.04.  It looks like most of the system is contained in a subdirectory named "casper" in a file named "filesystem.squashfs".   Squashfs is a compressed file system format.  To tinker with it you would need to extract the iso to a directory on your hard drive, then "unsquash" the squash file system to another directory, make your changes to the squash file system, resquash it back into the iso directory, rebuild the iso file from the changed directory tree.  Well, you can see how much trouble it would be.

My solution for this issue was to write a little script that takes a text file with the names of packages I want installed on a new system.  After I install the system, I run the script and it adds all the additional packages I want.  It's a little longer than absolutely necessary because I made it install up to 20 packages at a time to speed it up a bit.

```
#!/bin/bash

install_packages () {
    packagelist="$1"
    echo ">>>Installing $packagelist"

    apt-get -my install "$packagelist"
    rc=$?
    # If a package failed, retry each package individually    
    if [ $rc -ne 0 ]
    then
        for package in $packagelist
        do
            apt-get -my install $package
            rc=$?
            if [ $rc -ne 0 ]
            then
                echo "###Install of package $package failed"
            fi
        done
    fi
}

if [ $# -ne 1 ]
then
    echo "Usage: install_packages.sh package_list_file"
    exit
fi

if [ ! -e "$1" ]
then
  echo "$1 package list file not found"
  exit
fi

saveifs="$IFS"
IFS=$'\n' 
read -d '' -r -a lines < "$1"
IFS="$saveifs"

limit=${#lines[@]}
echo "Starting install of $limit packages"
counter=0
for ((i=0;i<$limit;i++))
do
    package=${lines[$i]}
    ((counter++))
    packages="$packages $package"
    if [ $counter -eq 20 ]
    then
        install_packages "$packages"
        counter=0
        packages=
    fi
done
if [ "$packages" != "" ]
then
    install_packages "$packages"
fi
exit
```

Here's an excerpt from the input package list file for the script:

```
audacious
audacity
build-essential
calibre
chromium-browser
cvs
default-jdk
default-jdk-doc
dosbox
eclipse
enscript
evince
exiftool
```

---

### Post by Bucky Ball on 2016-09-10
[Respin]("http://www.remastersys.org/"), linked to here and earlier, doesn't work for me. Downloaded .deb, tried to install, dependencies missing. I looked no further. Maybe they are not up to 16.04.1 (which is what I'm on).

---

### Post by yancek on 2016-09-10
There was a program called 'remastersys' which did exactly this.  Of course it also had the 4GB limit for the compressed iso.  It definitely worked through Ubuntu 12.04 and I've read posts by people getting it to work on 14.04.  If you are using something newer, I doubt it will work.  You might also look into systemback.  Just googling it should get you a lot of information.  

The simplest software of this kind I am aware of is 'mylivecd' which like almost all of this type software, is distribution specific.  In this case, it is only for PCLinuxOS.  After modifying your system, you simply type mylivecd in the terminal logged in as root and hit the Enter key.  And like other software of this type, it has the 4GB problem.

---

### Post by Bucky Ball on 2016-09-10
> **yancek said:**
> There was a program called 'remastersys' which did exactly this.

If you read previous posts we have already been talking about it. Remastersys is now spun into Respin and the .deb has missing dependencies for me on 16.04.1. :)

---

### Post by PopsTheSailor on 2016-09-11
Well it looks like you've answered my higher level question about whether there is a standard & easy way to do what I'm trying to do. Thanks all, I'll mess around with a few of these suggestions to see if I have any luck!

I'll go ahead and mark this a solved, even though it really isn't but no need to continue hashing this one out.

---

### Post by C.S.Cameron on 2016-09-11
With the cost of larger USB3 flash drives becoming more reasonable, you can easy do a full install and clone it from drive to drive.
There are several major advantages to a Full install to flash drive over a Persistent install.
I think Sudodus has made a small program to do this.

Edit:
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

