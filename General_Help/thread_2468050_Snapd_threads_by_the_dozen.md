---
title: "Snapd threads by the dozen"
date: 2021-10-17
forum: General Help
---

### Post by 21Jerry on 2021-10-17
I ran 18.04 server for a long time then upgraded to 20.04.  Since that time, and granted maybe I never noticed, I'm seeing quite a few snapd x 42 and mysqld x 33 threads running.  

They are listed as /usr/lib/snapd/snapd and /usr/sbin/mysqld.  They run all the time.  The system is a private owncloud server that hosts timemachine backups, none of which are running right now.   

Normal?

Thanks,

Jerry

---

### Post by The Cog on 2021-10-17
At least one snapd thread is normal - it's the daemon that runs snap packages (a kind of jail for some applications). I don't know if lots of snapd threads is normal - I would have thought not but I'm not sure because I always uninstall snapd as part of my installation procedure. But it does make me think that maybe there are some snap applications running.
mysqld is a database server application, and is not part of a normal installation. But when it is running, it does tend to run lots of threads.

Could both of these be part of timemachine? I don't know, I've no looked at timemachine.

---

### Post by 21Jerry on 2021-10-18
the mysql could be from OwnCloud as it uses it, maybe each device of which there are 10 or so, needs two sessions.  But the snapd stuff doesn't look normal.  Also, it seems like even with very low CPU after a reboot my memory is high, in the red and I have 48Gb in that server.

---

