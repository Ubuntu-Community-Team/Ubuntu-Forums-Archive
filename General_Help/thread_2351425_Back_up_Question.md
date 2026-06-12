---
title: "Back up Question"
date: 2017-02-03
forum: General Help
---

### Post by aviator1 on 2017-02-03
Hello All:

I'm using Deja Dup to back up. I get the following message at the end of each back up.

```
/home/dave/.gnupg/gpg.conf
/home/dave/.gnupg/secring.gpg
/home/dave/.gnupg/trustdb.gpg
/home/dave/.mozilla/firefox/s38ux4vv.default-1457227414761/ffmpeg
/home/dave/Downloads/hplip-3.14.4
/home/dave/Downloads/hplip-3.14.4
```

What do I need to correct? Will I be able to recover if I have a failure and still have these errors?

Thanks for any response.

---

### Post by TheFu on 2017-02-03
You should test the backups for recover-ability every few weeks.
Backups that cannot be recovered are a complete waste of time, right?

---

### Post by aviator1 on 2017-02-03
Should have thought of that.... Thanks.... :-)

---

### Post by TheFu on 2017-02-04
These forums have a few people almost every week who thought they were doing backups that could be recovered, but had never tested any recovery.  Then something bad happened and they learned all that effort had been wasted.  Their "backups" were useless.  

The only way I know to ensure solid backups is to test the different types of restores you may need.  IME, it takes about 5 times to get the backup methods correct before being able to restore with all the stuff you want.  This assumes you don't just backup everything (I don't).  For me, it seemed like a waste of time to backup the 4G of the OS that a fresh system install would put back.  We aren't big, but have 20-30 different servers.  Thats 30x4G .... times 60-120 days of storage for backups. It adds up.  I only backup the things required to rebuild a system back to the same point now in 30-60 minutes.  For a slight level of greater complexity, we save lots and lots of backup storage and don't loose hardly any time when a restore is needed.

But it did take a few failed recoveries to get here.  OTOH, if you backup everything (wasting storage), you'll have everything and just need to practice the restores to get familiar with those steps.  It still takes about 5 times to get good at it, IME.  Virtual machines are very useful for this practice.

---

### Post by speartip on 2017-02-04
I've fell foul in the past, with un-restorable or corrupt backups. In my opinion the best backup facility for Linux users is Areca.
[http://www.areca-backup.org/](http://www.areca-backup.org/)
There is a bit of a learning curve, but it's worth it, for peace of mind.

---

### Post by bearlake on 2017-02-04
I have a spare drive that's great to restore my backups at here and there.

Lucky enough, never had one fail yet. ;)

---

### Post by deadflowr on 2017-02-04
> **aviator1 said:**
> Hello All:

I'm using Deja Dup to back up. I get the following message at the end of each back up.

```
/home/dave/.gnupg/gpg.conf
/home/dave/.gnupg/secring.gpg
/home/dave/.gnupg/trustdb.gpg
/home/dave/.mozilla/firefox/s38ux4vv.default-1457227414761/ffmpeg
/home/dave/Downloads/hplip-3.14.4
/home/dave/Downloads/hplip-3.14.4
```

What do I need to correct? Will I be able to recover if I have a failure and still have these errors?

Thanks for any response.


Typically when you get a list of files that deja-dup cannot backup, like the list above, you need to check what the permissions are for the files.
Having said that, it only means that those files will not be in the backups when you try to restore.
It should have zero effect on a restore.

---

### Post by TheFu on 2017-02-05
A key to doing system backups is to run them as root. That maintains the owner, group, permissions and if the backup tool is smart enough, ACLs.
There's a downside - running most GUI tools as root can cause issues, if not done correctly.  This is a main reason why I don't use GUI backup tools - that and cron won't run a GUI tool.

OTOH, I haven't used Deja-dup in years and only used it long enough to test it out.  I didn't like the idea of using "old school" backup methods and schedules.  Thought deja-dup was based on duplicity, which needs weekly "full" backups and daily "incrementals."  Moving a full backup offsite every week was more than my bandwidth could support.  But I could be wrong. Maybe the tool doesn't work that way? [https://wiki.gnome.org/Apps/DejaDup/HowItWorks](https://wiki.gnome.org/Apps/DejaDup/HowItWorks) says it does and that they don't think time to backup is important.
> Déjà Dup assumes that disk space is cheap, that time-to-backup isn't a terribly important detail, and that safety of data is paramount. 
I choose something else for backups, correctly.  My requirements are different from theirs. They don't intend to perform system-level backups, just user data.

---

### Post by aviator1 on 2017-02-07
Thanks everyone. I have been away for a few days and could not respond.

The restore worked fine.

Regards.

---

