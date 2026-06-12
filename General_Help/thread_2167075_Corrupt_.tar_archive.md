---
title: "Corrupt .tar archive"
date: 2013-08-12
forum: General Help
---

### Post by brabox on 2013-08-12
Hello there,

I saved 5+ gB of photos to a .tar archive using file-roller (perhaps not the smartest move, I know). The resulting archive seemed to behave according to expectations, however, so I decided to keep the photos stored this way.
The problem is another person fiddled about with the archive (deleted some photos from it) and now file-roller can't open the archive anymore. It just says:
> tar: Skipping to next header
tar: Exiting with failure status due to previous errors


I looked up the issue (remember, it's not a .tar.gz archive but a regular .tar) and found some forum posts. The following command managed to extract the first 300mB of data but in the end it also failed.
```
$cat test1 | tar xf - 
```


This is the error message it gave me:

> tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

So... since tar archives don't use compression (that I know of), it seems to me this should be fixable (I could well be incredibly wrong, though). 
I would greatly appreciate any help!

Regards,
Bram

---

### Post by cortman on 2013-08-12
Did you try unpacking it from the command line?

```
tar -xvf mytar.tar
```

---

### Post by brabox on 2013-08-12
> **cortman said:**
> Did you try unpacking it from the command line?

```
tar -xvf mytar.tar
```


I have now :P
Sadly the output doesn't fill me with much hope:
```

DSC00622.ARW
DSC00623.ARW
DSC00624.ARW
DSC00625.ARW
DSC00626.ARW
DSC00627.ARW
DSC00628.ARW
DSC00629.ARW
DSC00630.ARW
DSC00631.ARW
DSC00632.ARW
DSC04196.ARW
DSC04196.JPG
DSC04197.ARW
DSC04197.JPG
tar: Skipping to next header
DSC00632.JPG
DSC04196.ARW
DSC04196.JPG
DSC04197.ARW
DSC04197.JPG
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: thefile.tar: Cannot read: Input/output error
tar: Too many errors, quitting
tar: Error is not recoverable: exiting now
```

---

### Post by cortman on 2013-08-12
Doesn't look good. Just browsing around the web I found [this thread]("http://www.linuxquestions.org/questions/linux-software-2/recovering-files-from-corrupt-tar-archive-326716/#4") (see post #4)- you might try the utility referred to there, cpio.

---

### Post by brabox on 2013-08-12
Ohh dear... 
You know something's spectacularly badly wrong when a utility like cpio segfaults :P

```
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number 
cpio: Malformed number DSC00632
cpio: Malformed number SC00632.
cpio: Malformed number C00632.J
cpio: Malformed number 00632.JP
cpio: Malformed number 0632.JPG
cpio: Malformed number 632.JPG
cpio: Malformed number 32.JPG
cpio: Malformed number 2.JPG
cpio: Malformed number .JPG
cpio: Malformed number JPG
cpio: Malformed number PG
cpio: Malformed number G
cpio: warning: skipped 723968 bytes of junk
DSC00632.JPG
cpio: DSC04196.ARW not created: newer or same age version exists
DSC04196.ARW
cpio: DSC04196.JPG not created: newer or same age version exists
DSC04196.JPG
cpio: DSC04197.ARW not created: newer or same age version exists
DSC04197.ARW
cpio: DSC04197.JPG not created: newer or same age version exists
DSC04197.JPG
Segmentation fault

```

---

### Post by cortman on 2013-08-12
Oh my. :(

Don't trash the whole thing on my word, but it looks to me like it's corrupted, and AFAIK no amount of recovery attempts will do much there.
But perhaps someone else with more knowledge will weigh in.
Sorry to not have been of much help. You have my sympathy!

---

### Post by brabox on 2013-08-13
> **cortman said:**
> Oh my. :(

Don't trash the whole thing on my word, but it looks to me like it's corrupted, and AFAIK no amount of recovery attempts will do much there.
But perhaps someone else with more knowledge will weigh in.
Sorry to not have been of much help. You have my sympathy!

Thanks very much for the help, I know it doesn't look good. My expectations weren't very high to begin with ;)

---

