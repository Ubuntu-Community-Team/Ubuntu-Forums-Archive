---
title: "apt-get update errors... cannot figure out how to fix"
date: 2015-09-27
forum: General Help
---

### Post by DK1993 on 2015-09-27
I am having errors being thrown after running an update on repositories (Trusty 14.04). I do not know how to fix this, and it's driving me nuts. Essentially it is looking for "binary-i387" in the repositories and I have no idea why. Where could I find this offending typo so I can make my update work again?

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release  Unable to find expected entry 'main/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release  Unable to find expected entry 'main/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release  Unable to find expected entry 'main/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'partner/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i387/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2015-09-27
Hmm, weird.
Perhaps look at both the sources.list file
```
cat /etc/apt/sources.list
```
(Though I doubt it'll show anything unusual like i387 entries.)
or the lists entries in /var/lib/apt/lists
```
ls /var/lib/apt/lists
```

---

### Post by DK1993 on 2015-09-27
I already had the same idea. All it tells me is the sources of the repositories with no mention of this obscure arch. type that it's searching for. I am so lost.

---

### Post by ajgreeny on 2015-09-27
Try command ```
cat /var/lib/apt/lists/* | grep i387
``` though why you should have any entry that includes i387 is beyond me.

The output of that command should show you where the problem lies you can also try a similar command piped to **grep i387** for other places where the problem entry of i387 might occur.

---

### Post by deadflowr on 2015-09-27
You might try this
```
sudo dpkg --remove-architecture i387
```
then re-run the update command.

---

### Post by DK1993 on 2015-09-27
I got it to work... by starting over. I tried everything you guys suggested but I may have created the typo myself by messing up trying to get i386 binaries awhile back. But I appreciate everyone's help :)

---

