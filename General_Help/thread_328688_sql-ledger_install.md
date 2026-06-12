---
title: "sql-ledger install"
date: 2006-12-31
forum: General Help
---

### Post by GoldWing on 2006-12-31
What I did:
-installed sql-ledger with apt-get
-installed postgresql-8.1 with apt-get
-createuser -d sql-ledger
-createlang plpgsql template1

-changed /etc/postgresql/8.1/main/pg_hba.conf to reflect "local all all trust"
-restarted postgresql-8.1

I am still receiving "FATAL: IDENT authentication failed for user "sql-ledger" when login on to admin.pl

Can someone point me in the good direction ?

---

### Post by got_nix on 2007-04-28
I'm of no use to you as yet.. because i cant figure out how to access the application.. i installed it via apt-get and would assume that since its a web based app it'ld be in lloal host however its located in /usr/share..

I created a symbolic link of the path to sql-ledger and placing that in my public_html dir but that also failed.. some assistance would be appreciated. thanks

---

### Post by jonny on 2008-01-08
> **GoldWing said:**
> What I did:
-installed sql-ledger with apt-get
-installed postgresql-8.1 with apt-get
-createuser -d sql-ledger
-createlang plpgsql template1

-changed /etc/postgresql/8.1/main/pg_hba.conf to reflect "local all all trust"
-restarted postgresql-8.1

I am still receiving "FATAL: IDENT authentication failed for user "sql-ledger" when login on to admin.pl

Can someone point me in the good direction ?
Did you switch to the postgres user before running the createuser and createlang commands?  You can do it with this command: ```
sudo su - postgres
```

---

### Post by jonny on 2008-01-08
Hmmm... just realised that the OP was 2006, not 2007.  Guess I'm a little too late responding!

---

