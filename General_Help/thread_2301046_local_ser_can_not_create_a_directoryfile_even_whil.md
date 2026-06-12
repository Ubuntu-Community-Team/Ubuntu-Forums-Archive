---
title: "local ser can not create a directory/file even while he is added in www-data roup"
date: 2015-10-30
forum: General Help
---

### Post by alain.roger on 2015-10-30
Hi,

as user i'm added into www-data group.
the www-data group is owner of /var/www firectory.
when i want to create a file of folder in /var/www i can not and i'm forced to use "sudo", what logically add root:root for owner of that file.
why ?

how can i automatically create folder and file as local user "alain" who is a member of www-data group ?
thx.

---

### Post by ian-weisser on 2015-10-30
> **alain.roger said:**
> the www-data group is owner of /var/www firectory.
Close. The www-data *user* (not the similarly-named *group*) is the owner of that directory.

Groups can't own files and directories.
Members of the www-data *group* (including alain) can read and edit and maintain /var/www files owned by www-data without using sudo.

But any NEW files alain creates are owned by alain, not www-data. If the server application lacks permission to read alain's files, you might get a mysterious permission error.

One answer is for alain to simply chown newly-created files to www-data.
Another answer is to use Sudo's -u flag to create the file as www-data instead of root.

---

### Post by SeijiSensei on 2015-10-30
1) You can make www-data your primary group by editing the entry for "alain" in /etc/passwd (with sudo) and changing your group to 33, the group ID for www-data.  Your record will look like this:
```
alain:x:1000:33:Alain Roger:/home/alain:/bin/bash
```
You may or may not want to do this since every file you create will be assigned the www-data group.  You could create another user account just for web authoring that belongs to the www-data.

2) Another option that doesn't require changing your group is to set the [SGID]("http://www.linuxnix.com/sgid-set-sgid-linuxunix/") bit on /var/www/html so that all files created will inherit the directory's group rather than your own.  First, add yourself to the www-data group with the command:
```
sudo adduser alain www-data
```
Now change the permissions on /var/www/html:
```
sudo chmod g+ws /var/www/html
```
That makes the directory writable by members of group www-data and any new files will inherit the group from the directory.  Now give it a try:
```
$ touch /var/www/html/test
```
Then if you run "ls -l /var/www/html" you should see
```
-rw-rw-r-- 1 alain      www-data     0 Oct 30 12:38 test
```

---

### Post by alain.roger on 2015-10-30
basically i already step 2, so i already added user (alain) to group www-data.
i did sudo chmod g+ws /var/www
but the touch /var/www/test.html is refused due to invalid permission :(

---

