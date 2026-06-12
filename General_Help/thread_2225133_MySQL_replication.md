---
title: "MySQL replication"
date: 2014-05-20
forum: General Help
---

### Post by gopukrishnan on 2014-05-20
I have two ubuntu 14.04 servers A and B replicating each other(MySQL Master-Master). I think all the permissions such as '**grant replication slave**','**CHANGE MASTER TO MASTER_HOST**' are storing in the database mysql, correct ?. Suppose I take the mysqldump of the first server as below :  ```
mysqldump -u root -ppassword --all-databases > /location_of_backup_server1/backup.sql
```  and restoring it in the second server as below :

  ```
mysql -u root -ppassowrd < location_of_backup_server2/backup.sql
```  Will it break the replication ? (all the grant privileges in the  server2 (mysql database) is replaced by the grant privileges in server1  ??)
  What if I take the full backup of a server that is not part of these  master-master replication and restoring to one of the servers in  master-master sync ? I want to confirm these before trying in the actual  servers.

---

