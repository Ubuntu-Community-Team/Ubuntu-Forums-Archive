---
title: "md5sum doesn't work on Ubuntu 13.10 dvd"
date: 2013-12-12
forum: General Help
---

### Post by doug-ravennasprings on 2013-12-12
I've downloaded an .iso image to burn due to the insane instability of Ubuntu 13.10 x64.
I type md5sum  filename and it produces a checksum.
I click the up arrow and hit enter and a completely different checksum is given.
I can do this all day.  Each time I get a brand new checksum on a single file.

I don't imagine the file is changing so what is happening?

---

### Post by The Cog on 2013-12-12
Have you run a memory test recently? 
After the first run, the file contents should be cached in memory (memory size permitting), so I doubt it's a disk problem. I'm on 13.10 amd64 here and don't have that kind of problem - same sum every time. A memory problem could account for all manner of instability.

---

