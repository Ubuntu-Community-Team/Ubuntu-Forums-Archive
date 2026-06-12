---
title: "Get error when trying to find software updates."
date: 2013-05-31
forum: General Help
---

### Post by TCChilds on 2013-05-31
Every time the system tries to check for software updates I get an error.  This is only over the last few weeks.  Prior all was well.

This is the error:

E:GPG error: [http://linux.ntuoss.org](http://linux.ntuoss.org) raring-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

I don't know what it means or how to fix it.  

Thanks in advance for any and all help.

Craig

---

### Post by plucky on 2013-06-01
> **TCChilds said:**
> Every time the system tries to check for software updates I get an error.  This is only over the last few weeks.  Prior all was well.

This is the error:

E:GPG error: [http://linux.ntuoss.org](http://linux.ntuoss.org) raring-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

I don't know what it means or how to fix it.  

Thanks in advance for any and all help.

Craig


Did you add [http://linux.ntuoss.org](http://linux.ntuoss.org) as a repository in your **Software Sources**?

Try disabling it as a source in **Software Sources** and then run ```
sudo apt-get update
``` from a terminal and post the result.

Good Luck

---

### Post by TCChilds on 2013-06-01
Plucky,

Thanks for the suggestions. 
 
I did not add [http://linux.ntuross.org](http://linux.ntuross.org) as a software source.  It is not listed as a separate software source.

I tried the terminal update and it got the same errors.

Get:1 [http://linux.ntuoss.org](http://linux.ntuoss.org) raring Release.gpg [9,320 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Get:2 [http://linux.ntuoss.org](http://linux.ntuoss.org) raring-updates Release.gpg [9,210 B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Get:3 [http://linux.ntuoss.org](http://linux.ntuoss.org) raring-backports Release.gpg [9,330 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Get:4 [http://linux.ntuoss.org](http://linux.ntuoss.org) raring-security Release.gpg [9,329 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Get:5 [http://linux.ntuoss.org](http://linux.ntuoss.org) raring Release [9,316 B]                         
Ign [http://linux.ntuoss.org](http://linux.ntuoss.org) raring Release                                     
E: GPG error: [http://linux.ntuoss.org](http://linux.ntuoss.org) raring Release: The following signatures were invalid: NODATA 1 NODATA 2

Thanks again for the help but need to try something else.

Craig

---

### Post by oldos2er on 2013-06-01
I suggest you go to [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) and regenerate a new sources.list. "[http://linux.ntuoss.org](http://linux.ntuoss.org)" isn't a valid repository.

---

### Post by TCChilds on 2013-06-03
oldos2er,

Thanks for the help.  Have created the list but can't change it.  Only the root can edit and change it.  I am the root but must be doing something wrong as it does not see me as the root.

And not sure what to do with the keys or synaptic data.

Sorry I don't understand how to do all this but I would really appreciate your help.

Craig

---

### Post by oldos2er on 2013-06-03
Move your old sources.list to a backup copy ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
``` Run ```
gksudo gedit
``` in a terminal, copy the newly generated list into it, then click File, Save as, type in /etc/apt/sources.list
Close gedit, run ```
sudo apt-get update
```

An alternative method to do the same thing is to open Synaptic, click Settings, Repositories, and copy the "Alternate layout for Synaptic" repo data one line at a time. You can also remove "[http://linux.ntuoss.org](http://linux.ntuoss.org)" while you're there. 

If you need to add any GPG keys post back and we'll deal with it.

---

### Post by TCChilds on 2013-06-03
Oldos2er,

Thanks for the update.  Making progress.  In terminal got these errors.

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0

Got errors when trying the software updater.  Found I had selected a number of source code repositories.  So I unchecked them.  

Updater could not get some info I guess because of no key.

So it looks like I need to get the keys.

Sorry to be such a problem but I really appreciate the help.

Craig

---

### Post by TCChilds on 2013-06-03
Sorry,

That is the key info.  here is the error.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3BDAAC08614C4B38
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1773AF13B1510FD
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B302120208A255AF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D45DF2E8FC91AE7E
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5AF549300FEB6DD9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)  Something wicked happened resolving 'deb.opera.com:http' (-11 - System error)


E: Some index files failed to download. They have been ignored, or old ones used instead.


update crashes because it had Error authenticating some packages.

---

### Post by oldos2er on 2013-06-04
Try ```
sudo apt-key update
``` first, if that doesn't get you all the keys you need, run   ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` replace KEYID with the alphanumeric string shown after NO_PUBKEY. Run ```
sudo apt-get update
``` again. Incidentally, you can still install packages with *sudo apt-get install foo* without the gpg keys, you'll just get authentication warnings.

Let me know how it goes.

---

### Post by TCChilds on 2013-06-04
Oldos2er,

Thanks for all your help.  Seems to be working.

So thanks again.

Craig

---

### Post by oldos2er on 2013-06-04
You're welcome. Enjoy Ubuntu!

---

