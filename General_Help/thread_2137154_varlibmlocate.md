---
title: "/var/lib/mlocate"
date: 2013-04-19
forum: General Help
---

### Post by jamesaepp on 2013-04-19
Greetings! I noticed my hard drive was about 66% full for no apparent reason (I don't have 500GB of movies :P) So I did:
 
sudo du -h | grep G 

(this was to categorize all files with a measurement, then find the files/directories that were at least a GB in size)

I found that /var/lib/mlocate.db.e1GYsY to be almost 600GB!!! 

Is it safe to delete this file?

---

### Post by bab1 on 2013-04-19
> **jamesaepp said:**
> Greetings! I noticed my hard drive was about 66% full for no apparent reason (I don't have 500GB of movies :P) So I did:
 
sudo du -h | grep G 

(this was to categorize all files with a measurement, then find the files/directories that were at least a GB in size)

I found that /var/lib/mlocate.db.e1GYsY to be almost 600GB!!! 

Is it safe to delete this file?

That file is not supposed t be there.  It should be at /var/lib/mlocate/mlocate.db.

See [**_[COLOR="#0000CD"]here[/COLOR]_**]("mlocate.db") for the info.

---

### Post by jamesaepp on 2013-04-19
> **bab1 said:**
> That file is not supposed t be there.  It should be at /var/lib/mlocate/mlocate.db.

See [**_[COLOR=#0000CD]here[/COLOR]_**]("http://mlocate.db") for the info.


There is also a mlocate.db However, this one appears to be some sort of temp file?

---

### Post by bab1 on 2013-04-19
> **jamesaepp said:**
> There is also a mlocate.db However, this one appears to be some sort of temp file?

That temp file is usually do to an interrupted *dbupdate* routine.  Read the link I sent you.

---

### Post by ibjsb4 on 2013-04-19
I have been googling for /var/lib/mlocate.db.e file and cannot find anything on it.  It doesn't exist on my system.  Have you downloaded any special search function packages/ppa/thirdparty?  At 600GB I would not care if its important or not, I delete it (do not send it to trash).

You could also delete and recreate mlocate.db to see if that would help.

[http://askubuntu.com/questions/23692/why-is-var-lib-mlocate-db-almost-800-mb](http://askubuntu.com/questions/23692/why-is-var-lib-mlocate-db-almost-800-mb)

---

### Post by jamesaepp on 2013-04-20
So I decided to just go ahead and rm the file. Turned out fine, after a reboot there were no issues or error message, so I guess I can only assume it was a REALLY weird temporary file.

---

