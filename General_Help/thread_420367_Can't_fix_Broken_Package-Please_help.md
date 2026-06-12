---
title: "Can't fix Broken Package-Please help"
date: 2007-04-23
forum: General Help
---

### Post by keithk50 on 2007-04-23
Hi, I upgraded to 6.10 from 6.06 over the weekend.  After restarting the system the Software Update Manager gave an error message saying "Software Index is broken.   It is impossible to install or remove any software.   Please use the Package Manager 'Synaptic'  or run sudo apt-get install -f' in a terminal to fix this issue at first".   The broken package is Samba.   I have tried to repair via command line.  Results from "sudo apt-get update -f" are:

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Fetched 6B in 0s (8B/s)  
Reading package lists... Done
keith@keith-laptop:~$ 

The Software Manager still returns the same error message.   In Synaptic Samba is showing as broken (red box)    When I try to repair it returns this error:

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1i386.deb:subprocess new pre-removal script returned error exit status 102.

I have tried numerous times to repair Samba but to no avail.   Even tried to remove it but no go.   My system is useless without the software updates/security ect and it took me hours of work to get Dapper just right.   Should have stuck with it I suppose but that 'big red button' is hard to ignore.   Can anyone offer any help or guidance?   Thanks.

---

### Post by keithk50 on 2007-04-23
Can anyone help?

---

### Post by ubu-for on 2007-04-23
Maybe an upgrade to Ubuntu 7.04 (Feisty Fawn) could fix your problem with Samba.

---

### Post by keithk50 on 2007-04-24
Thanks for your reply.   Perhaps your right, but are you saying that there is nothing more I could try within my current setup?.   Im fairly new to Ubuntu and perhaps not experienced enough to get around this problem.   One thing is for sure, I will not upgrade again.  Should have paid attention to all the members who had problems using the upgrade method.   Still, It's not the end of the world.   Thanks again for your reply.

---

### Post by ubu-for on 2007-04-25
It looks like you have a very individual problem, no other user had before.

I've never upgraded Ubuntu (5.10, 6.06, 7.04) to keep the OS fast and stable. So if you don't like to reinstall everything, I can only recommend to pass over every second release and create 3 partitions in all for "/" (about 10 GB, 5 GB is to small), "swap" (your RAM size x 2) and "/home".

Last try.

Go to "/var/cache/apt/archives/" and delete "samba_3.0.22-1ubuntu4.1i386.deb". You can use the file manager "Nautilus" with root rights.

```
sudo nautilus
```

Get sure that you have the sources list for Edgy.

```
sudo gedit /etc/apt/sources.list
```

Example:

```
## MAIN
deb http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
```

And NOT:

```
## MAIN
deb http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

Then:

```
sudo apt-get update
```

BTW before you delete and reinstall Ubuntu, you could try another upgrade. But don't forget to backup your files!

---

### Post by keithk50 on 2007-04-25
Thanks again for your help.   I have followed your steps as detailed in your post.   Unfortunately it did not resolve the problem and it is now obvious that I must move on.   My files are backed up and I am going to do a compete restall with 7.04.    Have tried out the live CD and it found my wireless card straight away.   The only thing I had a problem with was no sound but have resolved that now.   Thanks for trying, it is appreciated.   Good luck for the future.      Keith.

---

### Post by ubuntubrian on 2007-04-25
I just had a similar problem when I tried to upgrade libgcc from the Dapper version to a higher version. I couldn't remove or fix the package with Synaptic. Removing would have wiped out much of the default software like OpenOffice! I figured out that perhaps I could force a down grade to the previous libgcc version via Package>force-version in the Synaptic menu. I had 2 choices, the broken package and the older package. I force-installed the lower version and all is well. Perhaps you could downgrade Samba?

---

### Post by TerraMedicX on 2007-12-11
So I'm having this same problem with samba after trying to upgrade. I've tried fixing the broken package through Synaptec and through the command line (both apt-get install -f and aptitude install -f)...as well as deleting the file in the /var/cache/apts/ directory as suggested earlier. I also tried forcing a downgrade, but that fails still. It seems that it is the script to removing the old version of samba that continues to fail. I'd really prefer to not have to wipe my install and start over from CD. Does anyone have any suggestions?

Here's the output from attempting to run "sudo aptitude install -f"

```
 Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 121617 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu4.4 (using .../samba_3.0.24-2ubuntu1.4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.24-2ubuntu1.4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.24-2ubuntu1.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by keithk50 on 2007-12-17
I am sorry to read about your similar problem.   I spent hours of frustration with this and decided (no option really) to carry out a complete re-install of the higher version.   Backed my files up first.

I prefer to do this in every upgrade now as I have had problems with every upgrade.   I know it;s a lot of work setting up your system again but believe me it is the best option.

Good luck.

---

### Post by PmDematagoda on 2007-12-17
The problem is that the repositories for Ubuntu 6.10 are not available where they were any more as support for it has run out a long time ago(Does not apply for Ubuntu 6.06 since it is LTS).

So if you want to upgrade, make sure that the one you are upgrading to still is recent enough to receive support:).

---

