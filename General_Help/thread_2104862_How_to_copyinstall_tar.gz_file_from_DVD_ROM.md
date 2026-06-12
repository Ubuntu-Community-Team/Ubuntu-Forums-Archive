---
title: "How to copy/install tar.gz file from DVD ROM"
date: 2013-01-14
forum: General Help
---

### Post by ruwan2 on 2013-01-14
Hi,
I have a program on a DVD ROM to install. I use GUI window to copy that file to home folder. When I extract that file, it complaints format error:

MS-7696:/usr/local/CCSv5# sudo tar -xzvf /home/ruwan2/setup_CCS_5.0.3.00028.tar.gz ./

gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I suspect the copy results the error, but I do not know what command line can copy that tar.gz file to hard drive. Or you have better ideas for my problem.

Thanks

---

### Post by Impavidus on 2013-01-14
You can use cp to copy using the command line, but I don't think using the gui caused file corruption . Yet this archive seems corrupted. You could check by calculating the md5sum of the original and your copy, or let gzip (called by tar) read from the dvd directly. You may also have a bad dvd.

---

### Post by steeldriver on 2013-01-14
What is the trailing ./ there for?

```
# sudo tar -xzvf /home/ruwan2/setup_CCS_5.0.3.00028.tar.gz**[COLOR=Red] ./[/COLOR]**

```'tar' is probably treating that as a second archive file (and failing because it obviously isn't)

If you want to extract to a specific directory you need to use the -C switch I think e.g.

```
# sudo tar -xzvf /home/ruwan2/setup_CCS_5.0.3.00028.tar.gz **[COLOR=Red]-C[/COLOR]** ./
```

---

### Post by Impavidus on 2013-01-14
> **steeldriver said:**
> What is the trailing ./ there for?

```
# sudo tar -xzvf /home/ruwan2/setup_CCS_5.0.3.00028.tar.gz**[COLOR=Red] ./[/COLOR]**

```'tar' is probably treating that as a second archive file (and failing because it obviously isn't)

If you want to extract to a specific directory you need to use the -C switch I think e.g.

```
# sudo tar -xzvf /home/ruwan2/setup_CCS_5.0.3.00028.tar.gz **[COLOR=Red]-C[/COLOR]** ./
```
+1

I didn't see that ./. Actually, the default is to unpack in the current directory, so you don't need it at all.

Although, my tar gives a different error message when I try this:```

$ tar -xvzf randomtarball.tar.gz ./
tar: .: Not present in archive
```

---

