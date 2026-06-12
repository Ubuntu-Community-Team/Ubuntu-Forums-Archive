---
title: "Unmet dependencies 12.04 LTS"
date: 2013-07-12
forum: General Help
---

### Post by Mirgeee on 2013-07-12
Hi,

when I try to run apt-get, I get a message that libgl1-mesa-dev, libgl1-mesa-glx and libgl1-mesa-glx:i386 have unmet dependencies. I did some research and found out that the issue is that while I am using 64bit system, some applications are trying to download and use 32bit libraries. I guess it is basically solved in the following threads, however I am too much of a newbie to make sense of it. Could you please help?

[http://ubuntuforums.org/showthread.php?t=2122554](http://ubuntuforums.org/showthread.php?t=2122554)
[http://ubuntuforums.org/showthread.php?p=12587000#post12587000](http://ubuntuforums.org/showthread.php?p=12587000#post12587000)
( [http://ubuntuforums.org/showthread.php?t=2073770](http://ubuntuforums.org/showthread.php?t=2073770) )

Here is the terminal output, sorry it is in Czech, but due to the problem I can not change the language...

```

$ sudo apt-get upgrade
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;ím strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Pro opravení m&#367;&#382;ete spustit &#8222;apt-get -f install&#8220;.
Následující balíky mají nespln&#283;né závislosti:
 libgl1-mesa-dev : Závisí na: mesa-common-dev (= 8.0.4-0ubuntu0.4) nebo
                                mesa-common-dev-lts-quantal ale není nainstalovaný nebo
                                mesa-common-dev-lts-raring ale nedá se nainstalovat
 libgl1-mesa-glx : Závisí na: libglapi-mesa (= 8.0.4-0ubuntu0.4)
 libgl1-mesa-glx:i386 : Závisí na: libglapi-mesa:i386 (= 8.0.4-0ubuntu0.4)
E: Nespln&#283;né závislosti. Zkuste pou&#382;ít -f.

```

EDIT:
Here is what outputs software-center, in english:
```

installArchives() failed: dpkg: dependency problems prevent configuration of libgl1-mesa-glx:i386: 
 libgl1-mesa-glx:i386 depends on libglapi-mesa (= 8.0.4-0ubuntu0.4); however: 
  Version of libglapi-mesa:i386 on system is 8.0.4-0ubuntu0.6. 
dpkg: error processing libgl1-mesa-glx:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgl1-mesa-glx: 
 libgl1-mesa-glx depends on libglapi-mesa (= 8.0.4-0ubuntu0.4); however: 
  Version of libglapi-mesa on system is 8.0.4-0ubuntu0.6. 
dpkg: error processing libgl1-mesa-glx (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgl1-mesa-dev: 
 libgl1-mesa-dev depends on mesa-common-dev (= 8.0.4-0ubuntu0.4) | mesa-common-dev-lts-quantal | mesa-common-dev-lts-raring; however: 
  Version of mesa-common-dev on system is 8.0.4-0ubuntu0.6. 
  Package mesa-common-dev-lts-quantal is not installed. 
  Package mesa-common-dev-lts-raring is not installed. 
 libgl1-mesa-dev depends on libgl1-mesa-glx (= 8.0.4-0ubuntu0.4) | libgl1-mesa-glx-lts-quantal | libgl1-mesa-glx-lts-raring; however: 
  Package libgl1-mesa-glx is not configured yet. 
  Package libgl1-mesa-glx-lts-quantal is not installed. 
  Package libgl1-mesa-glx-lts-raring is not installed. 
dpkg: error processing libgl1-mesa-dev (--confNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
igure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 libgl1-mesa-glx:i386 
 libgl1-mesa-glx 
 libgl1-mesa-dev 
dpkg: dependency problems prevent configuration of libgl1-mesa-glx:i386: 
 libgl1-mesa-glx:i386 depends on libglapi-mesa (= 8.0.4-0ubuntu0.4); however: 
  Version of libglapi-mesa:i386 on system is 8.0.4-0ubuntu0.6. 
dpkg: error processing libgl1-mesa-glx:i386 (--configure): 
 dependency problems - leaving unconfigured 

```

---

### Post by slickymaster on 2013-07-12
See [this]("http://ubuntuforums.org/showthread.php?t=1940733&p=11766164&viewfull=1#post11766164"), please.

---

### Post by Mirgeee on 2013-07-12
This method didn't work. That's strange, he was experiencing almost the same problem! Still says:

After running ```
 dpkg --force-depends --purge libgl1-mesa-glx 
``` I get message that /usr/lib/x86_64-linux-gnu/xorg is not empty, so will not be removed, which may be relevant...?

---

### Post by Mirgeee on 2013-07-12
Sorry, I applied the command to all the packages concerned, and everythings works now. Thank you!

---

### Post by fantab on 2013-07-12
Remove the errant packages and then re-install if need be. Try the following:

```
sudo dpkg --purge libgl1-mesa-dev libgl1-mesa-glx libgl1-mesa-glx:i386
sudo apt-get remove --purge libgl1-mesa-dev libgl1-mesa-glx libgl1-mesa-glx:i386
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get -f install
sudo apt-get update && sudo apt-get dist-upgrade
```

To re-install:
```
sudo apt-get install libgl1-mesa-dev libgl1-mesa-glx libgl1-mesa-glx:i386
```

Good Luck...

---

### Post by slickymaster on 2013-07-12
Thing is you are running a 64-bit system (amd64) and some application pulls a whole bunch of 32-bit libraries. See [this post]("http://ubuntuforums.org/showthread.php?p=12587000#post12587000").

---

