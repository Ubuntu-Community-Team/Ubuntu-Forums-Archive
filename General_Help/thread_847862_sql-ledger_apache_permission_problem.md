---
title: "sql-ledger apache permission problem"
date: 2008-07-02
forum: General Help
---

### Post by Marty4344 on 2008-07-02
I just installed sql-ledger on my 8.04 ubuntu laptop along with apache.  Apache works fine but when i try to login to the admin section for the initial setup which is [http://localhost/sql-ledger/admin.pl](http://localhost/sql-ledger/admin.pl) I get this message

Error!
users/members: permission denied.

I know this it probobly a permission error but im just wondering what it is im doing wrong.  Has anyone ever used this because I cannot figure out what it is im doing wrong.  Any help would be greatly appreciated.  Or if you could think of something better then sql-ledger that is similar to quickbooks let me know.  I would rather not try to run quickbooks in wine or vmware because im trying to keep it all linux and open source.

---

### Post by Marty4344 on 2008-07-03
*bump*

---

### Post by Marty4344 on 2008-07-04
anyone?

---

### Post by tedjordan on 2009-02-25
it's been years since I've set this up, but I think that I had to make my user
part of the apache group or sql-ledger group in /etc/group file

---

### Post by tpcarmen on 2009-04-20
> **Marty4344 said:**
> anyone?

The users subdirectory needs to be:

chown -R apache:apache *

(or whoever apache runs as).

FWIW, sql-ledger needs a much better installer.

Terry

---

