---
title: "Add local deb files to sources ?"
date: 2004-10-31
forum: General Help
---

### Post by CbrPad on 2004-10-31
Hi,

I'm on my second install of Ubuntu, messed up the first one doing newbie stuff, heh.  I had made a backup of all the packages I had downloaded, which had been in /etc/apt/archives, but can't figure out how to correctly add them to the sources list.  

I've copied them back to that location, and think I should have a line something like

deb file:/etc/apt/archives 

but what do I put at the end ?  They're a mix of sarge and universe and multiverse,etc.   If I put in, e.g.,  deb file:/etc/apt/archives/ warty main   I get an error in Synaptic saying stuff like this ...

Couldn't stat source package list file: warty/main Packages (/var/lib/apt/lists/_etc_apt_archives_dists_warty_main_binary-i386_Packages) - stat (2 No such file or directory)

Any help much appreciated as don't want to download 200+ megs by dialup again!

---

### Post by Vlammend on 2004-11-03
Being a complete newbie i am also not able to install a downloaded debian package (Mattricks)

How should I download a singe deb file?

The man pages of apt are not a real help and the help file for synaptic is not completly compatable with the shown screens and information.
Searching the forum did also not help 

Help will be appreciated.

---

### Post by ulrich on 2004-11-03
@cbrpad
shouldnt it be enough to activate universe multiverse in your sources.list and doing an 'apt-get update' ?
does ubuntu really trying to download again, even if the file is already downloaded and present in the archives folder?

@vlammend
deb-files need to be installed like
```

dpkg -i thedebiwant.deb

```

---

### Post by TekMate on 2004-11-03
If you backed up all the files you should be able to open a terminal in the folder they're saved to and type dpkg *.deb to install them all.

---

### Post by az on 2004-11-03
actually, it would be:
dpkg -i *.deb

If the versions have changed in the repositories since the time you downloaded those files, synaptic (or apt) will download the newser version.  What you could do with your pile of packages is either the above command or create yourself a repository.

cd /storage #assume that your directory is named storage
dpkg-scanpackages . /dev/null > Packages

note the "." and the capital P

then add

deb file://storage ./
 
to your apt sources.list file
apt-get update

apt-get install whatever...

---

### Post by CbrPad on 2004-11-04
Fantastic.  Thanks guys, I'll give that repository thing a try.   

I had tried dpkg -i at first and for some reason it wasn't working, but it worked last night even though I had to go in and install every dependency individually.

---

### Post by rupert on 2004-11-04
its a bit of topic,
but can i make a snapshot of my installed packages?
I mean that i wanna install a new machine and than use the same packages than on the old machine by using the cached deb packages in /car/cache/apt.
under suse you could create a file where all the installed packages are listed and then run this script on a clean install to get the same config.

rupert

---

### Post by Vlammend on 2004-11-04
Thanks for the answers, I managed to install it.

@Rupert, I think you can with "dpkg -l"
look at paragraph 3.3. of [Installing Debian software using Apt](http://newbiedoc.sourceforge.net/system/apt-get-intro.html)

---

### Post by dare2dreamer on 2004-11-15
How to replicate the installed packages of one system on another:

existing system:

```
sudo dpkg --get-selections > /someplacelikeafloppy/selections
```

new system:

```
sudo dpkg --set-selections < /someplacelikeafloppy/selections
sudo apt-get dselect-upgrade
```

The "selections" file is a plain text file, and can be edited to customize list of packages to install.

---

