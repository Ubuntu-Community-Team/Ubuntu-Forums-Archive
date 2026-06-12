---
title: "Keep specific directory in cache long term"
date: 2016-05-24
forum: General Help
---

### Post by jrmymllr on 2016-05-24
This is a rather odd request.

I have a service that writes frequently to a specific directory.  The directory doesn't contain more than 200MB of files, but it's written so often that it's adding up to a lot of writes.  The location is on an SSD, data is not absolutely critical, and the machine is on a UPS so I'm not too concerned about data loss but am trying to limit the writes.  

It would be nice to keep the files in cache and commit maybe once a day or so, but only for that directory.  I could copy to a RAM drive and use a cron job to copy to disk, but is there a way to do this with the cache so the OS completely manages it, including if the OS is shutdown or rebooted?

---

