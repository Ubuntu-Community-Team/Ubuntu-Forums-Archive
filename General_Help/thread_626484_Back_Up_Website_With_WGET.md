---
title: "Back Up Website With WGET"
date: 2007-11-29
forum: General Help
---

### Post by renzokuken on 2007-11-29
hiya,

we're moving servers with our website and before we do i want to download the entire site to my laptop, as a backup......

i've been looking into using wget but i'm getting confused. i want to download everything!! as is without it converting filenames and links within the html. an exact replica i can simply upload to the new server.

i tried using ftp to download the entire contents but i keep getting 550 permission errors and have no idea why.......hence having a go with wget.

can anyone explain the correct usage of wget for me here.......is it as simple as

```
 wget -r http://www.mywebsite.co.uk
```

thanks

EDIT: i just tried that anyway and it still seems to be missing things.......possibly the files with the 550 error.....i'm clueless

---

### Post by scooper on 2007-11-30
I think "wget -m" enables full mirroring.  For myself, I've preferred to use rsync.  In addition to accurately mirroring a site locally, it has many more options, including exclusions, and can minimize the transfer size for incremental backups.

---

