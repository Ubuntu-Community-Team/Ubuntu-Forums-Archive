---
title: "Strange unarchiving error."
date: 2015-11-02
forum: General Help
---

### Post by Owen Thomas on 2015-11-02
Hello.

When I compress files, I try to have some protection by encrypting them with the .zip extension. I use the Archive manager that comes with Ubuntu. I'm using Ubuntu 14.4.

I tried to uncompress my archive today, and it says that "An error occurred while extracting files". I've tried previous archives with the same result.

Has something changed with the archive manager?

A bit anxious to know what's going on...

  Owen

---

### Post by howefield on 2015-11-03
Try uncompressing via the command line, you might get a clue as to what is happening.

```
unzip filename -d destinationfolder
```

---

### Post by Owen Thomas on 2015-11-03
Thanks for the tip. I tried and got the message: "error:  invalid compressed data to inflate". I found [this suggestion]("http://ubuntuforums.org/showthread.php?t=1042629"), and am wondering if it applies to me seeing as it was published in 2009? Still, I am also wondering why my problem has decided to start happening to me now?

---

### Post by ajgreeny on 2015-11-03
Have you tried yet with p7zip as your link suggests?

I use p7zip a lot and it's been faultless when dealing with encrypted, password protected files.

---

### Post by Owen Thomas on 2015-11-03
Thanks for the tip ajgreeny.

I could install the software, but that doesn't answer the question of why my problems have decided to start happening right now. Do you know why? Could it be something to do with recent software updates introducing a bug? Installing a piece of software as an old fix to a problem that has only just recently appeared on my computer doesn't seem to be a sufficient answer. This archiving utility appears to add another format to the Archive Manager (I think). Why would I want to use the new .7z format? Would I be able to use .zip to compress and uncompress my archives. Would I be able to access my previous archives?

I was able to uncompress my archive an another (old Windows) machine, and copy it to my computer. There appears to be nothing wrong with the archive - all files appear to be present. Why does my computer running Ubuntu 14.4 have a problem when am old Windows machine doesn't?

Installing a new format just because an existing one has, for some strange reason, stopped working is almost no answer at all.

---

### Post by ajgreeny on 2015-11-04
Have you uncompressed them in Windows then changed them in some way and  re-compressed them, again in Windows?

It's a fair point you make about why the sudden change, but my only answer to that is that I'm afraid I haven't got any ideas from the information you have given us, unless the archives have been corrupted in some way in Windows that makes them unreadable in Ubuntu.

---

