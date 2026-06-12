---
title: "nxclient missing libstdc++2.10-glibc2.2 error"
date: 2007-01-19
forum: General Help
---

### Post by pete44904 on 2007-01-19
Hi i'm a bit of a newbie to linux and i'm currently trying to install nxclient on Ubuntu 6.04 dapper drake but i'm not getting that far i have searched the internet but i could solve the problem:

This is what i have done i have downloaded the nxclient package from the nomachine website, and have then tried to install by using the following command

sudo dpkg nxclient_2.1.0-11_i386.deb

I then receive a dependency error saying that libstdc++2.10-glibc2.2 is missing - i have tried to type apt-get install libstdc++2.10-glibc2.2 - and i receive the following error:-

Package libstdc++2.10-glibc2.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++2.10-glibc2.2 has no installation candidate


I hope someone can help me with list as i'm not sure what i am doing wrong - thanks in advance

---

### Post by mkoyle on 2007-01-19
I don't know from your post what version of libstdc++2.10-glibc2.2 exactly you need, but my guess is that if you download the i386 package from [http://packages.debian.org/unstable/libs/libstdc++2.10-glibc2.2](http://packages.debian.org/unstable/libs/libstdc++2.10-glibc2.2), you will be able to finish your install (unless there are further dependency problems).

The trouble you are having is that the NX client guys did not assume you would be using Ubuntu and Debian standard does include that file.

You could add the debian repositories, but generally they recommend not doing that here.  I have gotten away with it in the past, but there are really no guarantees ;)

So download [http://http.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://http.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb) and then 'sudo dpkg -i libstdc[Tab]' and you should be un business.  If you get another problem or a message about dependency problems, post again and someone will show you how to add the Debian repositories temporarily and then remove them again.

--Matthew

---

### Post by pete44904 on 2007-01-20
Hi thanks for the quick reply - i have tried to download the repository file and install it but i recieve the following error, Do i need to unistall the old version - Thanks again for your help i feel like i've made a lot of progress just need to sort the dependcy out and i think i'm sorted:D 

Preparing to replace libstdc++2.10-glibc2.2 1:2.95.4-27 (using libstdc++2.10-glibc2.2_2.95.4-27_i386.deb) ...
Unpacking replacement libstdc++2.10-glibc2.2 ...
dpkg: dependency problems prevent configuration of libstdc++2.10-glibc2.2:
 libstdc++2.10-glibc2.2 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libstdc++2.10-glibc2.2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++2.10-glibc2.2

---

### Post by mkoyle on 2007-01-22
Hey... are you running Ubuntu Dapper?  If you want to stay with Dapper that's fine; just don't be surprised by dependency problems like this when you go to install things that are not in Ubuntu repositories.

---

### Post by mkoyle on 2007-01-22
I am guessing that the fellows that packaged that file you are trying to install figured you would have Ubuntu Edgy / Debian Unstable.  It is not exactly a problem, but it could be a bit difficult for you.  You aren't doing anything wrong, so I will try to show you ways to get around this.  The good news is that we can probably do it.  The bad news is that some packages have so many dependencies that it is nearly impossible to do it manually.

So go to a terminal window.  wget is a command line program that downloads files off the internet.  Type

wget http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.1_i386.deb

then type 

sudo dpkg -i libc6[Tab key]

after you press the tab key, the entire filename should fill in.

You might be set now.  Don't try to do the following if that worked ;)  Anyway, if that gives you more dependency errors and you really want to get this installed, the next option is ... the wild and crazy (don't be too scared) idea of using Ubuntu Edgy repositories to get this installed and then removing the Edgy repositories.  To do that, do the following:

1. We are going to make a backup of a file I am about to have you change (so we can get it back to normal easily):

sudo cp /etc/apt/sources.list /etc/apt/sources.list_default

2. To open 'gedit' (I think that stands for gnome editor or something like that), in a terminal type

sudo gedit /etc/apt/sources.list

3. The file that opens includes the internet addresses of additional files and also the current files which Ubuntu maintainers can upgrade to correct problems like the one you are having. These can be changed to anything you want as long as you trust the source you get them from (after this is fixed, you can look at ubuntuguide: [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)) One of the lines in the file will be something like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

4. Copy that line and make an identical copy of it right below the original so it looks like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

5. Change one of the two lines so that instead of dapper it says edgy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

6. Now we are going to use the command-line application 'apt-get' (in the terminal) to install that program I tried to have you install before.

sudo apt-get update
sudo apt-get install libc6
sudo apt-get install -f

This might generate a really long list of ... 'do you really want to install these?' Type 'y' and 'enter.'  At this point, if the problem is fixed, the dpkg -i command you ran on your original file should say it installed properly.  If this is the case, we want to undo the change we just made so your entire system doesn't try to move over to Edgy (remember not to run the upgrade tool while your system is like this; trust me you don't want to do it).

7. Finally we are going to undo the change we made to the sources.list file by copying the original back over the one we changed.

sudo cp /etc/apt/sources.list_default /etc/apt/sources.list
sudo apt-get update

8. Now cross your fingers and try it. My guess is it's fixed (unless you got an error message like the one we already talked about).  Post again if it isn't working.

--Matthew

---

