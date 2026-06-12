---
title: "Sigil install error in Ubuntu 12.04"
date: 2013-07-18
forum: General Help
---

### Post by michaelbr on 2013-07-18
I have a new Ubuntu 12.04 installation dual boot with Windows XP, when I tried to use Ubuntu Software Center to install SIgil, I got the following error message:
The following packages have unmet dependencies:

Package dependencies cannot be resolved
sigil: Depends: libboost-filesystem1.46.1 (>= 1.46.1-1) but 1.46.1-7ubuntu3 is to be installed
       Depends: libboost-regex1.46.1 (>= 1.46.1-1) but 1.46.1-7ubuntu3 is to be installed
       Depends: libboost-system1.46.1 (>= 1.46.1-1) but 1.46.1-7ubuntu3 is to be installed
       Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
       Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
       Depends: libqt5concurrent5 (>= 5.0.2) but it is not going to be installed
       Depends: libqt5core5 (>= 5.0.2) but it is not going to be installed
       Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed
       Depends: libqt5network5 (>= 5.0.2) but it is not going to be installed
       Depends: libqt5printsupport5 (>= 5.0.2) but it is not going to be installed
       Depends: libqt5webkit5 but it is not going to be installed
       Depends: libqt5widgets5 (>= 5.0.2) but it is not going to be installed
       Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
       Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

How do I solve those dependencies problems? Why those packages cannot be installed? How can I check or correct those problems?

---

### Post by HiImTye on 2013-07-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
version problems usually result from using PPAs that don't stay up to date, did you add any?

---

### Post by michaelbr on 2013-07-18
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
version problems usually result from using PPAs that don't stay up to date, did you add any?

Thanks for your prompt reply, I'm pretty sure that I did, after I got the error message from using PPAs, I removed the PPA from Software source in USC (Ubuntu Software Center), but still I got the same error, what can I do to remove completely the previous install? The first time I used command line, then UBC, both got similar error messages.

---

### Post by HiImTye on 2013-07-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
add it again, then use ppa-purge```
sudo add-apt-repository <PPA>
sudo apt-get install ppa-purge
sudo apt-get update
sudo ppa-purge <PPA>
```

---

### Post by Brian1215 on 2013-07-18
Missing dependencies are all Qt5.x which isn't in the repositories. 
I was using Sigil 0.6.2 installed with a ppa that was later removed and also have 0.7.1 installed with Wine. There is also an unofficial .deb for 0.7.2 at [http://www.mobileread.com/forums/showthread.php?t=211754](http://www.mobileread.com/forums/showthread.php?t=211754) which installs and seems to run fine in 12.04.

---

### Post by michaelbr on 2013-07-19
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
add it again, then use ppa-purge```
sudo add-apt-repository <PPA>
sudo apt-get install ppa-purge
sudo apt-get update
sudo ppa-purge <PPA>
```

Thanks HiImTye, I'll give it a try and report back later.

---

### Post by michaelbr on 2013-07-19
> **Brian1215 said:**
> Missing dependencies are all Qt5.x which isn't in the repositories. 
I was using Sigil 0.6.2 installed with a ppa that was later removed and also have 0.7.1 installed with Wine. There is also an unofficial .deb for 0.7.2 at [http://www.mobileread.com/forums/showthread.php?t=211754](http://www.mobileread.com/forums/showthread.php?t=211754) which installs and seems to run fine in 12.04.

Thanks Brian1215 for this tip, I'll fix the error message problem first and give it a try with unofficial .deb.

---

### Post by michaelbr on 2013-07-19
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
add it again, then use ppa-purge```
sudo add-apt-repository <PPA>
sudo apt-get install ppa-purge
sudo apt-get update
sudo ppa-purge <PPA>
```

I'm afraid I really messed up this time, when I did sudo apt-get update, I got the following errors:
```

.....
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
.....
W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/source/Sources  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
How can I fix those errors? I tried to remove Ubuntu Tweak from Synaptic, then I got an error saying couldn't find package, so I added the package back and tried to remove the ppa using ppa-purge, then added Ubuntu Tweak back through Synaptic, but the error is still there.

---

### Post by Brian1215 on 2013-07-19
Don't Panic. I've got the same or similar errors when I tried those addresses just now via several routes. Try again later. Looks like a server problem not yours.

---

### Post by michaelbr on 2013-07-19
> **Brian1215 said:**
> Don't Panic. I've got the same or similar errors when I tried those addresses just now via several routes. Try again later. Looks like a server problem not yours.

Thanks Brian1215 for the tip, I'll try later and see what happens.

---

### Post by Brian1215 on 2013-07-20
Let me try to bring this thread and your other at [http://www.mobileread.com/forums/showthread.php?t=218270](http://www.mobileread.com/forums/showthread.php?t=218270) together.

After running sudo ppa-purge <PPA> it is necessary to run 
sudo apt-get update

[http://www.upubuntu.com/2012/02/how-to-remove-purge-unofficial-ppa.html](http://www.upubuntu.com/2012/02/how-to-remove-purge-unofficial-ppa.html)

On the terminal type in the following commands (one line at a time) >>
sudo apt-get update -f
sudo apt-get upgrade -f
sudo apt-get install synaptic
(from [http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager](http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager))

In Synaptic>Settings>Repositories check that Software Sources shows that Main, Universe, Multiverse and Canonical Partners are ticked.

All being well this should fix any errors. (I notice that some of the errors that you saw earlier are still appearing – ignore them for now)

Now follow the advice of DiapDealer and download and install his .deb (double click the downloaded file). I've just (almost – waiting for last minute news) completed this month's edition of a magazine using Sigil installed using it.

Like many others I use Synaptic as I find the software center as useful as a chocolate teapot.

---

### Post by pavelpetr-cz on 2013-11-09
Hi,

I tried to install unsuccessfully Sigil too from source 
```

ppa:sunab/sigil-git
```

 It gave me the same error with wrong dependencies as you. After that I noticed in command line that this software is using Qt5. 

So I add 

```
ppa:ubuntu-sdk-team/ppa
```

and then ran

```
sudo apt-get update
sudo apt-get install sigil 
```

And it worked. So you can try it too. I am using updated version of Ubuntu 12.04 LTS.

---

### Post by michaelbr on 2013-11-11
> **pavelpetr-cz said:**
> Hi,

I tried to install unsuccessfully Sigil too from source 
```

ppa:sunab/sigil-git
```

 It gave me the same error with wrong dependencies as you. After that I noticed in command line that this software is using Qt5. 

So I add 

```
ppa:ubuntu-sdk-team/ppa
```

and then ran

```
sudo apt-get update
sudo apt-get install sigil 
```

And it worked. So you can try it too. I am using updated version of Ubuntu 12.04 LTS.
Thanks for your tips, right now I'm replacing my old laptop with a new one, and having trouble with Ubuntu install, as soon as I have it installed, I'll give it a try.

---

