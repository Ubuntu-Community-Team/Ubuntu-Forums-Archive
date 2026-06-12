---
title: "problems with unmet dependency:linux-image-generic"
date: 2014-10-09
forum: General Help
---

### Post by cluelesswonder on 2014-10-09
Hello there.

I'm having some issues with what seems like an unmet dependency.
Software center wanted me to upgrade to the latest software today but returned an error and didn't finish installing.
I opened a terminal and ran:
sudo apt-get update which returned no errors

sudo apt-get upgrade which said I should try apt-get -f install
```
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-extra-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

sudo apt-get -f install which returned:
```
The following extra packages will be installed:
  linux-image-extra-3.13.0-37-generic
The following NEW packages will be installed:
  linux-image-extra-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/36.7 MB of archives.
After this operation, 152 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 411591 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.13.0-37-generic_3.13.0-37.64_amd64.deb ...
Unpacking linux-image-extra-3.13.0-37-generic (3.13.0-37.64) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-3.13.0-37-generic_3.13.0-37.64_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-3.13.0-37-generic_3.13.0-37.64_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Usually I'm much better at figuring stuff out on my own but Ubuntu has been running so well for the past few months that I've gotten kind of lazy and my brain seems unable to figure out how to fix this. . .>.< or maybe it's because a baby is getting ready to pop out of me. . .? help!?

---

### Post by ian-weisser on 2014-10-09
> **cluelesswonder said:**
> ```
Unpacking linux-image-extra-3.13.0-37-generic (3.13.0-37.64) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
```

Perhaps a corrupted package?
Delete the package from your cache. Apt will automatically redownload a fresh copy when it next tries to install the package.
```
sudo apt-get clean linux-image-extra-3.13.0-37-generic
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cluelesswonder on 2014-10-09
Had to do a sudo apt-get -f install instead of upgrade, but yep! That worked! :D

Thanks!

---

### Post by Ian_Gibb on 2014-10-11
I was receiving a very similar error, but I was still getting the error

```

dpkg: unrecoverable fatal error, aborting: files list file for package 'libxxf86vm1:i386' is missing final newline

```

After some more searching I found this thread [http://ubuntuforums.org/showthread.php?t=1319791](http://ubuntuforums.org/showthread.php?t=1319791) which had some python code to help solve the missing final newline error (as it turns out I was also missing the character from my bash.preinst). Once i ran that i was able to run the ```
apt-get -f install
``` and resolve the issue

---

### Post by ebonweaver on 2014-10-22
I'm hitting this issue and none of the posted replies help.  If I try to -f upgrade or -f install the result is the same:

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What makes no sense is it says it's dependant on itself:

The following packages have unmet dependencies:
 linux-image-extra-3.13.0-37-generic : Depends: linux-image-3.13.0-37-generic but it is not installed

That seems like a significant issue in the update package being malformed, and it's causing the entire system to not be updatable as if one package fails the check they all fail.  That seems like a design flaw when unrelated updates are not allowed to run because of one bad package.

Also curious:

linux-image-extra-3.13.0-37-generic is already the newest version

If that's try, why are you trying to update to what you already have?

Anyone have ideas how to correct this issue and get updates working again?  From what I can see this is a problem affecting Ubuntu 14 LTS but not in Ubuntu 12 LTS (they updated fine)

---

### Post by ian-weisser on 2014-10-22
linux-image-extra-<version>-generic and
linux-image-<version>-generic
really are different packages. 

The entire output would be much more helpful. dpkg error 1 simply means something failed. Earlier in the output will be the details of the failure(s) that we need to know.

---

### Post by ebonweaver on 2014-10-22
That really is all there is to see, there is no error earlier in the output, otherwise I might have something to go on.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-37-generic : Depends: linux-image-3.13.0-37-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.

I found another LTS 14 system is not having this error condition, it's holding these packages back instead (presumably because of a problem with the dependencies), which allows other updates to occur.  This system however is failing to deal with the dependency issue and simply skip over and allow other updates to occur.

---

### Post by ebonweaver on 2014-10-22
Found the answer on another forum.  Apparently there is a flaw in Ubuntu where it fails to clean up after updates some times leaving remnants of old packages behind that then cause conflicts and bad behavior like this.  Performing **sudo apt-get -f autoremove** forced it to clean up it's act.  Took about 5 minutes for that to run through after which updates worked properly again.

---

### Post by ian-weisser on 2014-10-22
If you have time, a link to that forum post would be most helpful.
Glad to see that good old 'autoremove' fixed your problem.

---

### Post by ebonweaver on 2014-10-22
I stumbled over the command in relation to a lot of posts related to failed updates due to /boot getting filled up.  While that wasn't my issue per se, that command and the comments about it caught my attention.  A quick comparison showed other systems had only one set of files in /boot and the one having issues had like six.  Note that I did not run any of the other commands in these posts, just the one I stated, and it cleaned up most of those other files (left 3 instead of just 1 like other systems, still curious about that).  I had to add the -f flag or it also failed to run, but once forced to clean up things were fine.  That leads me to conclude since I wasn't uninstalling things first, and this command removed a bunch of things and resolved the issue, it was just cruft left over from previous updates that had failed to be cleaned properly at the time.  I also noted that there were 2 versions ahead of the version reported by uname -r which I found no notes about anywhere, but once I was done uname then reported the most recent version, so I'm guessing it had the new files ready but couldn't implement them because update wouldn't complete due to the conflicts. 

[http://markmcb.com/2013/02/04/cleanup-unused-linux-kernels-in-ubuntu/](http://markmcb.com/2013/02/04/cleanup-unused-linux-kernels-in-ubuntu/)
"...and then removes all the residual junk that&#8217;s laying around"

[http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition](http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition)
"...you can run this to remove ever packages you won't need anymore"

I have seen both Windows and Mac systems have  a similar issue where their update caches or something similar gets  bloated, corrupted, etc and update fail until you purge stuff and  let it rebuild or something similar.  First time hitting this on Ubuntu, but apparently it's not uncommon there either.  One more trick for the tool belt.

---

