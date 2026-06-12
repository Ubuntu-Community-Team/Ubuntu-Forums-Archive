---
title: "Libreoffice Base - one database used by miltiple users/computers"
date: 2015-01-19
forum: General Help
---

### Post by Tristan_Williams on 2015-01-19
How can I use a Libreoffice Base database on multiple computers and by multiple users? It wouldn't be in an environment where data changes would be causing conflicts, so don't worry about that.

I basically want one database, for example a small business log of orders, assets, and contacts, to be available on my desktop, laptop, and a few other employees laptops. We haven't got much data in the database, so it could easily be inserted to a new database if we have to restart from the beginning and make a new database. It does need to be in Libreoffice though.

---

### Post by grahammechanical on 2015-01-20
It is a little while since I messed with Libreoffice Base and I am no expert but I notice that the underlying database file has the odb file extension after the name that we give to the database we are creating.

And if I remember correctly the bit where we users enter data into the database which we usually think of as the database is called a Form. The database.odb file would need to be stored at a location that can be accessed by all machines. And the form would need to be created on each machine. But you could use the Libreoffice File>Open dialog to browse to the location of the database.odb file and open it in Libreoffice Base and work on it from any of those machines that can access the location. If the location of the file is mounted then the Files>Recent list should show the database.odb file.

Regards.

Regards.

---

