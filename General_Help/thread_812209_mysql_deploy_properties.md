---
title: "mysql deploy properties"
date: 2008-05-29
forum: General Help
---

### Post by anderskitson on 2008-05-29
I am supposed to configure deploy properties for a program, that coincide with mysql-server that I have installed, it gives instructions to do so, but they are for windows, yet they have a linux download. Anyways they tell me to do this
> Enter grant all privileges on {schema_name}.* to
‘{db_user}@’{web_server_name}’ identified by ‘{db_password}’
with grant option;


I get an SQL syntax error, I just copied and pasted it, are the windows commands for mysql different than linux. Also in the deply properties it asks me to define some things, which arent there I am not sure if I am supposed to create them, or if this is not needed in linux. For example

> db_user =User name to create for
your MySQL database

schema_name =name of schema to create

There are others as well.

To give you background into what I am doing, I am installing a sdk called caCORE which stands for cancer biomedical information grid, I am working for a doctor in a lab, and we are chaning all of there ms access database over to mysql, they wanted this caBIG The programs are written in java, they use argouml for uml modeling mysql for the databse server, jboss as the application server and Ant as the build tool. I will attach a copy of the deploy properties file, if anyone could help that would be great. I installed mysql-server from synaptic package manager if that matters. I edited the deploy.properties a little bit adding the lab471 and 471msb part

---

