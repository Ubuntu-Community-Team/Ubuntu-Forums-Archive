---
title: "Will same /home partition work with multiple operating systems"
date: 2017-01-10
forum: General Help
---

### Post by Ralph L on 2017-01-10
I have installed on my hard disk several different version of ubuntu.  For example, I currently have installed Ubuntu 12.04, Xubuntu 14.04, and Xubuntu 16.04.  I have never used a separate /home partition during my installs.  Instead I have always had a single separate Data partition that each OS can access, no matter which partition I boot.  It appears to me that there are advantages to using a single /home partition and copying my Data partition into that (afterwards deleting my Data partition).  However, I have to be sure that all version of Ubuntu can use this single /home partition.  Note that I want to install Lubuntu and Kubuntu in the near future to try them.  I would like to use the same /home partition with them also.

My question is:  Will I have problems using the same /home partition??

---

### Post by kevdog on 2017-01-10
I just going to throw out some ideas...

1. Are you planning on running the OS's at the same time through virtualization or just separately booting them.
2. I could think there might be a problem is the UID/GIDs are not the same between the installations --- I'm not sure of this however.

---

### Post by SuperFreak on 2017-01-10
I was advised against this by the Ubuntu gurus . I think the home directory may contain some system files that will become conflicted with multiple OSs

---

### Post by vasa1 on 2017-01-10
> **SuperFreak said:**
> ... I think the home directory may contain some system files that will become conflicted with multiple OSs
That's my feeling as well.

---

### Post by Bucky Ball on 2017-01-10
In my opinion, what you have now is by far the best option. Are you using symlinks in the /home directories in each install to link to the directories in your /data partition? That works best.

I'm presuming you have /home directories, not partitions, for each install? By what you've said so far, seems this is the case, although not crystal clear.

---

### Post by wildmanne39 on 2017-01-10
> **SuperFreak said:**
> I was advised against this by the Ubuntu gurus . I think the home directory may contain some system files that will become conflicted with multiple OSs
+2 there are some configuration files that will conflict.

---

### Post by Ralph L on 2017-01-11
Thank you all for responding.  I will heed your advice and not try to use the same /home partition for multiple OS's. 
Kevdog:  I would just be running different OS's at different times, not trying to run 2 at once.
Bucky Ball: 1. I currently have a /home folder for each OS, not separate /home partitions for each OS.  2.  Yes, I have symlinks to my Data partition.  I have my Firefox profile, my Thunderbird profile, my LuckyBackup profile, my Calc macros, my Writer Templates, and a number of Libreoffice configuration files on my Data partition with symlinks to them in each OS.  I have also installed Python Windows Organizer on the Data Partition with symlink to it.  This eases the task of installing a new OS and allows each OS to have apps that work the same.  However, installing a new OS is still a pain setting up the symlinks, revising the boot time start up menu, setting custom actions in Thunar, etc.  

Thanks again for the quick response!!

---

### Post by Bucky Ball on 2017-01-11
> **Ralph L said:**
> Bucky Ball: 1. I currently have a /home folder for each OS, not separate /home partitions for each OS.  2.  Yes, I have symlinks to my Data partition.  I have my Firefox profile, my Thunderbird profile, my LuckyBackup profile, my Calc macros, my Writer Templates, and a number of Libreoffice configuration files on my Data partition with symlinks to them in each OS.  I have also installed Python Windows Organizer on the Data Partition with symlink to it.  This eases the task of installing a new OS and allows each OS to have apps that work the same.  However, installing a new OS is still a pain setting up the symlinks, revising the boot time start up menu, setting custom actions in Thunar, etc.

How would the hassle be relieved by doing it the other way? Just a different set of 'things to do at install'. 

In my opinion, you have the ideal setup already for your circumstances. If it ain't broke, don't fix it, and what you're using now is what is generally advised for similar setups. It is used by many. Having four installs all using the same /home partition can get messy. A data partition and symlinks is better.

