---
title: "trying to install samba"
date: 2017-02-12
forum: General Help
---

### Post by jgw on 2017-02-12
I am trying to install samba.  I have tried a number of things but keep getting the same results/errors.  I have posted some of this at [http://pastebin.com/pUtxA418](http://pastebin.com/pUtxA418)

I have 5 computers here.  One is using windows10 and the rest are using ubuntu 16.04

I have also tried with synaptic with the same results.

I am trying to setup a local network and failing.

Thank you.....

---

### Post by wildmanne39 on 2017-02-12
*Thread moved to **General Help**.*
You have a lot of ppa's I recommend removing any that you do not need then check the one's that are left to make sure the link to them are good, I believe the chrome ppa has been causing issues lately.

Then do:
```
sudo apt-get update && sudo apt-get upgrade
```
and post any error's received.

---

### Post by jgw on 2017-02-12
Thank you for the reply.  

I disabled chrome ppa then ran y ppa manager and did what I could and removed any duplicates.  The unmet stuff all seems to involve samba except 1 - "libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed".  My temptation is to go into synaptic and uninstall everything I can find that has 'samba' in the name.  I actually did that once and get back to exactly where I am now.  I have also tried to install with both apt and apt-get (same results)

Here is what I did:
```
greg@greg:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for greg: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:3 [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) xenial InRelease
Hit:4 [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu) xenial InRelease
Hit:5 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial InRelease
Hit:6 [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) xenial InRelease
Hit:7 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial InRelease
Hit:8 [http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu](http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu) xenial InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greg@greg:~$ sudo apt-get  install  samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: python-samba but it is not going to be installed
         Depends: samba-common (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
         Depends: samba-common-bin (= 2:4.3.8+dfsg-0ubuntu1) but it is not going to be installed
         Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
         Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
         Recommends: attr
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by wildmanne39 on 2017-02-12
Check for held packages with the following command:
```
apt-mark showhold
```
and then take the off hold with:
```
sudo apt-mark unhold <package name>
```
but I am not sure you will be able to install this version of samba all the dependencies it needs have bee replaced by newer version of the same dependencies.

Where are you  trying to install samba from?
I am running ubuntu mate and by default samba was installed, I use synaptic package manger, it is the first application that I install in a new release.
[ATTACH=CONFIG]273665[/ATTACH]

---

### Post by jgw on 2017-02-12
Thanks again.

apt-mark showhold showed no replies.

I have also had synaptic fix broken packages multiple times as well as doing the same with a command line.  Makes no difference still get the same stuff.  What do you think about my going in, with synaptic, and simply deleting everything that has unmet dependencies and then making another run at installing?  Oh, and if I am going to reinstall how do you suggest I do that? (synaptic, apt, apt-get, ubuntu software?)

---

### Post by wildmanne39 on 2017-02-12
You might try the command like this:
```
sudo apt-mark showhold
```
I am not sure removing everything with unmeet dependencies is a good idea or needed.

Do you have all the repositories enabled that are in the screenshots below:
[ATTACH=CONFIG]273669[/ATTACH][ATTACH=CONFIG]273670[/ATTACH]
if not enable them and then reload the repositories and update Ubuntu.
Thanks

---

### Post by wildmanne39 on 2017-02-12
Try what is in this link:
[http://askubuntu.com/questions/363200/e-unable-to-correct-problems-you-have-held-broken-packages/451078#451078](http://askubuntu.com/questions/363200/e-unable-to-correct-problems-you-have-held-broken-packages/451078#451078)

---

### Post by jgw on 2017-02-13
Thanks.  I did as the link suggested and got (I am not sure what happened - perhaps nothing?):

```
greg@greg:~$ sudo aptitude install samba
[sudo] password for greg: 
The following NEW packages will be installed:
  attr{a} libaio1{a} python-ldb{a} python-samba{ab} python-tdb{a} samba{b} 
  samba-common-bin{ab} samba-dsdb-modules{ab} samba-vfs-modules{ab} 
  tdb-tools{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,026 kB of archives. After unpacking 23.5 MB will be used.
The following packages have unmet dependencies:
 python-samba : Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba : Depends: samba-common (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
         Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
         Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-dsdb-modules : Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
                      Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-vfs-modules : Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-common-bin : Depends: samba-common (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
                    Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     python-samba [Not Installed]                       
2)     samba [Not Installed]                              
3)     samba-common-bin [Not Installed]                   
4)     samba-dsdb-modules [Not Installed]                 
5)     samba-vfs-modules [Not Installed]        

