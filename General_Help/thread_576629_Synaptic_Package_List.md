---
title: "Synaptic Package List"
date: 2007-10-15
forum: General Help
---

### Post by samurailink3 on 2007-10-15
I'm looking to get synaptic to install the packages I have installed on here in a fresh ubuntu install. Is there any way synaptic can export a list of installed packages? I want to be able to automate the installation of these packages across different installs, I know I can export a 'changes' list, but the problem is, I've already installed these packages. Any ideas, is there some function I've overlooked? Thanks!!

---

### Post by p_quarles on 2007-10-15
I'm not sure how to do this in Synaptic, but here are some instructions for using the command line to do this.

To export the package list:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```This will put a file called "package_list" in your home folder. This is all you will need to clone the installation, so put this file onto some form of removable media (external HD, flash drive, etc.).

After you've done the fresh installation, copy the package_list file into your new home directory, and run these commands:
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```A few warnings:
1) If you installed any .deb packages that weren't in the Ubuntu repositories, this method will produce an error. You can deal with this either by removing those packages before you create the package_list file, or you can edit the package_list file itself to remove their listings. 

2) If you're upgrading to a new version of Ubuntu (which is likely, given the timing here), you'll probably encounter some packages that are no longer in the repos, or have changed names. When you run the second command, it will give you an error message telling you which packages cannot be found. Make a note of them, edit them out of packages_list, and run the command again. 

So, it's not perfect, but it will automate 95% of the reinstallation process.

---

### Post by samurailink3 on 2007-10-16
Ok, thanks!!

---

### Post by rockprincess on 2007-10-16
the --get-selection command doesn't work for me :(

---

### Post by p_quarles on 2007-10-16
> **rockprincess said:**
> the --get-selection command doesn't work for me :(
Oops. That was a typo on my part. Should be "--get-selections" (plural)

I've edited my first post for accuracy.

---

### Post by rockprincess on 2007-10-16
cheers man, this is just what i needed :D

---

### Post by jkeyes0 on 2007-10-23
> **p_quarles said:**
> I'm not sure how to do this in Synaptic, but here are some instructions for using the command line to do this.

To export the package list:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```This will put a file called "package_list" in your home folder. This is all you will need to clone the installation, so put this file onto some form of removable media (external HD, flash drive, etc.).

After you've done the fresh installation, copy the package_list file into your new home directory, and run these commands:
```
sudo apt-get update
cat package_list | xargs sudo apt-get install
```A few warnings:
1) If you installed any .deb packages that weren't in the Ubuntu repositories, this method will produce an error. You can deal with this either by removing those packages before you create the package_list file, or you can edit the package_list file itself to remove their listings. 

2) If you're upgrading to a new version of Ubuntu (which is likely, given the timing here), you'll probably encounter some packages that are no longer in the repos, or have changed names. When you run the second command, it will give you an error message telling you which packages cannot be found. Make a note of them, edit them out of packages_list, and run the command again. 

So, it's not perfect, but it will automate 95% of the reinstallation process.

/bowdown. /grovel.
I was planning on installing Gutsy tonight, and wanted to make sure that I have a backup copy of all my installed software in case something goes wrong. You're a lifesaver.=D>

---

### Post by jkeyes0 on 2007-10-24
> **jkeyes0 said:**
> /bowdown. /grovel.
I was planning on installing Gutsy tonight, and wanted to make sure that I have a backup copy of all my installed software in case something goes wrong. You're a lifesaver.=D>

Update: I performed the steps p_quarles mentioned, and it backed up my selection list perfectly. I had to trim the fat out of the list to make it work in gutsy, but it was mainly removing libs and some of the 3rd party apps I use.

One thing, however. I had to put a -y at the end of the "cat package_list | xargs sudo apt-get install" line to get it to keep from aborting every time. Other than that, I've got all my needed software in gutsy with a very minimal amount of effort now. Thanks!

---

### Post by p_quarles on 2007-10-24
> **jkeyes0 said:**
> Update: I performed the steps p_quarles mentioned, and it backed up my selection list perfectly. I had to trim the fat out of the list to make it work in gutsy, but it was mainly removing libs and some of the 3rd party apps I use.

One thing, however. I had to put a -y at the end of the "cat package_list | xargs sudo apt-get install" line to get it to keep from aborting every time. Other than that, I've got all my needed software in gutsy with a very minimal amount of effort now. Thanks!
Thanks for pointing that out. I've added the "y" option to the instructions in my original message.

---

### Post by boga on 2007-12-09
And is there any way to list only those packages that were installed explicitly by me, that is exclude the ones installed during system installation and ones installed as dependencies? That would make the list much shorter and much less prone to errors because of certain packages being removed/renamed. I've tried to write a script that lists all the packages then lists all their dependencies and then outputs only those packages that are never listed as dependencies but unfortunately it fails to output packages with dependency loops like thunderbird - mozilla-thunderbird. May be there's an easier way to do it rather than adding loop handling to the script?

---

### Post by p_quarles on 2007-12-09
> **boga said:**
> And is there any way to list only those packages that were installed explicitly by me, that is exclude the ones installed during system installation and ones installed as dependencies? That would make the list much shorter and much less prone to errors because of certain packages being removed/renamed. I've tried to write a script that lists all the packages then lists all their dependencies and then outputs only those packages that are never listed as dependencies but unfortunately it fails to output packages with dependency loops like thunderbird - mozilla-thunderbird. May be there's an easier way to do it rather than adding loop handling to the script?
That's an interesting idea. As far as I know, APT doesn't actually differentiate between packages installed initially and those added later -- it marks them all as installed.

What you *could *do, though, is make a package list immediately after a brand new installation. You could then use a script to find and remove items on that list from any subsequent package lists. This would require either planning far in advance, or taking the time to virtualize a new installation of your current distro. 

Frankly, though, the worst I've had with this method was needing to remove 12 items from the list manually. Getting around this step might be worthwhile, still, if you normally upgrade every three distros or so.

---

### Post by boga on 2007-12-10
> **p_quarles said:**
> 
What you could do, though, is make a package list immediately after a brand new installation. You could then use a script to find and remove items on that list from any subsequent package lists. This would require either planning far in advance, or taking the time to virtualize a new installation of your current distro. 
Well, I just assume that the initial package list is: ubuntu-desktop ubuntu-minimal ubuntu-standard linux-generic and all their dependencies (both required and recommended) and it works just fine besides the problem of dependency loops which results in some packages missing from the output list like thunderbird or uqm.
Having reinstalled Gutsy 10 times or so before I made it work :-), what I'm trying to do is to create a set of scripts for as much as possible automated reinstallation which requires saving/restoring /boot/grub/menu.lst, /root, /usr/local, apt cache (for faster/cheaper reinstallation) and some other stuff in /usr and /etc. This can also help to switch between i386/amd64, ubuntu/kubuntu or any other distribution (at least Debian based) and restore in case of hard disk failure (provided the /home partition is backed up regularly :-)).

---

### Post by boga on 2007-12-17
> **p_quarles said:**
> What you *could *do, though, is make a package list immediately after a brand new installation.
Well, I've found out this list is really created during installation (/var/log/installer/initial-status.gz) so there's no need to create it. So this script does the job perfectly:
```

#! /bin/sh
TEMPFILE=`tempfile`
cat /var/log/installer/initial-status.gz | gzip -d |grep '^Package:' | awk '{ print $2}' > $TEMPFILE
aptitude search -F %p '~i!~M' | awk '{ print $1}' | grep -v -F -f $TEMPFILE
rm $TEMPFILE

```

---

