---
title: "Cant logging on to oracle"
date: 2008-05-23
forum: General Help
---

### Post by SteBed on 2008-05-23
I'm in the same situation.. tried reinstalling Oracle several times and i still can't login. Would love some help on this one!
Thanks

---

### Post by jaruti on 2008-07-07
This happened to me too --very frustrating.

After looking around in /etc/init.d/oracle-xe, here's what worked for me:

From the command line:

```
cd $ORACLE_HOME/bin
sudo su oracle
./sqlplus

```

And then in sqlplus:

```
alter user system identified by "some-password";
```

You should now be able to log in.  I hope this helps someone in the future.

---

