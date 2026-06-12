---
title: "Seamonkey doesn't run: Lubuntu 13.10"
date: 2013-10-18
forum: General Help
---

### Post by vasa1 on 2013-10-18
*I should have mentioned that I'm now using Lubuntu 13.10 **64-bit**. The main download link on the seamonkey-project page is for **32-bit**. Installing 32-bit Seamonkey on 64-bit Lubuntu seems to be rocket science. I found a 64-bit "contributed" build that installed smoothly. Shantiq has had success with a ppa as described in the second post*.  

I downloaded Seamonkey from [http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/). After extracting **seamonkey-2.21.tar.bz2**, I used **sudo mv seamonkey /usr/local/seamonkey** to move the Seamonkey folder.

There are two executables and one script in that folder. 

```
-rwxr-xr-x  1 vasa1 vasa1     8915 Sep 17 00:01 run-mozilla.sh*
-rwxr-xr-x  1 vasa1 vasa1   760868 Sep 17 01:16 seamonkey*
-rwxr-xr-x  1 vasa1 vasa1   760872 Sep 17 01:16 seamonkey-bin*

```

But double-clicking on either executable gives a pop-up window with:

> Failed to execute file "seamonkey".
Failed to execute child process "/usr/local/seamonkey/seamonkey" (No such file or directory).


Trying **run-mozilla.sh** gives:
```
run-mozilla.sh: Cannot execute .

``` 

And running seamonkey or seamonkey-bin in the terminal gives:
```
vasa1@vasa1-Inspiron-1545:/usr/local/seamonkey$ seamonkey
bash: /usr/local/seamonkey/seamonkey: No such file or directory
vasa1@vasa1-Inspiron-1545:/usr/local/seamonkey$ seamonkey-bin
bash: /usr/local/seamonkey/seamonkey-bin: No such file or directory
vasa1@vasa1-Inspiron-1545:/usr/local/seamonkey$ 

```
I had no problem with Lubuntu 13.04 and Seamonkey from the same source.

I modified `/etc/environment` to this:
```
vasa1@vasa1-Inspiron-1545:/usr/local/seamonkey$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/local/seamonkey"

```
but no joy even after a reboot.

Any ideas?

---

### Post by shantiq on 2013-10-21
Hi Vasa    the old route does not work after pangolin or anyway i do not howto ::]]


so thanx to Richard[ here]("http://ubuntuforums.org/showthread.php?t=1961934&p=11869656#post11869656")   and the info is here [too]("http://www.ubuntuupdates.org/ppa/ubuntuzilla?dist=all")


there is another route:


in terminal:


**1.  **```
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29


```



**2**. ```
  [noparse]echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" \| sudo tee -a /etc/apt/sources.list > /dev/null [/noparse]
```



**3.  **download deb for [32-bit]("http://softlayer.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/s/seamonkey-mozilla-build/seamonkey-mozilla-build_2.21-0ubuntu1_i386.deb")  or [64-bit]("http://softlayer.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/s/seamonkey-mozilla-build/seamonkey-mozilla-build_2.21-0ubuntu1_amd64.deb")   from[ this page]("http://www.ubuntuupdates.org/package/ubuntuzilla/all/main/base/seamonkey-mozilla-build")


**4. **then install deb with** software centre** or command line

```
sudo dpkg -i seamonkey-mozilla-build_2.21-0ubuntu1_amd64.deb
```


and there you have it for 13.10 ...     start with```
 seamonkey
``` from command line or from dash after reload or lock to launcher

---

### Post by vasa1 on 2013-10-21
> **shantiq said:**
> Hi Vasa    the old route does not work after pangolin or anyway i do not howto ::]]
...
Shantiq, thanks for replying. What problem did you face? I could use your original solution in 12.10 **and** in 13.04.

If there's is no other way, I'll use the ppa you suggested but I'd still like to figure out *why* I can't install Seamonkey as before.

---

### Post by shantiq on 2013-10-22
ha ok Vasa    i must confess i had not used it for a while on 13.10 it said this when i tried to start it

```
/usr/local/seamonkey/seamonkey
XPCOMGlueLoad error for file /usr/local/seamonkey/libxul.so:
libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
Couldn't load XPCOM.


```

so i installed [http://packages.ubuntu.com/saucy/libdbus-glib-1-2](http://packages.ubuntu.com/saucy/libdbus-glib-1-2)


and still would not start so i went to the PPA
surely someone with more knowledge will easily crack it
PPA is ok tho...

---

### Post by vasa1 on 2013-11-09
@shantiq, I omitted to mention that, for 13.10, I'm now using 64-bit Lubuntu. It appears that the Seamonkey from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) is 32-bit. I asked for guidance over here: [http://unix.stackexchange.com/q/99562/15760](http://unix.stackexchange.com/q/99562/15760) and the solution that works is posted as my answer: 

> I searched the web for "can seamonkey be installed on 64-bit linux".

One of the results was this: [http://tutorialforlinux.com/2013/10/31/how-to-install-seamonkey-on-xubuntu-13-10-saucy-64bit-linux/](http://tutorialforlinux.com/2013/10/31/how-to-install-seamonkey-on-xubuntu-13-10-saucy-64bit-linux/). It pointed to [http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.22/contrib/seamonkey-2.22.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.22/contrib/seamonkey-2.22.en-US.linux-x86_64.tar.bz2).

That worked.


---

### Post by shantiq on 2013-11-09
excellent Vasa!    been using the PPA myself so will stay with that but good you found a route through

---

### Post by vasa1 on 2013-11-09
> **shantiq said:**
> excellent Vasa!    been using the PPA myself so will stay with that but good you found a route through
Thanks! That same link to 64-bit Seamonkey is on the seamonkey project pages as well: one can get to it by clicking on [http://www.seamonkey-project.org/releases/#contrib](http://www.seamonkey-project.org/releases/#contrib).

---

