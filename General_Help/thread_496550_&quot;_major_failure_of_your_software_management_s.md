---
title: "&quot; major failure of your software management system&quot;"
date: 2007-07-09
forum: General Help
---

### Post by Confuzzled on 2007-07-09
Hi,

I'm running Xubuntu, which I installed using *xubuntu-7.04-desktop-i386.iso*. The package manager has worked up until now.

I attempted to use the "Synaptic Package Manager" to install KDevelop, and possibly also a JAVA plugin for Mozilla (I can't remember). It froze for a long time, so I went off to browse the web. Ten minutes later, I realized I was not able to modify any files on my desktop. I kept receiving an error message telling me it was a read-only file system. 

I then also noticed that the Synaptic Package Manager had stopped attempting to install the software, and had some error message I cannot remember.

I tried rebooting the computer hoping to then be be able to make changes to files on my desktop. Xubuntu started to load, but didn't get to the point of having a GUI, It told me to run the "fsck" command (exact name might be wrong), which I did, and hit "y" for all the prompts, since I didn't understand any of them. Now I can get back into the GUI, and edit files on my desktop, but the package manager wont work.

When I open *Applications>Systems>Synaptic Package Manager*, I get the error message: 
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


When I attempt to run *dpkg --configure -a* I get the error message:
> dpkg: parse error, in file `/var/lib/dpkg/status' near line 3850:
 missing package name


Here is line 3850, and two lines before and after it (the line itself is blank):

> Type: text
Owners: xserver-xorg/config/monitor/default-identifier

Name: xserver-xorg/config/monitor/horiz-sync
Description: Monitor's horizontal sync range:

When I open *Applications>Systems>Add/Remove*, I get the error message: 
> 
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I attempt to run *sudo apt-get update*, this is the output:
> 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US


<edited for brevity>

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 2s (1B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Any help is very welcome. 

p.s. I just installed Ubuntu two days ago. I'm new to Linux.

---

### Post by smoker on 2007-07-09
>  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  			 		

did you try the 'dpkg --configure -a' to correct?

---

### Post by r0ck80y on 2007-07-09
Try this command:
```
sudo dpkg --clear-avail
```
Then run apt-get again

---

### Post by Confuzzled on 2007-07-09
> **r0ck80y said:**
> Try this command:
```
sudo dpkg --clear-avail
```
Then run apt-get again
I tried it, but the apt-get failed the same way again

> **smoker said:**
> did you try the 'dpkg --configure -a' to correct?
Yes. I said so in my first post.

The problem is still there, but thanks both for trying.

---

### Post by wj32 on 2007-07-09
Try and replace that line with

Package: horiz-sync

and try again

---

### Post by Confuzzled on 2007-07-10
> **wj32 said:**
> Try and replace that line with

Package: horiz-sync

and try again

Now it gives me the error message:
```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 3852 package `horiz-sync':
 duplicate value for user-defined field `Name'
```

thanks anyway.

---

### Post by Confuzzled on 2007-07-10
Is there anything I can do at all?

I heard Ubuntu doesn't yet have an equivalent to Window's System Restore, but what about just uninstalling and reinstalling the package manager? Or is there a better way, as I don't have a clue how to reinstall it.:-({|=

---

### Post by Confuzzled on 2007-07-10
bump. Sorry, but I have no choice. Without package manager, I'm lost.

---

### Post by Confuzzled on 2007-07-11
bump

---

### Post by Rui Pais on 2007-07-11
> **Confuzzled said:**
> 
Here is line 3850, and two lines before and after it (the line itself is blank):
Type: text
Owners: xserver-xorg/config/monitor/default-identifier

Name: xserver-xorg/config/monitor/horiz-sync
Description: Monitor's horizontal sync range:

Hi,
that format as nothing to do with dkpg/status file. 
You must have a borked file :(

Try to use the backup (hoping is not borked too):
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-BROKED
sudo cp -a /var/lib/dpkg/status-old /var/lib/dpkg/status

```
good luck

---

### Post by Confuzzled on 2007-07-11
Hurray! That allowed me to then run "dpkg --configure -a", which then fixed my package manager. You sir, and your creepy *** avatar, are my savior. Thanks a lot.

---

### Post by Rui Pais on 2007-07-12
> **Confuzzled said:**
> Hurray! That allowed me to then run "dpkg --configure -a", which then fixed my package manager. You sir, and your creepy *** avatar, are my savior. Thanks a lot.

No prob :)

Well i wanted an orangutan, but they run out of stock at pet store... i was left with that filthy creature that do any smart tricks for fresh sardines. :lol:

---

