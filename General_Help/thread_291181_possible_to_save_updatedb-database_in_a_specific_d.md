---
title: "possible to save updatedb-database in a specific directory?"
date: 2006-11-02
forum: General Help
---

### Post by loko on 2006-11-02
hello,

i would like to save the database that is created when running updatedb in a directory of my home-partition.

background why to do this:

my /home-partition is encrypted, but the best encryption isn't helpful if updatedb-database contains the names of all files you have on your harddrive.

does somebody know how to do?

And no, i won't encrypt my /root - i think this is needless.

---

### Post by galileon on 2006-11-02
i get the impression its this file 

/var/lib/slocate/slocate.db

but you have to try and check this...

---

### Post by galileon on 2006-11-02
indeed this appears to be right:

galileon@Griffin:~$ sudo ls /var/lib/slocate/ -lh
total 3.6M
-rw-r----- 1 root slocate 3.6M 2006-11-02 09:31 slocate.db
galileon@Griffin:~$ sudo updatedb
galileon@Griffin:~$ sudo ls /var/lib/slocate/ -lh
total 3.8M
-rw-r----- 1 root slocate 3.8M 2006-11-02 11:55 slocate.db
galileon@Griffin:~$

---

### Post by loko on 2006-11-02
galileon,

you're right with this, but the question is:

Is it possible to tell updatedb to create this database (for example) in /home/123/database?

---

### Post by nikhilk on 2006-11-02
> **loko said:**
> galileon,

you're right with this, but the question is:

Is it possible to tell updatedb to create this database (for example) in /home/123/database?
Yes it is, just run the updatedb command with the -U switch.
For the example you gave the command will be
```
updatedb -U /home/123/database
```

---

### Post by loko on 2006-11-02
nikhilk, 

sorry but this is the wrong option, all -U is doing is start creating the database at /home/123/database.

This doesn't mean the database is created there.
It only put everything in /home/123/database and it's directories in there in the database.

---

### Post by loko on 2006-11-02
ok,

maybe i can make updatedb work that my /home-partition is not checked by it, so i found this option:

```
updatedb -e /home
```

the question now is, where can i put this option in?:

can i put it in /etc/cron.daily/slocate?

or should i put it in /etc/updatedb.conf?

---

### Post by nikhilk on 2006-11-02
Ok, NOW I get what you are trying to do. Sorry for the confusion, my bad, I did not read your first post completely.

I believe what you are trying to do is not supported by updatedb/slocate. I guess this is because of the fact that running updatedb is not a trival operation, it requires considerable resources (time, memory, CPU etc). So creating the database per user is not such a good idea.

As far as the security aspect is concerned, since updatedb cannot be run by a non root user that itself provides some degree of security. Morever you can specify which directories you want to exclude so you can exclude your "top_secret" directory if you want.

I hope this, atleast partially, answers your question.

---

### Post by galileon on 2006-11-02
or encrypt ur /var/lib...

---

### Post by nikhilk on 2006-11-02
In the "/etc/updatedb.conf" file you can specify the directories you want to exclude.

PRUNEPATHS="/tmp"
export PRUNEPATHS

As seen in the above example the PRUNEPATHS variable should be set to exclude the directory you want. If there are multiple directories you want exclude, just seperate them with a space e.g

PRUNEPATHS="/tmp /dir1 /dir2"
export PRUNEPATHS

---

### Post by loko on 2006-11-03
thanks for the tip

---

### Post by nikhilk on 2006-11-03
Let us know if the "PRUNEPATHS" method works for you.

---

