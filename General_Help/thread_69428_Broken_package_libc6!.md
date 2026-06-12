---
title: "Broken package libc6!"
date: 2005-09-26
forum: General Help
---

### Post by rsvirani on 2005-09-26
I have upgraded my libc6 by instruction in some random forum for a particular task.   I no longer need to have the latest version.  I want to go back to the original libc6.  I have seen a forum in which this is explained.  I do not want to remove all of the dependencies though.  Is this possible?  Can I uninstall the current libc6 without removing dependencies, which is like everything, and reinstall the original ubuntu one?  Please help.  I have four broken packages because of this attempt:
1. libc6-dev
2. libc6-686
3. locales
4. mozilla-firefox-gnome-support.

Will fixing the libc6 version also fix these broken packages?  Do I really have to remove all the dependencies?  Please help.

---

### Post by DJ_Max on 2005-09-26
How did you do the libc upgrade? Linux has very little package integrity. Messing with libc is dangerous, and unless you have a really good reason for upgrading (C/C++ development), there is no need to touch libc.

---

### Post by rsvirani on 2005-09-26
I followed some directions in a forum to upgrade the libc6.  They said it was needed for the printer drivers i needed.  I later found directions on how to install the printer drivers without the upgrade.  But it was too late and I broke my packge! lol.  Any advice.

---

### Post by DJ_Max on 2005-09-27
[QUOTE=rsvirani]I followed some directions in a forum to upgrade the libc6.  They said it was needed for the printer drivers i needed.  I later found directions on how to install the printer drivers without the upgrade.  But it was too late and I broke my packge! lol.  Any advice.[/QUOTE]
It's rarely needed to upgrade libc. Anyway, I can't give you any useful advice unless I know how'd you upgrade.

---

### Post by rsvirani on 2005-09-27
**This is what I followed in order to get my printer working.  My printer works and of course i have the broken packages from the top posting.::**

 				[COLOR=Blue][IMG]http://ubuntuforums.org/images/icons/icon1.gif[/IMG] 				**HOWTO: Install Canon PIXMA ip1500**[/COLOR] 			
  			  			 		 		 		 		[SIZE=2][COLOR=Blue]**Do this at your own risk!**[/COLOR][/SIZE][COLOR=Blue]

 First you will need to update libc6 to one from the Debian site (why I say at your own risk)

[http://packages.debian.org/testing/base/libc6]("http://packages.debian.org/testing/base/libc6")

**sudo dpkg -i libc6_2.3.2.ds1-22_i386.deb**

 then goto: [http://linux.cergynux.net/canon/]("http://linux.cergynux.net/canon/") 

 get: bjfilter-pixmaip1500_2.50-3_i386.deb & bjfilter-common_2.50-3_i386.deb

**sudo dpkg -i bjfilter-common_2.50-3_i386.deb bjfilter-pixmaip1500_2.50-3_i386.deb**

 You will then be required to restart cups:

**sudo killall cupsd**
**sudo cupsd**

 After we're all done - all we have to do now is set-up the printer!  :) 

**System >> Administration >> Printing >> New Printer** 

 Select: **Use another printer by specifying port** drop down to: **USB Printer #1 (Canon ip1500)** 

 Then select the PIXMA iP1500 ver.2.50 from the list :)

**I have figured a way past the dependancy hell with the above. Install the debian locales package also**[/COLOR] 

**Does this help?  Can someone help me fix the packages knowing how I upgraded licbc6?**

---

### Post by DJ_Max on 2005-09-27
Your first problem was trying to upgrade something like libc6. Your second mistake was using packages for Debian and you're using Ubuntu.

When you do
```
sudo apt-get -f install
``` what happends.

---

### Post by rsvirani on 2005-09-28
[COLOR=SeaGreen]root@rahim:/home/rsvirani # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  g++ g++-3.3 language-pack-en language-pack-en-base libc6-dev libc6-i686
  libstdc++5-3.3-dev locales lsb mozilla-firefox-gnome-support ubuntu-base
  ubuntu-desktop
0 upgraded, 0 newly installed, 12 to remove and 9 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 41.2MB disk space will be freed.
Do you want to continue [Y/n]?
[/COLOR]

---

### Post by rsvirani on 2005-09-28
These are the versions of my broken packages in synaptic.

                                  Installed                                -  Latest Version
1. libc6-dev -             2.3.2.ds1-20ubuntu14 -              2.3.2.ds1-20ubuntu14
2. libc6-686            - 2.3.2.ds1-20ubuntu14 -              2.3.2.ds1-20ubuntu14
3. locales               -  2.3.2.ds1-20ubuntu14              - 2.3.2.ds1-20ubuntu14
4. mozilla-firefox-gnome-support - 1.0.6-1ubuntu1~5.04ubp1  - 1.0.7-0ubuntu0.1

Any recommendations as to what I should do to repair these broken packages?

---