and to check:
greg@greg:~$ samba
The program 'samba' is currently not installed. You can install it by typing:
sudo apt install samba

Thoughts?          



Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

---

### Post by wildmanne39 on 2017-02-13
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please post the output of:
```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by wildmanne39 on 2017-02-13
Did you have the option to install the packages:
```
Keep the following packages at their current version:
1)     python-samba [Not Installed]                       
2)     samba [Not Installed]                              
3)     samba-common-bin [Not Installed]                   
4)     samba-dsdb-modules [Not Installed]                 
5)     samba-vfs-modules [Not Installed]  
```

---

### Post by jgw on 2017-02-13
Thanks for the reply.  

I screwed up in my last reply.   I inserted "and to check to thoughts? before the end of the reply to "sudo aptitude install samba".  So, there were no options to install anything.  Had I used code tags I don't think that would have happened.  (the point of what was inserted is that samba is not installed and I betcha if I try I will get the same errors).  In case I missed it there were no held programs and I asked symantic to fix any packages that needed it before I did anything.  I also think that my problem is probably there because I did something clever and absolutely wrong but have no idea what it might have been.

I have also, in case I didn't show it:
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
sudo apt-get --fix-broken install
sudo apt-get clean



The output of your last suggested was:

```

greg@greg:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu xenial main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial main universe restricted multiverse #Added by software-properties

greg@greg:~$ ls /etc/apt/sources.list.d/
atareao-atareao-trusty.list
atareao-atareao-trusty.list.distUpgrade
atareao-atareao-trusty.list.save
diodon-team-ubuntu-stable-xenial.list.save
google-chrome.list
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.save
me-davidsansome-ubuntu-clementine-xenial.list
me-davidsansome-ubuntu-clementine-xenial.list.save
michael-gruz-canon-trusty.list.save
noobslab-ubuntu-apps-xenial.list
noobslab-ubuntu-apps-xenial.list.save
noobslab-ubuntu-indicators-xenial.list
noobslab-ubuntu-indicators-xenial.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.distUpgrade
otto-kesselgulasch-gimp-trusty.list.save
rolfbensch-sane-git-trusty.list
rolfbensch-sane-git-trusty.list.distUpgrade
rolfbensch-sane-git-trusty.list.save
webupd8team-ubuntu-gnome3-xenial.list.save
webupd8team-ubuntu-y-ppa-manager-xenial.list
webupd8team-ubuntu-y-ppa-manager-xenial.list.save
webupd8team-y-ppa-manager-trusty.list.distUpgrade
webupd8team-y-ppa-manager-trusty.list.save
xenial-partner.list
xenial-partner.list.save

