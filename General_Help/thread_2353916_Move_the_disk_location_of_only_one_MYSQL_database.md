---
title: "Move the disk location of only one MYSQL database"
date: 2017-02-26
forum: General Help
---

### Post by steveearle86 on 2017-02-26
Hi all,
Just wondering if there is any way to move only one MYSQL database directory?

I have a MYSQL server set up with multiple databases. I run a zoneminder CCTV setup and have a dedicated volume for all the zoneminder event files. I would like to have the Zoneminder database on the same volume as the files, currently the database resides in /var/lib/mysql/zm. I do not want to move my other SQL databases

All Googling just seems to point to moving the whole data directory which is not exactly what I want to do.

Can it be done?

---

### Post by SeijiSensei on 2017-02-26
Move the directory to the new location, then create a symbolic link to that place in /var/lib/mysql.  Stop the mysql service, then run
```

cd /var/lib/mysql
sudo rsync -av zm /path/to/new/location/
sudo mv zm zm.old
sudo ln -s /path/to/new/location/zm

```
Now restart mysql and see how things go.  If it works as before you can delete zm.old.

---

### Post by steveearle86 on 2017-02-26
Hi,
sorry was just writing a reply as you replied! I tried exactly the same thing funnily enough.

I also did ```
sudo chown root:root /path/to/new/location/zm
```
and then restarted the service and when I load it up in Mysql workbench it says tables cannot be fetched

---

### Post by SeijiSensei on 2017-02-26
The new zm must be owned by mysql:mysql.  On Ubuntu, the database directories have 755 permissions, but for better security use 700 like RedHat flavors do.  The files in zm should have 660 permissions and be owned by mysql:mysql.  Something like this:
```

cd /path/to/new/location
sudo chown -R mysql:mysql zm
sudo chmod 700 zm
cd zm
sudo chmod 660 *

```

MySQL runs as the mysql user, so that user needs to have permissions in the directory.  

The symbolic link in /var/lib/mysql can be owned either by root or mysql because it's transparent.  What matters are the permissions on the linked directory.

---

### Post by steveearle86 on 2017-02-26
Thanks for your reply,

I have fo[FONT=arial][/FONT]llowed[FONT=arial] the instru[/FONT]ctions in your latest post and I am still getting he same result through Workbench.

I tried with both 755 and 700 permissions.

using ls-l, I can see the zm directory in the source and its contents are owned by mysql.

To test, I have ensured 
```
/path/to/new/location/ 
```

[FONT=arial]is on the system drive, the same drive as the current mysql directory, to rule out any mount / filesystem issues and I still get the same result[/FONT]

---

### Post by steveearle86 on 2017-02-26
AppArmour issue maybe?

---

### Post by steveearle86 on 2017-02-26
Fixed! it turned out to be an AppArmor issue.

Edited
```
/etc/apparmor.d/usr.sbin.mysqld
```

added 

```
/path/to/new/location/ r,
/path/to/new/location/** rwk,

```

under the section
```

# Allow data dir access

```

restarted apparmor and it worked :p

Thanks for your help!

---

