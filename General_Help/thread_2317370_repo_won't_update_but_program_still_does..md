---
title: "repo won't update but program still does."
date: 2016-03-15
forum: General Help
---

### Post by Evil Wayz on 2016-03-15
Update manager is constantly telling me some files weren't loaded. 

The problem seem to be google.  So I uncommented it and tried refreshing and got the same error. 

This is the error ```
W:Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I think that Ubuntu is updating google-chrome-stable from it's own repo so this other one is not needed but I can't figure out why it thinks it can't connect to the internet.

---

### Post by sandyd on 2016-03-16
Google Chrome has been discontinued for i386, the repo no longer has versions for i386.

The repo at  /etc/apt/sources.list.d/google-chrome.list is causing the error likely. Remove it to fix the issue.

It may be a good idea to remove chrome as well as it will no longer receive updates.

---

### Post by mcgess on 2016-03-16
Hi

I got this warning as well and was confused as I have the amd64 version on Lubuntu. I had to modify the source entry for chrome to

```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```

Martin

---

### Post by Evil Wayz on 2016-03-18
I removed the original line from software sources as it doesn't appear in /etc/apt/sources.list, and add the above to sources.  Gives me the same error. However, I just had a hernel upgrade so I have to restart, maybe it will work then.

---

### Post by Bashing-om on 2016-03-18
Evil Wayz; Hello;

AND: must also change the references in the file /opt/google/chrome/cron/google-chrome : 
see: [http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html](http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html) <- modified with the addition of a second command that adds "[arch=amd64]" to the script that generates the .list file . In my install was lines 24 and 25 .

Sneaky little bugger, huh .

[INDENT][INDENT]not done 'til
[INDENT][INDENT][INDENT]all the paper work is done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

