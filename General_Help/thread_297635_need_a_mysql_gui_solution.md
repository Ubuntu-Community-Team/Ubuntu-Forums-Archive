---
title: "need a mysql gui solution"
date: 2006-11-11
forum: General Help
---

### Post by nephish on 2006-11-11
Hey there,
I have a mysql server running on ubuntu edgy.
i really need a database front end for it that is fairly easy to use for someone comming from access. There are a lot of them out there, but i cant seem to find one that does all that i need.
here is what i have tried.

knoda = very good, but no way to set up table relationships.
openoffice.org = also good, but crashes on me with larger tables. Also will not let me set up table relationships
kexi = cool kde app, but will not allow me to import tables (keeps giving me sql errors) also, dont know if it allows me to edit stuff in place, looks like it wants me to import into a file or other database and edit from there ( which is kinda useless for me )
mergeant - pretty cool, i think, cant figgure out how to connect it to mysql. I think it can be done, but the only database provider that seems to come installed on it is the xml one.
phpmyadmin - good, but slow, and browser based, i really need a desktop app.
flashadmin = also cool, and prettier than phpmyadmin, but falls short for the same reason.

so, if anyone has an app suggestion, or a way to fix one of my above troubles, please, please let me know

if you have read this far, thanks for your time

---

### Post by adwait on 2006-11-11
Try mysql-admin....

---

### Post by nephish on 2006-11-11
yeah, i like mysql-admin, but it does not give me the ability to actually get at the data in the tables ( unless i am missing something about how to )
thanks

---

### Post by adwait on 2006-11-11
I don't remember correctly, but I think you can select a database and then go to the views tab. There, add a view like "select * from <table>", and you can view the contents of the table. Alternativels, Right Click>Edit Table Data can also be used...

---

### Post by Elaztic on 2006-11-12
From synaptics you can install mysql query browser.
Together with mysql admin you have a pretty good GUI solution.
Hope it works for you.

---

### Post by pismo on 2006-11-16
Have you had alook at Glom

---

### Post by nephish on 2006-11-16
Hey thanks for the tips, gents.
i was not able to connect glom to a mysql database. I think it might be postgre only. Unless i am doing something wrong.

i was able to create views from multiple tables in knoda, but have found myself unable to edit from with them.

thanks again for that tip, i am using it now.

---

### Post by druhboruch on 2006-11-16
Mysql Admin does not work for me.  It hungs while I try to access user management tab.  Query browser works great though.

---