```

---

### Post by wildmanne39 on 2017-02-13
This is what is in my:
```
cat /etc/apt/sources.list
```
```
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```
I recommend that you go to the link and generate a new list or copy and paste my source list into yours after you delete yours then reload the repositories and update your system then try to install samda using the aptitude command. 
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

Edit:

Also in the:
```
/etc/apt/sources.list.d/
```
you need to remove the trusty repositories.

---

### Post by jgw on 2017-02-13
I want to make sure I am understanding what you want me to do.  You sent me, I think, your own ppa list.  What you want me to do is to install the ppas, in that list but, first, delete all my "other software" ppas (I can do this by simply going to y ppa and backing them all up and deleting them all (?)  I also went to the etc/apt/ directory and found stuff of possible interest (I was trying to look at them and found stuff from samba there as well.  Here is a list of the directory:[http://pastebin.com/JzteHgak](http://pastebin.com/JzteHgak) if you are interested.  

Anyway (I want to do this right).  You want me to save and then delete all my other software ppas and then insert those which you sent to me?  After I accomplish that update the ppas and then run (all or one):
sudo apt-get update 
sudo apt-get upgrade   
sudo apt-get dist-upgrade

then install samba using aptitude?  No reboot?

Oh, synaptic tells me I have the following, under samba, installed (just making sure I am giving you all the info you might need):
libsmbclient
libwbclent0
nautilus-share
samba-common
samba-libs
smbclient
vlc-plugin samba

I am also confused about the "new list" thing.  I have been to that place but have never figured out just what is to be done.  I think I only need to check off all the stuff in the other software section and leave the rest alone?

---

### Post by wildmanne39 on 2017-02-13
The new list has little red question marks, they are help files basically just click on them to learn about each one, put a check by what you want to include in the new list that it will be created for you so you can replace yours with it, please refer to the screenshots. 

Using the list would be my first choice for you to replace your sources list not your sources list.d.

You can use my source list if you want but notice there are not any ppa's in that list, they are in the source list.d file but I only have one, the more you add the more trouble you will have.

I use synaptic package manager, in it you can disable your ppa's by uncheckiing them, anything that says trusty you for sure want to disable or remove, I always remove them but that is my personal preference.
Reload the repos and run an upgrade after the changes then you can try to install samba.

This:
> Oh, synaptic tells me I have the following, under samba, installed (just making sure I am giving you all the info you might need):
libsmbclient
libwbclent0
nautilus-share
samba-common
samba-libs
smbclient
vlc-plugin samba

makes it seem like samba is installed already, that is what mine shows in synaptic and samba is installed.

Do you want to configure samba with a GUI? if so do:
```
sudo apt-get install system-config-samba cifs-utils
```
What happens?




To uncheck the ppa's open synaptic then go to settings>repositories>other software
[ATTACH=CONFIG]273691[/ATTACH][ATTACH=CONFIG]273692[/ATTACH]

---

### Post by jgw on 2017-02-14
Thanks again.  I have tried to simply run samba from a terminal and get:
reg@greg:~$ samba
The program 'samba' is currently not installed. You can install it by typing:
sudo apt install samba

This leads me to believe its not installed (I thought the same as you)  I also include a list, from symantic, as to what is installed under a search for samba.  Everything but samba itself was listed.  I too use symantic (found that I can REALLY screw up things with that <G>)

I am tempted to disable all other ppa's and then do the sudo apt install samba just to see what will happen although I already know that I will probably get the same old errors.  Even if I get samba installed I will have to also install the gui as well (I think).

I couldn't resist and I:
```

greg@greg:~$ sudo aptitude install samba
[sudo] password for greg: 
The following NEW packages will be installed:
  attr{a} libaio1{a} python-ldb{a} python-samba{ab} python-tdb{a} samba{b} 
  samba-common-bin{ab} samba-dsdb-modules{ab} samba-vfs-modules{ab} 
  tdb-tools{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,026 kB of archives. After unpacking 23.5 MB will be used.
The following packages have unmet dependencies:
 python-samba : Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba : Depends: samba-common (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
         Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
         Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-dsdb-modules : Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
                      Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-vfs-modules : Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
 samba-common-bin : Depends: samba-common (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
                    Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     python-samba [Not Installed]                       
2)     samba [Not Installed]                              
3)     samba-common-bin [Not Installed]                   
4)     samba-dsdb-modules [Not Installed]                 
5)     samba-vfs-modules [Not Installed]                  

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         

