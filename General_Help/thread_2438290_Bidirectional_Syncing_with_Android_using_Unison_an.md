---
title: "Bidirectional Syncing with Android using Unison and MTP"
date: 2020-03-09
forum: General Help
---

### Post by Weisskrautbrautkleid on 2020-03-09
Hey,

I'm currently trying to sync bidirectionally some folders of my PC (Ubuntu 18.04) with my Smartphone (Fairphone 3, Android 9) via MTP using Unison. I thought that this should be pretty easy, but it turned out to be rather complicated. Unison is able to detect if two versions of a file exist in the two sync directories. However, than two problems occur:
1. Unison cannot detect which one of the files is the up-to-date version. I can set this manually, but this is rather time consuming and also prone to errors, in case I make a mistake.
2. Unison cannot overwrite the old version of the file with the up-to-date version.

I here document what I have done so far:
1. Create a mount directory for the file system of the smartphone:
```
mkdir /tmp/fp3
```
2. Mount the filesystem of the phone:
```
jmtpfs -o allow_other /tmp/fp3
```
3. Sync the directory of the phone with the according directory of the PC. Both directories contain different versions of the file "test":
```
unison -fat ~/Desktop/Test /tmp/fp3/SD-Card/Home/Test
```
The last command returns the following output in the console. Unison cannot detect the appropriate syncing direction for the file "test" and I'm setting it manually with ">":
```

Contacting server...
Looking for changes
Reconciling changes

Desktop/Test   Home/Test          
new file ====> new file   test  [] >

Proceed with propagating updates? [] y
Propagating updates


UNISON 2.48.4 started propagating changes at 10:29:48.42 on 06 Mar 2020
[BGN] Updating file test from /home/$USER/Desktop/Test to /tmp/fp3/SD-Card/Home/Test
Failed: Error in renaming /tmp/fp3/SD-Card/Home/Test/.unison.test.92833400e4472a77b19cca039512131e.unison.tmp to /tmp/fp3/SD-Card/Home/Test/test:
Input/output error [rename(/tmp/fp3/SD-Card/Home/Test/.unison.test.92833400e4472a77b19cca039512131e.unison.tmp)]
100%  00:00 ETAFailed [test]: Error in renaming /tmp/fp3/SD-Card/Home/Test/.unison.test.92833400e4472a77b19cca039512131e.unison.tmp to /tmp/fp3/SD-Card/Home/Test/test:
Input/output error [rename(/tmp/fp3/SD-Card/Home/Test/.unison.test.92833400e4472a77b19cca039512131e.unison.tmp)]
UNISON 2.48.4 finished propagating changes at 10:29:48.99 on 06 Mar 2020


Saving synchronizer state
Synchronization incomplete at 10:29:48  (0 items transferred, 0 skipped, 1 failed)
  failed: test

```

Looks like Unison is first copying an up-to-date version of the file "test" with the name ".unison.test.92833400e4472a77b19cca039512131e.unison.tmp" into the directory where the old version of "test" sits. Then it is trying to rename the up-to-date version, which seems to fail.
Any ideas what could cause this error? Any help is highly appreciated!

Cheers

---

