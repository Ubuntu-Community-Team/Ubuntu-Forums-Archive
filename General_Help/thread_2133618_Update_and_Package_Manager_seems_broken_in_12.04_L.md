---
title: "Update and Package Manager seems broken in 12.04 LTS 64-Bit due to E17 dependency"
date: 2013-04-08
forum: General Help
---

### Post by gcleric on 2013-04-08
Hello,

I've been doing some forum surfing and googling and can't quite get my issue resolved so hopefully you guys may help!

The common message I get is: The following packages have unmet dependencies:

libefl-bin: Depends: libefl (= 201212281219-551~precise1) but 201304081310-21693~precise1 is installed

I got this while trying to execute my updates in the update manager. 

I've tried apt-get update -f install with a similar result:


root@ubuntudustyn:/home/dustyn# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libudev0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libefl-bin
The following packages will be upgraded:
  libefl-bin
1 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.
Need to get 0 B/315 kB of archives.
After this operation, 670 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 203899 files and directories currently installed.)
Preparing to replace libefl-bin 201212281219-551~precise1 (using .../libefl-bin_201304081310-21693~precise1_amd64.deb) ...
Unpacking replacement libefl-bin ...
dpkg: error processing /var/cache/apt/archives/libefl-bin_201304081310-21693~precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/edje_player', which is also in package libedje-bin 201303080929-2876~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl-bin_201304081310-21693~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It appears this is an issue with E17 (enlightenment) and I'd love to just remove the whole thing now but here's what I get when I try that. 

root@ubuntudustyn:/home/dustyn# apt-get purge e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libefl-bin : Depends: libefl (= 201212281219-551~precise1) but 201304081310-21693~precise1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


root@ubuntudustyn:/home/dustyn# apt-get remove e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libefl-bin : Depends: libefl (= 201212281219-551~precise1) but 201304081310-21693~precise1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Any help would be very much appreciated. Thanks!

---

### Post by Frogs Hair on 2013-04-08
If you are using one of the E17 PPAs you may have held packages which happens sometimes. The best thing to do if that is the case wait for further updates. I never had that happen with the Ubuntu  repository packages, but they don't offer the modules like the PPAs. Don't install a PPA while the repository packages are installed or you will have dependency problems and broken packages. I used following PPA until I got tired of package problems though it worked very well at first. [https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)

---

### Post by gcleric on 2013-04-08
Hello. So, there's no way to completely get rid of E17 now? I have no access to update manager, I can't use apt-get install and I can't use software center as it currently stands which is kinda rough.

---

### Post by gcleric on 2013-04-08
I think I've solved it, and thank you to Frogs Hair for jogging my brain about PPA sources. 

1) I opened Ubuntu Software Center
2) I went to Edit>Software Sources>Other Software [Tab]
3) Unchecked all of my PPA entries
4) Ran "sudo apt-get install -f"
5) "sudo-apt get update" now works and software center now loads without spitting errors at me!

---

### Post by gcleric on 2013-04-08
How do I mark this bad boy as solved?

---

### Post by Frogs Hair on 2013-04-09
Sorry I didn't get back I logged of for the day but I see you have it solved.  [http://ubuntuforums.org/showthread.php?t=2128829](http://ubuntuforums.org/showthread.php?t=2128829)

---

