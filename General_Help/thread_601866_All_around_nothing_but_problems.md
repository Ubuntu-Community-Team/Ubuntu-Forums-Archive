---
title: "All around nothing but problems"
date: 2007-11-03
forum: General Help
---

### Post by antixerox on 2007-11-03
I am not sure exactly what is wrong with my system I just installed Ubuntu 7.10 Gutsy on my Dell Inspiron 6400 and the ATI restricted drivers are not working.  When i followed the steps to fix that i keep getting issues like ubable to install of repository indexes and some index files failed to download.

I was having similar problems when I installed on my desktop yesterday but that was an nvidia and i fixed it by running gnome-app-install well that isnt working and I have no idea what to do anymore help would be greatly appreciated.

EDIT;
when i try to enable the ATI video drives it says this...
The software source for the package

   xorg-driver-fglrx

 is not enabled.

---

### Post by Maestro23 on 2007-11-03
Make sure you have all your Sources enabled.  System>>Admin>>Software Sources

---

### Post by antixerox on 2007-11-03
Already tried that sorry forgot to include in first post all of my boxes are checked just like yours, and I also have replaced my sources.list file with one i made from ubuntu's although I am not sure that fixed anything.

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> Already tried that sorry forgot to include in first post all of my boxes are checked just like yours, and I also have replaced my sources.list file with one i made from ubuntu's although I am not sure that fixed anything.

What's your video card?  What drivers do you have installed for it?

---

### Post by antixerox on 2007-11-03
My video card is the mobile x1400 and there are no drivers installed it wont let me due to the other problems with connection or just not finding the files.

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> My video card is the mobile x1400 and there are no drivers installed it wont let me due to the other problems with connection or just not finding the files.

Connection problems?  What kind?

Have you looked into using the Envy script to install your drivers? Has helped a lot of people.

Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by antixerox on 2007-11-03
Ok so my school blocks that web page but the connection problems are like the ones i mentioned in my first post. 
its unable to download all of the repository files, and when i do sudo apt-get update it says unable to connect or download anything.
stuff like that and since i can do them fine from my desktop running the same os i think its something to do with my sources file.

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> Ok so my school blocks that web page but the connection problems are like the ones i mentioned in my first post. 
its unable to download all of the repository files, and when i do sudo apt-get update it says unable to connect or download anything.
stuff like that and since i can do them fine from my desktop running the same os i think its something to do with my sources file.

Post your sources.list file.

> cat /etc/apt/sources.list

Copy/Paste the file here.

---

### Post by strabes on 2007-11-03
Once you get your sources.list problem worked out, follow the instructions in the ATI link in my signature.

---

### Post by antixerox on 2007-11-03
> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse 

# Upstream Opera
# GPG key: 6A423791
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy 


There is my sources file

EDIT:
and i have followed those directions, but when i run the commands it dosnt find the files, that is why i think its a source problem

---

### Post by antixerox on 2007-11-03
ok so after a few new attempts at a few different possible solutions I still circle back around to when I try to install codes, update, and repository files it is either unable to download them or just cant find them.  Is there a place where i can get a new sources.list file cause i dont think mine is correct?

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> ok so after a few new attempts at a few different possible solutions I still circle back around to when I try to install codes, update, and repository files it is either unable to download them or just cant find them.  Is there a place where i can get a new sources.list file cause i dont think mine is correct?

What are you running? 32 or 64-bit Gutsy

---

### Post by antixerox on 2007-11-03
I am pretty sure its 32 but how can i check?

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> I am pretty sure its 32 but how can i check?

> uname -a

If its like mine: 
> Linux gt5058 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007** x86_64 **GNU/Linux

You're running 64-bit Gutsy

---

### Post by antixerox on 2007-11-03
Linux jlappy 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

i think its 32 bit

---