```

its interesting.  It says "The following actions will resolve these dependencies:" but there are no actions.  Then it asks if I want to accept the solution which, apparently, doesn't exist.  As far as I can tell I seem to be in some sort of version box which I can't get out of.  Very strange.  then it tells me to keep the following packages as they are and lists 5 packages that are not installed.  I am considering going to synaptic and install the specific versions that are missing but I am not sure that those would play with the existing (newer) versions.  

I am just trying to setup a local network.  This used to be simple and almost automatic and I could access all my machines, including the windows machine.  Not any more! <G>

---

### Post by wildmanne39 on 2017-02-14
I believe it is because your sources list is messed up and the sources list.d please do what I asked you to do in the previous post and generate a new list at the link I gave you then replace your source list with it and in the sources list.d remove anything that is trusty unless they are all ppa's then uncheck them in synaptic then do:
```
sudo apt-get update && sudo apt-get upgrade
```
then try to install samba.

To delete your source list do:
```
sudo -H gedit /etc/apt/sources.list
```
or whatever text editor you use when the file opens delete your file and replace it with the new one generated at the link in my previous post if it is to confusing then use my list that I posted here as yours.
Let us know how it goes.

Thanks

---

### Post by jgw on 2017-02-17
Sorry I took so long getting back.  Had to deal with family stuff.

I think I did as you suggested but am not sure.  when I did the sudo apt-get update && sudo apt-get upgrade thing it too a lot of time (over 1/2 an hour)  The file of that process is saved and has 1599 lines in it.  I have 3 files which are:
stuffdone.txt     run up to the update/upgrade thing                  [http://pastebin.com/vA0Cch5K](http://pastebin.com/vA0Cch5K)
stuff2.txt          the actual update/upgrade thing                      [http://pastebin.com/k8XcatUA](http://pastebin.com/k8XcatUA)
stuff3samba.txt when I enter 'samba' in a terminal                   [http://pastebin.com/GXH4CgQ2](http://pastebin.com/GXH4CgQ2)
(I think it installed but may still need help) 

I suspect this is just too much stuff to put into an email so I will put it up on pastbin and you can have at them.  (be kind <G>)

---

### Post by wildmanne39 on 2017-02-17
Yes it installed and many more updates that is great, there were a few things that did not upgrade please do:
```
sudo apt-get update && sudo apt-get upgrade
```
then post the results here and let's see what did not upgrade and the error's.
I know there were some gpg key errors but it is hard to tell which ones with all the information at pastebin.

---

### Post by jgw on 2017-02-18
Thank you for your help and time.  I ran your suggestion.  I actually did it two times.  After the first (see below) I ran the y ppa manager and did the missing gpg and the fix gpg thing, reloaded, and then ran it again.  It did differently on the second run.

```

greg@greg:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for greg: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]   
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:4 http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu xenial InRelease
Hit:6 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial InRelease 
Get:7 http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease [17.5 kB]      
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:5 http://screenshots.getdeb.net xenial-getdeb InRelease [8,139 B]          
Ign:7 http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease                
Hit:9 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu xenial InRelease
Ign:5 http://screenshots.getdeb.net xenial-getdeb InRelease
Hit:10 http://ppa.launchpad.net/noobslab/apps/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial InRelease
Fetched 230 kB in 1s (143 kB/s)                     
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F13930B14BB9F05F
W: The repository 'http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://screenshots.getdeb.net xenial-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: The repository 'http://archive.getdeb.net/ubuntu xenial-getdeb InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic sabnzbdplus
  sabnzbdplus-theme-plush sabnzbdplus-theme-smpl
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
.....
greg@greg:~$ sudo apt-get update && sudo apt-get upgrade
Ign:1 http://dl.google.com/linux/talkplugin/deb stable InRelease
Hit:2 http://dl.google.com/linux/talkplugin/deb stable Release                                                                               
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                   
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                 
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                                                                    
Hit:7 http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu xenial InRelease                                         
Hit:9 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial InRelease                            
Hit:10 http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease                                                                           
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                               
Hit:12 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu xenial InRelease                       
Hit:8 http://screenshots.getdeb.net xenial-getdeb InRelease                                                 
Hit:13 http://ppa.launchpad.net/noobslab/apps/ubuntu xenial InRelease                                       
Hit:14 http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial InRelease           
Fetched 204 kB in 1s (127 kB/s)                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic sabnzbdplus sabnzbdplus-theme-plush sabnzbdplus-theme-smpl
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.


