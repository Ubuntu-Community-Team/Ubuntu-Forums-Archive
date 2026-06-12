---
title: "copy no retry help its driving me crazy"
date: 2007-02-10
forum: General Help
---

### Post by blackest_knight on 2007-02-10
Hi 
this might seem crazy but I want to copy some files from a Cd but the problem is some of them are damaged and unrecoverable- I don't care about the damaged files i couldnt give a monkeys about them. 

The problem is soon  as I start to copy it ubuntu finds a damaged file and insists on trying to recover it.  this will fail eventually but not before it has tried a million times and so a 15-20 minute file copy takes a week. 

I guess i can try to copy one by one but there are a 1000 files and dragging and dropping 1000 files is just as bad (and a damaged file will not cancel forcing a reboot. 


please please please tell me there is a file copy utility that will only try once and then move onto the next file. 

I do not want to recover the damaged files :(

---

### Post by dcstar on 2007-02-10
> **blackest_knight said:**
> Hi 
this might seem crazy but I want to copy some files from a Cd but the problem is some of them are damaged and unrecoverable- I don't care about the damaged files i couldnt give a monkeys about them. 
........
please please please tell me there is a file copy utility that will only try once and then move onto the next file. 

I do not want to recover the damaged files :(
```
man readcd
``` You can set the retry count to copy the whole image, and then you may be able to burn it to another CD so the corrupted files go through ok.

The other option would be to directly burn a copy of the bad CD and set the burning program to ignore any read errors.

---

