---
title: "What are these files with the plus sign"
date: 2019-10-26
forum: General Help
---

### Post by Gnusboy on 2019-10-26
I see these a lot, but I don't know why they are there.

default/storage/default/https+++[www.pinterest.com](www.pinterest.com)
.default/storage/default/https+++[www.americanexpress.com](www.americanexpress.com)
Data/o8fadx9q.default/storage/temporary/https+++otherthanhonorabledischarge.wordpress.com
[I]
I also need to find out how to access more of my posts here. All that shows up are a pair from 3 weeks ago

Thanks
[/I]

---

### Post by TheFu on 2019-10-26
full path to the files?

---

### Post by The Cog on 2019-10-26
I had a look, and as an example, ~/.mozilla/firefox/e0ynaaqh.default/storage/default/https+++slashdot.org is a folder containing an sqlite database - presumably local storage for web sites.

I don't recall allowing use of local storage for slashdot though.

---

### Post by Gnusboy on 2019-10-26
Yes, me neither - at least intentionally
I'll look into it another time
Thanks

---

### Post by TheFu on 2019-10-26
I just removed a few of the directories and visited the websites.  With javascript allowed, the files **were recreated**.  
Disabled javascript, removed the directories and files again and those directories+files **were not re-created**.
I'm suspecting they are a cache for the javascript that is specific to each site.

Took a look at the DB schema for one of the .sqlite files. It was a generic object store for blobs which would be fine for javascript.

---

### Post by &amp;KyT$0P# on 2019-10-27
I believe those are Firefox storage of IndexedDB data.

---

