---
title: "How to set up progresql in Ubuntu 6.06"
date: 2006-11-12
forum: General Help
---

### Post by Nebu Pookins on 2006-11-12
I'm trying to set up egroupware, and it told me my DB is not working. So I checked synaptic, and I discovered progresql wasn't even installed. So I installed the progesql-8.1 package, and the installer didn't ask me any questions, so I don't know what the password for the DB admin is, or how to access the DB, or anything like that.

egroupware gives me the instructions:

[I]Start the postmaster
[user@server user]# postmaster -i -D /home/[username]/[dataDir]
Create the empty database -
[user@server user]# createdb egroupware[/I]

But postmaster isn't a recognize command on my system. Not sure how to proceed from here. What further steps do I need to perform to get progresql set up?

---

### Post by kishd on 2006-11-12
run "sudo /etc/init.d/postgresql-8.1 start" to start the daemon. Also enable it to startup in system>administration>services

---

### Post by Nebu Pookins on 2006-11-13
Thank you. The DB server is now running, but I still don't know what the username and password of the root account for the DB server is, and I don't know how to create more users in the DB server. I still need to create a database called "egroupware", and create a user with read and write access to that database.

---

