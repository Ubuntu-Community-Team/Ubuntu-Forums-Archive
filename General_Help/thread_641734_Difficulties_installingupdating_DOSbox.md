---
title: "Difficulties installing/updating DOSbox"
date: 2007-12-15
forum: General Help
---

### Post by Eric Weir on 2007-12-15
I am currently running DOSbox 0.65 under Ubuntu 7.4. Following instructions on the Debian website I attempted to add a respository to my sources list and upgrade to 0.72. Specifically, Using Software Sources I entered: 
            ```
deb http://debian.oregonstate.edu/debian sid main
```After which Software Sources notified me that my files were ot of date. After the files were downloaded I got the following error messages: 

 First,```
W: GPG error: http://debian.oregonstate.edu sid Release: The following signatures couldn't 
be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
```And then,```
E: Dynamic MMap ran out of room 
E: Error occurred while processing qt4-dev-tools (NewVersion1) 
E: Problem with MergeList var/lib/apt/lists/debian.oregonstate.edu_debian_dists_sid_main_binary-i386_Packages 
E: The package lists or status file could not be parsed or opened. 
E: _cache->open() failed, please report.
```Subsequently Adept notified me that an upgrade was available, but then reported that the database could not be opened. It recommended that I try running apt-setup and apt-get update, which I did with the following result.
```
eric@eric-linux:~$ apt-setup
bash: apt-setup: command not found
eric@eric-linux:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
eric@eric-linux:~$ 

```So, four questions: [1] How do I add the key? [2] Is the second error related to the first, and what do I do about it? [3] Why was the first apt command not found? [4] What does the second apt error report mean, and what do I do about it?

Thanks for any help.

---

