---
title: "What does it mean?"
date: 2014-10-01
forum: General Help
---

### Post by molda3 on 2014-10-01
Hi,

I have the following command in a tutorial, which is designed to work on ubuntu, but it seams it doesn't.

```
$ sudo tar --strip-components=3 –C /media/rootfs -xzpf linaro-precise-ubuntu-desktop-20121124-560.tar.gz binary/boot/filesystem.dir
```

So, I know that sudo is for super user privileges
tar is for (de)compressing  the .tar.gz file
–C /media/rootfs is the output location
what I don't know is what do
--strip-components=3 
and 
-xzpf
and 
binary/boot/filesystem.dir
parameters stands for?

Deni

---

### Post by TheFu on 2014-10-01
man tar

---

### Post by Impavidus on 2014-10-01
**sudo** — you know that
**tar** — you know that
**--strip-components=3** — according to **man tar**:```
     --strip-components=NUMBER
           strip NUMBER leading components from file names on extraction
```So, suppose the archive contains the files```
foo/bar/booz/A.txt
foo/bar/booz/dir/B.txt
foo/bar/booz/dir/C.txt
```it will be extracted as```
A.txt
dir/B.txt
dir/C.txt
```
**-C /media/rootfs** — you know that
**-xzpf** — x: extract files from the archive; z: assume the archive is compressed using gzip; p: preserve permissions; f: the following argument is the filename of the archive
**binary/boot/filesystem.dir** — extract this file from the archive, leave the others

If it doesn't work, it would usually give an error message.

---

### Post by molda3 on 2014-10-02
Thank you Impavidus for your help.

Here is the error message I get:

tar: &#8211;C: Not found in archive
tar: /media/deni/rootfs: Not found in archive
tar: Exiting with failure status due to previous errors

for the command: 
tar --strip-components=3 &#8211;C /media/deni/rootfs -xzpf linaro-precise-ubuntu-desktop-20121124-560.tar.gz binary/boot/filesystem.dir

I already sudo su befor that. The tar.gz is located in the ~ directory.
 /media/deni/rootfs is a valid directory, I checked it many times. 

I have no clue on what can be wrong or why can it be wrong.  I would appreciate any help.

Deni

---

### Post by Impavidus on 2014-10-02
It should be -C, but what you type looks like –C. That is, an n-dash instead of a hyphen. Change that to a hyphen and it should work.

---

### Post by TheFu on 2014-10-02
There must be easier ways to accomplish the desired outcome.
In 20+ yrs, I've never seen tar used like this. Perhaps I'm just sheltered.

---

### Post by molda3 on 2014-10-02
oh, now it works :) Thank you!

---

