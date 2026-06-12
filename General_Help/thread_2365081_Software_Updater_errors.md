---
title: "Software Updater errors"
date: 2017-07-02
forum: General Help
---

### Post by jaren2004 on 2017-07-02
Whenever i try to update my computer it says failed to download repository information
Here are the details
E:The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu zesty Release' does not have a Release file.

Pls Help

---

### Post by CatKiller on 2017-07-02
[https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)
>                          Wine Team PPA

                                                                          
             PPA description

   
    !!! PLEASE NOTE THAT THIS REPOSITORY IS DEPRECATED !!!
 In fact, it's double deprecated -- it was replaced by the Wine Builds PPA, which was then itself replaced.
 For more information, please see:
     [https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html](https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html)


---

### Post by jaren2004 on 2017-07-02
I dont get what im suppose to do with that link

---

### Post by johndough2 on 2017-07-02
Hi

I think the repository is dead and defunct.  There is a new repository to visit.

Therefore replace your old repo "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu zesty Release"
 and read [https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html](https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html)

""- We already added the new Ubuntu repository to the CDN, so that users can
start switching by now and don't have to wait till the next release. The
repository can be added using the following commands:

wget [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
sudo apt-key add Release.key
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'

To make sure that all users will be informed about this change, I will
push at least one additional update (Wine 2.5) to the PPA that displays
a warning during the package upgrade containing the necessary
instructions (I hope this also works on Ubuntu, I have only tested it on
Debian so far). This means users will have at least two weeks to switch
from the PPA to the new repository - maybe a bit more if we push
additional builds. -""

---

### Post by jaren2004 on 2017-07-03
Well i tried doing that but it didn't really solve the problem it still says Failed to download repository Information

---

### Post by RobGoss on 2017-07-03
Hello and welcome, Got to **software & updates,** choose** other software**, them remove the **PPA** that's returning the error message

Then try update the system again is see how it works

---

### Post by jaren2004 on 2017-07-03
i tried that but it didn't work too

---

### Post by jaren2004 on 2017-07-03
sorry that it's so hard to solve
btw

---

### Post by deadflowr on 2017-07-03
Please post the output for
```
sudo apt-get update
```
then we can see what is actually going on...

---

### Post by RobGoss on 2017-07-03
> **jaren2004 said:**
> sorry that it's so hard to solve
btw

No need to be sorry that's what the forums are for to solve problems

---

### Post by jaren2004 on 2017-07-04
oh ok 
btw heres the what it said when i updated it
```
Hit:1 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty InRelease
Get:2 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates InRelease [89.2 kB]         
Get:3 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-security InRelease [89.2 kB]        
Get:4 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-backports InRelease [89.2 kB]       
Get:5 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates/main amd64 DEP-11 Metadata [41.9 kB]
Get:6 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata [57.6 kB]
Get:7 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates/universe DEP-11 64x64 Icons [58.7 kB]
Get:8 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:9 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-security/main amd64 DEP-11 Metadata [5,816 B]
Hit:10 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) zesty InRelease                
Get:11 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-security/universe amd64 DEP-11 Metadata [8,908 B]
Get:12 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-backports/universe amd64 DEP-11 Metadata [4,672 B]
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease                     
Get:14 [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease [3,644 B]
Ign:14 [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease
Ign:15 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:16 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Hit:18 [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                             
Hit:19 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                          
Fetched 451 kB in 6s (73.3 kB/s)                                               
Reading package lists... Done
W: GPG error: [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
W: The repository 'https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2017-07-04
Try this command:
```
wget https://download.01.org/gfx/RPM-GPG-GROUP-KEY-ilg -O - | sudo apt-key add -
```
then re-run the update command again.

---

### Post by jaren2004 on 2017-07-04
Btw thanks for the help

also sorry i accidentally posted it again a second time cause my internet was slow so i thought i didnt post it

the actual thing the came up the second time was
```
Hit:1 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty InRelease
Hit:2 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-updates InRelease                                                                                                                                    
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                    
Hit:4 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-security InRelease                                                                                                                                   
Hit:5 [http://mirror.pregi.net/ubuntu](http://mirror.pregi.net/ubuntu) zesty-backports InRelease                                                                                                                                  
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                                         
Hit:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) zesty InRelease                                                                                                                     
Hit:8 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                           
Hit:10 [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                                             
Hit:11 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease               
Get:12 [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease [3,644 B]
Ign:12 [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease
Fetched 3,644 B in 1s (3,225 B/s)
Reading package lists... Done
W: GPG error: [https://download.01.org/gfx/ubuntu/17.04/main](https://download.01.org/gfx/ubuntu/17.04/main) zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
W: The repository 'https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2017-07-04
What was the actual output for the command I gave you to run?

---

### Post by jaren2004 on 2017-07-06
the second one sorry i accidentally got the wrong output

---

