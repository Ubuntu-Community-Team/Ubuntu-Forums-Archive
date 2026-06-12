---
title: "Mysql backup file permission denied :'("
date: 2008-04-26
forum: General Help
---

### Post by NawaMan on 2008-04-26
Hi there,
    I've just finish installing Hardy Heron. And I found that my musics database (Aramok) cannot be read by MySQL. Before the format, I use Gutsy and I copy my DB files (those in /var/lib/mysql) to my home partition and create a symbol-link back to /var/lib/mysql changing appropriate owner and permission (mysql:mysql and 770). And I can use the DB normally. I actually did this since I use Feisty so I am quite sure it works (I am not sure any more :'( ).

When I use other tools like MySQL Administrator to look at the Database it said
```

Could not retrieve schema table definitions from server
MySQL Error Nr. 1018
Can't read dir of './MyMusics/' (errno: 13)

```

When I use mysql -u root -p and see into the DB it said

```

mysql> SHOW TABLES;
ERROR 1018 (HY000): Can't read dir of './MyMusics/' (errno: 13)

```

I am very sure that I set owner and permission correctly and also use the name username and password (for root). So there should be no different from other times.

I have a lot of music rating in there :'( and Really don't want to loose it. Please someone ... anyone ... help me :'(

Thanks in advance

Edit: I solve it. The problem is about symbolink. I copy the actual files to the '/var/lib/mysql' and bang! It works. This is great. But what I am still wonder is why it used to work but now it is not.

---

