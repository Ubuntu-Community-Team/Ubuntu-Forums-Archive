---
title: "About checksum"
date: 2017-11-10
forum: General Help
---

### Post by satimis on 2017-11-10
Hi all,

I couldn't recall the command to check an .ISO image.  It won't display its sum file but only indicating OK if no problem found.

Please advise

Thanks

Regards
satimis

---

### Post by VMC on 2017-11-10
md5sum ISOfile

check results against  'MD5SUMS' file

---

### Post by satimis on 2017-11-10
> **VMC said:**
> md5sum ISOfile

check results against  'MD5SUMS' file
Hi,

No.

I ran that command several times.  It only generated 'OK", not result for comparing MD5SUM file.

Edit
===

Finally I dig it out from my database

&#10219; checkisomd5 ovirt-node-ng-installer-ovirt-4.1-2017110820.iso ```

Press [Esc] to abort check.

The media check is complete, the result is: PASS.

It is OK to use this media.
```


Regards
satimis

---

### Post by vasa1 on 2017-11-10
There's also```
openssl dgst -sha256 /path/to/filename
```

---

### Post by satimis on 2017-11-10
> **vasa1 said:**
> There's also```
openssl dgst -sha256 /path/to/filename
```

$ openssl dgst -sha256 ovirt-node-ng-installer-ovirt-4.1-2017110820.iso ```

SHA256(ovirt-node-ng-installer-ovirt-4.1-2017110820.iso)= 6c4ac037c0efd4ce93a85be6e065f1a3f64a247e8b9285f25a3d8f6680ea8ab8

```
But I have to compare the output with sha256sum file

Regards
satimis

---

### Post by Holger_Gehrke on 2017-11-10
You can pass the option '-c' or '--check' to md5sum and pass the name of the file with the checksums as the argument. If this file is itself the output of md5sum or a compatible program, it contains the checksum, the relative path and the filename for one file per line. If there are multiple lines, multiple files can be checked with just one command. Output is one line per file with the filename and either 'OK' or 'FAILED'  and in case of any failures a line at the end with the count of files failing the test.

And for sha256 there is also a program named sha256sum with the same capabilities as md5sum.

Holger

---

### Post by satimis on 2017-11-10
> **Holger_Gehrke said:**
> You can pass the option '-c' or '--check' to md5sum and pass the name of the file with the checksums as the argument. If this file is itself the output of md5sum or a compatible program, it contains the checksum, the relative path and the filename for one file per line. If there are multiple lines, multiple files can be checked with just one command. Output is one line per file with the filename and either 'OK' or 'FAILED'  and in case of any failures a line at the end with the count of files failing the test.

And for sha256 there is also a program named sha256sum with the same capabilities as md5sum.

Holger

Hi Holger,

Thanks for your advice.

I have been running sha256sum and md5sum for long time.  But I need download the sum files for comparison until one day I found checkisomd5 by chance on Internet.

This program is rather convenient.  Actually what we need to know is the download ISO image having no problem. OK and FAIL will be sufficient.  If FAIL download another ISO image.  However up to now running checkisomd5 to check ISO images I haven't encountered a FAIL on their checking.

Regards
satimis

---

### Post by Holger_Gehrke on 2017-11-11
Hello,

if the checkisomd5 you mean is the one from the package 'isomd5sum', then there's one small problem with it: it needs the md5 to be put in the iso by implantisomd5. Of the 8 iso-images of various linux-distributions I have lying around none were prepared that way ...

Holger

---

### Post by satimis on 2017-11-11
> **Holger_Gehrke said:**
> Hello,

if the checkisomd5 you mean is the one from the package 'isomd5sum', then there's one small problem with it: it needs the md5 to be put in the iso by implantisomd5. Of the 8 iso-images of various linux-distributions I have lying around none were prepared that way ...

Holger
Hi,

IIRC it comes from ISO9660 checksum utilities.  It doesn't work on all ISO images but work on most of them.  Should the output is:```

.......
The media check is complete, the result is: NA.

No checksum information available, unable to verify media.

```
then I download the respective sums file for comparison.

If the output is:```

....
The media check is complete, the result is: PASS.

It is OK to use this media.
```
then I start installation immediately.


Regards
satimis

---

