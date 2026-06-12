---
title: "Firefox Downloads Finish Too Soon"
date: 2007-03-01
forum: General Help
---

### Post by firefly2442 on 2007-03-01
I'm not sure if this is a problem with Firefox as a whole or just the Ubuntu version but I was just downloading a file in Firefox and it was humming along nicely.  I glanced at the status and it said 20% finished.  A few minutes later I checked it again and it said it was done.  I thought that was kinda weird so I checked the filesize and sure enough, it was 30 MB too small.  Firefox thought the download was done when it really wasn't.  It didn't give any error or anything which is the weird part.  I seem to remember seeing this issue with Firefox under Windows XP as well.  Has anyone else experienced this problem?

---

### Post by yabbadabbadont on 2007-03-01
I see this every now and then with large downloads.  So for large downloads, I just copy the download link and then use wget in a terminal window to download the file.  For that matter, you could use "wget -c url-to-file" to download only the remaining portion of the file.

---

