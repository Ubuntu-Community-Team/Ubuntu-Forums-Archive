---
title: "Problem running java install script."
date: 2013-01-14
forum: General Help
---

### Post by sandysmd on 2013-01-14
m stuckd at executing ./oab-java.sh command..
here is my output script after executing it.

sandeep@sandeep-Inspiron-N5010:~$ gksu ./oab-java.sh
oab-java.sh v0.2.6 - Create a local 'apt' repository for Sun Java 6 and/or Oracle Java 7 packages.

Copyright (c) Martin Wimpress, [http://flexion.org](http://flexion.org). MIT License

By running this script to download Java you acknowledge that you have
read and accepted the terms of the Oracle end user license agreement.

* [http://www.oracle.com/technetwork/java/javase/terms/license/](http://www.oracle.com/technetwork/java/javase/terms/license/)

If you want to see what this is script is doing while it is running then execute
the following from another shell:

  tail -f /home/sandeep/oab-java.sh.log

 [x] Installing Java build requirements success
 [x] Making build directories success
 [x] Removing clones of [https://github.com/rraptorr/sun-java6](https://github.com/rraptorr/sun-java6) success
 [x] Cloning [https://github.com/rraptorr/sun-java6](https://github.com/rraptorr/sun-java6) success
 [x] Checking out v6.38-1 success
 [x] Getting Java SE download page success
 [x] Getting current release download page success
 [x] Downloading jdk-6u38-linux-i586.bin : 68.45 MB success
 [x] Symlinking jdk-6u38-linux-i586.bin success
 [x] Downloading jdk-6u38-linux-x64.bin : 68.72 MB success
 [x] Symlinking jdk-6u38-linux-x64.bin success
 [x] Getting Java Cryptography Extension download page success
 [x] Downloading jce_policy-6.zip : 8.89 KB success
 [x] Symlinking jce_policy-6.zip success
 [x] Updating the changelog success
 [x] Building the packages success
 [x] Moving the packages success
 [x] Creating Packages.gz file success
 [x] Creating Release file success
 [x] Signing the 'Release' file success
 [x] Exporting public key success
 [x] Adding public key success
 **[x] Update package list failed**
 [[B]i] Showing the last 5 lines from the logfile (/home/sandeep/oab-java.sh.log)...
success
 [x] Update package list   E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
7027's retcode: 100
failed

[/B]i marked the error as bold text in above output script. Please help me out of these.
thanks in advance :)

---

### Post by coffeecat on 2013-01-14
@sandysmd, you posted in a thread about a different problem from the one you are needing help with. I have moved it into its own thread and given it a suitable title. Please start your own threads if you need help.

---

### Post by d4rk0wl on 2013-01-14
What does your
```
/etc/apt/sources.list
```
look like?

My untouched file is only 56 lines long also what does the lodfile say?

Regards,
- D4rk0wl

---

### Post by matt_symes on 2013-01-14
Hi
 
> 
**Update package list E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)**
 
 
This looks like your error.
 
Please post the output of (from the terminal)
 
```
 
sed -n 59p /etc/apt/sources.list

```
 
Kind regards

---

