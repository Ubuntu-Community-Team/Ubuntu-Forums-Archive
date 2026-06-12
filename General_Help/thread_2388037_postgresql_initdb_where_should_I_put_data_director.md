---
title: "postgresql initdb where should I put data directory"
date: 2018-03-27
forum: General Help
---

### Post by Sherman_Willden on 2018-03-27
User: Sherman
Platform: HP Compaq 6710b
Operating System: Ubuntu 17.10
postgresql: 10

I just installed postgresql 10 using add-apt and apt-get. When I start initdb it asks for a data directory. Where do you put your data directory? Do I really need to perform initdb?

Thank you;

Sherman

---

### Post by SeijiSensei on 2018-03-28
If you installed the postgresql-10  package from the repositories, the data directory is /var/lib/postgresql/10/main.  Other files like postgresql.conf and pg_hba.conf are stored in /etc/postgresql/10/main.

I didn't have to do anything to configure this out of the box.  Just starting the postgresql service was sufficient.  

If you installed postgres some other way, please give us a more explicit description of the steps you took.

---