```

...

---

### Post by wildmanne39 on 2017-02-19
It is looking a lot better, apparently from 16.04 and newer we need to run an update like this:
```
sudo apt update
sudo apt upgrade
```
See if that gets rid of those packages being kept back.

Either way this thread is solved because you have samba now installed.

---

### Post by jgw on 2017-02-19
Thanks again.

I ran them and got:

```

greg@greg:~$ sudo apt update
[sudo] password for greg: 
Ign:1 http://dl.google.com/linux/talkplugin/deb stable InRelease
Hit:2 http://dl.google.com/linux/talkplugin/deb stable Release                 
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]   
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu xenial InRelease 
Hit:10 http://ppa.launchpad.net/jcfp/ppa/ubuntu xenial InRelease               
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]   
Hit:7 http://screenshots.getdeb.net xenial-getdeb InRelease                    
Hit:12 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/noobslab/apps/ubuntu xenial InRelease          
Hit:14 http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial InRelease    
Fetched 204 kB in 1s (119 kB/s)                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
greg@greg:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libavahi-compat-libdnssd1 libjs-bootstrap libjs-jquery-ui libjs-moment
  linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic
  linux-image-4.4.0-47-generic linux-image-extra-4.4.0-47-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libavahi-compat-libdnssd1 libjs-bootstrap libjs-jquery-ui libjs-moment
The following packages have been kept back:
  sabnzbdplus sabnzbdplus-theme-smpl
The following packages will be upgraded:
  snap-confine snapd
2 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 8,782 kB/9,522 kB of archives.
After this operation, 3,242 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snapd amd64 2.22.3 [8,741 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snap-confine amd64 2.22.3 [41.5 kB]
Fetched 8,782 kB in 6s (1,421 kB/s)                                            
Selecting previously unselected package libavahi-compat-libdnssd1:amd64.
(Reading database ... 335050 files and directories currently installed.)
Preparing to unpack .../libavahi-compat-libdnssd1_0.6.32~rc+dfsg-1ubuntu2_amd64.deb ...
Unpacking libavahi-compat-libdnssd1:amd64 (0.6.32~rc+dfsg-1ubuntu2) ...
Selecting previously unselected package libjs-bootstrap.
Preparing to unpack .../libjs-bootstrap_3.3.6+dfsg-1_all.deb ...
Unpacking libjs-bootstrap (3.3.6+dfsg-1) ...
Selecting previously unselected package libjs-jquery-ui.
Preparing to unpack .../libjs-jquery-ui_1.10.1+dfsg-1_all.deb ...
Unpacking libjs-jquery-ui (1.10.1+dfsg-1) ...
Selecting previously unselected package libjs-moment.
Preparing to unpack .../libjs-moment_2.11.0+ds-1_all.deb ...
Unpacking libjs-moment (2.11.0+ds-1) ...
Preparing to unpack .../snapd_2.22.3_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket
Unpacking snapd (2.22.3) over (2.22.2) ...
Preparing to unpack .../snap-confine_2.22.3_amd64.deb ...
Unpacking snap-confine (2.22.3) over (2.22.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libavahi-compat-libdnssd1:amd64 (0.6.32~rc+dfsg-1ubuntu2) ...
Setting up libjs-bootstrap (3.3.6+dfsg-1) ...
Setting up libjs-jquery-ui (1.10.1+dfsg-1) ...
Setting up libjs-moment (2.11.0+ds-1) ...
Setting up snap-confine (2.22.3) ...
Setting up snapd (2.22.3) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...

```
..

Then I ran synaptic.  Fixed any packages, updated one package, installed 2 other packages and then deleted 3 others (I had previously ran sudo apt autodelete).  I had planned to save the process and add it to this but I had synaptic configured wrong - sorry.............

Interesting times <G>

---

### Post by wildmanne39 on 2017-02-19
All looks well, I think you can mark this solved.
I am glad it is working!
Enjoy!

---

### Post by jgw on 2017-02-19
Thank you for all the help.  It remains a mystery but I learns stuff! - thanks again (marked it solved <G>)

---

### Post by wildmanne39 on 2017-02-19
Your welcome!
Enjoy!

---

