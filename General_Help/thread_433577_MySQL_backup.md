---
title: "MySQL backup"
date: 2007-05-05
forum: General Help
---

### Post by daz4126 on 2007-05-05
Hi,

I've recently done a clean install of Feisty and realised that I've lost my previous MySQL databases. Nothing too important, but rather annoying to have to reinstall and then set the databases up again. I keep my home directory separate which helps with most settings, but is there an easy way to backup any MySQL databases for future upgrades? I know that this wouldn't happen if I did an upgrade instead of a clean install, but after Edgy, I have decided that clean install is the best option.

thanks,

DAZ
ps - how come the Firefox logo has gone back to the globe in Feisty? I thought the Fox logo was here for good now?

---

### Post by iBix on 2007-05-05
You might wish to try phpmyadmin. 


You can export and import mysql databases in different formats like zip, tar etc.. 

I just tried the system and it seemed to work fine at least as far as exporting all databases from remote webserver (ubuntu) to my test setup in  os x bp. 

in this case i exported two wprdpress databases, but as i did not have similar wordpress installations on my laptop i could not test wheter the import worked all the way. Basically what happened was that i could see my databases in the mysql installed on my laptop, but did not see them at work on wordpress... :( 


I also think creating a backup of your /var/lib/mysql/ directory would be reasonable. (or whatever DATADIR your mysql is using)

---

### Post by daz4126 on 2007-05-06
That's just what I want to do (export the databases), can I do this without phpmyadmin? Or would it just be easier to make a backup of /var/lib/mysql? (how would I know if this is the datadir that mysql is using?

thanks for the reply,

DAZ

---

