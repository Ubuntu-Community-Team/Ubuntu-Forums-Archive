---
title: "apt-get update broken? 18.04"
date: 2018-05-06
forum: General Help
---

### Post by eth0s2 on 2018-05-06
Hey peeps. having an issue. I can't run apt-get update, apt-get dist-upgrade, or update manager. not sure whats going on here. gonna post the results of apt-get update below. 

```
 derrick@Machine:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Err:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
  Couldn't create temporary file /tmp/apt.conf.s5vw2t for passing config to apt-key
Ign:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Ign:3 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Err:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
  Couldn't create temporary file /tmp/apt.conf.4DSpqC for passing config to apt-key
Err:5 http://security.ubuntu.com/ubuntu bionic-security Release
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_bionic-security_Release - open (30: Read-only file system) [IP: 2001:67c:1562::16 80]
Err:6 http://us.archive.ubuntu.com/ubuntu bionic-updates Release
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_bionic-updates_Release - open (30: Read-only file system) [IP: 2001:67c:1562::19 80]
Reading package lists... Done
W: chown to _apt:root of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chown to _apt:root of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.NXjyWq - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.mAKhnA - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.RkL1NJ - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/.apt-acquire-privs-test.GfcMeT - IsAccessibleBySandboxUser (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com/ubuntu bionic InRelease: Couldn't create temporary file /tmp/apt.conf.s5vw2t for passing config to apt-key
W: Problem unlinking the file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_bionic-updates_InRelease - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_bionic-security_InRelease - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease - PrepareFiles (30: Read-only file system)
W: chown to _apt:root of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chmod 0600 of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease failed - Item::QueueURI (30: Read-only file system)
W: chown to root:root of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease failed - 400::URIFailure (30: Read-only file system)
W: chmod 0644 of file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease failed - 400::URIFailure (30: Read-only file system)
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease: Couldn't create temporary file /tmp/apt.conf.4DSpqC for passing config to apt-key
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_bionic-security_Release - PrepareFiles (30: Read-only file system)
E: The repository 'http://security.ubuntu.com/ubuntu bionic-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Problem unlinking the file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_bionic-updatesor jums_Release - PrepareFiles (30: Read-only file system)
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file systemwith my typing cur)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)
derrick@Machine:~$ 


```
sorry, i know that's a lot to read. but, i'm having a lot of trouble figuring this one out.  I'm also having an issue with my typing cursor jumping around randomly. very irritating. it jumps between windows, between apps, and just to different boxes on pages when i'm typing. very strange.

---

### Post by eth0s2 on 2018-05-06
so, i seem to have fixed the problem. i rebooted. it auto booted me into some type of diagnostic tool i haven't seen. (I'm a linux newb if you couldn't tell)  told me it needed to run a command on a file path i can't recall. something along the lines of /dev/root--ubuntu-? ran some fixes and it's going again. still having the issue with my typing cursor jumping all over the place. but, one battle at a time lol.

---

### Post by Impavidus on 2018-05-07
It sounds like you file system was mounted read-only. When that happens, nothing can create new files or edit existing ones. The file system is automatically remounted read-only whenever there is an input/output error on that file system, to prevent further damage. During reboot, a file system check was executed and it was again mounted read-write.

This I/O error may be nothing. I once saw it happen when my computer overheated, and my computer still works flawlessly years later. However, it can be an indication of a failing hard drive. Just keep your backups up-to-date.

---

