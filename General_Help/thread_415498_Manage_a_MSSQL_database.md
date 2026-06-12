---
title: "Manage a MSSQL database"
date: 2007-04-20
forum: General Help
---

### Post by scotty32 on 2007-04-20
ok, so i made the move to ubuntu a few weeks ago and everything went fine

but i cant seem to get into MSSQL databases...

.. as i started off as an ASP developer, i have websites in ASP running of MSSQL databases, and i cant connect to the DBs to manage them

before i moved i saw in OpenOffice you could connect to them and i thought "ah great that'll be ok"

but on linux, it doesnt list it.

done searchers and it mentions JDBC but that doesnt seem to be working and nothing i try seems to work, and theres very little i can find on it.

anyone know any programs, or even a way to get Open Office to connect to it?

---

### Post by hvbakel on 2007-04-20
I think the default mysql server install is configured to only allow connections from localhost. If you need to connect to it from other machines you need to edit /etc/mysq//my.conf. Then change the following line:

```
bind-address          = 127.0.0.1

to

# bind-address          = 127.0.0.1
```

---

### Post by ysse on 2007-04-20
It should be possible to connect with JDBC, using a URL like jdbc:microsoft:sqlserver://yourhost:1433

For JDBC to work, you will need specific JDBC drivers for MSSQL, just like you needed ODBC drivers in Windows for MSSQL, Oracle etc. I don't know if OpenOffice would fill your needs, but it does have a generic JDBC connection. You might try general SQL clients like henplus (in synaptic) if all you need is a way to run SQL statements.

/Anders

---

### Post by PaulHuffman on 2007-10-15
What do I use for a JDBC Driver Class in the OO Database Wizard?

---

### Post by jordoncm on 2008-05-06
I actually had this same problem myself and I figured out how to get OpenOffice.org to connect to MSSQL. It took me a bit of research but I got it working.

I put together an article with instructions, I hope this helps.

[http://www.finefrog.com/2008/04/14/connecting-to-an-mssql-server-and-others-with-openofficeorg/](http://www.finefrog.com/2008/04/14/connecting-to-an-mssql-server-and-others-with-openofficeorg/)

---