Tip: On a new install, set up the first symlink command in a terminal and copy it. Create the symlink. When you set up the next symlink, paste the other and just change the target and source *directories*, not the whole command line. Easy and done in less than five minutes.

For instance:

```
ls -n /home/user/**databit** /media/user/data/**databit**
```

(The file paths are probably not going to be the same as your machine, obviously.) Copy that command before running it and paste it in when creating the next symlink and you only need to change the target and source, which are both 'databit'. :)

---

### Post by oldfred on 2017-01-11
I also noted hassle of each new install requiring configuration.
After just a couple, I said is not computer supposed to make things easier.
So I tried to do as much thru command line as I could, and then copied commands from history into a bash file.
Over time I added some checks & features that other users posted.

While my script would not work for you, in may give you some ideas. You may still have in your history from a new install, if you used command line to make changes.
history > history_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).txt

       Oldfred's install scripts
[https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662](https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662)

---

### Post by Keith_Helms on 2017-01-11
> **Ralph L said:**
> Thank you all for responding.  I will heed your advice and not try to use the same /home partition for multiple OS's. 
Kevdog:  I would just be running different OS's at different times, not trying to run 2 at once.
Bucky Ball: 1. I currently have a /home folder for each OS, not separate /home partitions for each OS.  2.  Yes, I have symlinks to my Data partition.  I have my Firefox profile, my Thunderbird profile, my LuckyBackup profile, my Calc macros, my Writer Templates, and a number of Libreoffice configuration files on my Data partition with symlinks to them in each OS.  I have also installed Python Windows Organizer on the Data Partition with symlink to it.  This eases the task of installing a new OS and allows each OS to have apps that work the same.  However, installing a new OS is still a pain setting up the symlinks, revising the boot time start up menu, setting custom actions in Thunar, etc.  

Thanks again for the quick response!!

I have a little script that is one of the first things I run on a new install to set up symlinks to a shared partition.  It also gets rid of the standard directory names (I hate navigating through directories with caps in the names).  You're welcome to modify it for all the symlinks you normally set up.

```

#/bin/bash

remove_dir () {
if [ -e "$HOME/$DIR" ]
then
    echo "Removing $HOME/$DIR"
    rmdir $HOME/$DIR
else
    echo "$HOME/$DIR does not exist"
fi
}

set_homedirs_softlink () {
echo "creating link for $DIR"
if [ ! -e "/homedata" ]
then
    echo "/homedata does not exist!"
    return
fi
if [ ! -e "/homedata/homedirs" ]
then
    mkdir "/homedata/homedirs"
fi
if [ ! -e "$HOME/$DIR" ]
then
    if [ ! -e "/homedata/homedirs/$DIR" ]
    then
        mkdir "/homedata/homedirs/$DIR"
    fi
    ln -s "/homedata/homedirs/$DIR" "$HOME/$DIR"
fi
}

set_softlink () {
echo "creating link for $DIR"
if [ ! -e "/homedata" ]
then
    echo "/homedata does not exist!"
    return
fi
if [ ! -e "$HOME/$DIR" ]
then
    if [ ! -e "/homedata/$DIR" ]
    then
        mkdir "/homedata/$DIR"
    fi
    ln -s "/homedata/$DIR" "$HOME/$DIR"
fi
}


DIR="Documents"
remove_dir
DIR="Downloads"
remove_dir
DIR="Music"
remove_dir
DIR="Pictures"
remove_dir
DIR="Public"
remove_dir
DIR="Templates"
remove_dir
DIR="Videos"
remove_dir

DIR="bin"
set_homedirs_softlink
DIR="data"
set_homedirs_softlink
DIR="documents"
set_homedirs_softlink
DIR="dosdrive"
set_homedirs_softlink
DIR="download"
set_homedirs_softlink
DIR="jars"
set_homedirs_softlink
DIR="workspace"
set_homedirs_softlink
DIR="Podcasts"
set_softlink
DIR="video"
set_softlink

exit

```

---