### Post by antixerox on 2007-11-03
Ok so i found a different source.list file and replaced mine with it and now when i try to sudo apt-get update it will install about half of the files same with media player codecs, but still no drivers for my graphics card :(

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> Ok so i found a different source.list file and replaced mine with it and now when i try to sudo apt-get update it will install about half of the files same with media player codecs, but still no drivers for my graphics card :(

What commands are you using to install?  Lets take things one at a time.

---

### Post by antixerox on 2007-11-03
sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx

mainly those few to try and get my video drivers working and I am also trying to install tor so i can try envy but i am unable to find the file tor when i run
sudo apt-get install tor privoxy

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx

mainly those few to try and get my video drivers working and I am also trying to install tor so i can try envy but i am unable to find the file tor when i run
sudo apt-get install tor privoxy

Ok.  So the 1st two commands.  Are you able to find/install the 2 packages?

---

### Post by antixerox on 2007-11-03
the first of the two 
sudo apt-get update
returns a huge list of failed and err stuff and then starts to download then outputs this
> W: GPG error: [ftp://ftp.uni-kl.de](ftp://ftp.uni-kl.de) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.



sudo apt-get install linux-restricted-modules-generic

says that it is the current version so i think this one works but something is going wrong in the first one.

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> the first of the two 
sudo apt-get update
returns a huge list of failed and err stuff and then starts to download then outputs this



sudo apt-get install linux-restricted-modules-generic

says that it is the current version so i think this one works but something is going wrong in the first one.

Can you post this current sources list you're using?  Where did you get it from?

---

### Post by antixerox on 2007-11-03
> deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘partner’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

##################################################
##################################################
##ffmpeg of ubuntu is slower then molasses in January on the arctics
##Alternative resource for Multimedia support like ffmpeg
#is meant for Debian But works fine on my Gutsy Gibbon
##use at your own risk
##See: [http://debian.video.free.fr/index.html](http://debian.video.free.fr/index.html)
##get the apt GPG key from here : [http://debian.video.free.fr/faq.html](http://debian.video.free.fr/faq.html)
deb [ftp://ftp.uni-kl.de/debian-multimedia/](ftp://ftp.uni-kl.de/debian-multimedia/) stable main
##############################################
##############################################

I got it from a ubuntu page somewhere.  someone recommended it

---

### Post by Maestro23 on 2007-11-03
Comment out the following line at the end:

> #deb [ftp://ftp.uni-kl.de/debian-multimedia/](ftp://ftp.uni-kl.de/debian-multimedia/) stable main


Don't need any debian sources in there.

Then:

> sudo apt-get update

sudo apt-get upgrade


---

### Post by antixerox on 2007-11-03
still not upgrading everything.

should I just try to reinstall again?

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> still not upgrading everything.

should I just try to reinstall again?

Hmm... So after you did what I posted, did you try installing the xorg-driver again?  If so, what error message did it give you?

---

### Post by antixerox on 2007-11-03
jordan@jlappy:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

---

### Post by Maestro23 on 2007-11-03
> **antixerox said:**
> jordan@jlappy:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

Got into Synaptic.  Search for xorg-driver-fglrx. Try it that way.  By the way, you can hit me up on Yahoo IM or MSN IM.  Just click either icon by my name.

---

### Post by antixerox on 2007-11-03
nvm i got in there but I couldnt find the file

---

### Post by strabes on 2007-11-03
Ok, after making sure you're connected to the internet (try running "ping google.com") please replace the entire contents of your sources.list file with the following:> ## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted

Then, paste the output of the following commands:```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
```

---

### Post by antixerox on 2007-11-03
here is the output after executing both of them 
one thing is when i ran the second on it actually prompted me for yes or no so that did somthing.
> jordan@jlappy:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
jordan@jlappy:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base libstdc++5
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5 xorg-driver-fglrx
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 9005kB of archives.
After unpacking 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main gcc-3.3-base 1:3.3.6-15ubuntu2
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libstdc++5 1:3.3.6-15ubuntu2
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-14.9
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb)  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb)  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb)  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



EDIT::
Then i went to the restricted drivers and tried to install the graphics driver and it actaully ran but failed to install giving me this error.
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.9_i386.deb)
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]


---

### Post by antixerox on 2007-11-04
Yea i still cant get it to download any codecs or the graphics drivers.  it seems to me like somthing is borked especially considering it did this straight from the start up.

---

### Post by antixerox on 2007-11-04
ok so I am reloading now gonna see if that fixes anything. if not I will prolly start a new thread from the beginning.

---

### Post by ZzeusS on 2007-11-04
Try it from a network that is not blocking access to ubuntu.com

---

### Post by Happy_Man on 2007-11-04
This isn't a Synaptic problem; it's an internet connection problem. Are you being blocked from ubuntu repos? Try pinging [www.google.com](www.google.com) using the command ```
ping www.google.com
``` or getting on the Internet using firefox. If you are behind a work or school firewall, that may be the problem.

---

