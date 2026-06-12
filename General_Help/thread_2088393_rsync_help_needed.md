---
title: "rsync help needed"
date: 2012-11-26
forum: General Help
---

### Post by antoine2223 on 2012-11-26
I need to exclude   certain  folders during rsync  .but i does not work i need a help from you guys 


i have a cronjob like this 

0,10,20,30,40,50  * * * * rsync -raz --progress --delete-after  --exclude-from=/root/exclude.rsync /www/ [EMAIL="root@vm03.xxxxomain.com"]root@vm03.xxxxomain.com[/EMAIL]:/www/ > /dev/null


my /root/exclude.rsync  file contains the files which to be excluded .
- /var/www/extranet/tmp/*
- /var/www/extranet/dvd/*


after doin this i tried to create  file in folder  tmp but its been copied 
need your ideas or in which part have i done mistake  .

---

### Post by The Cog on 2012-11-26
Plese use code tags round your code postings - it makes things much easier to read. Click Advanced while composing the post and use the # button on the toolbar.

I don't think the * works in the exclude file - try just naming the directory you want to exclude.
```
/var/www/extranet/tmp
/var/www/extranet/dvd
```

---

### Post by antoine2223 on 2012-11-26
hello , i  have tried it .

my exclude  file looks like this 


i did some googling but of no use . please do guide me in this context

---

### Post by oldfred on 2012-11-26
I do not understand all the details but mine works. I have excludes file in same folder as mybackup.sh rsync script.

one of several lines from:
#mybackup.sh
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

```
# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

```

---

### Post by antoine2223 on 2012-11-26
mine actual looks like this


   
  - /var/www/extranet/tmp/*
  - /var/www/extranet/dvd/*
  - /var/www/extranet/www/tmp/*
  - /var/www/nga-1001/www/flux/*
  - /var/www/nga-1004/www/flux_pericles/*

and i have changed to urs can u tell me am i right  because in each folder there are lot of children folders


/var/www/extranet/tmp/*/
 /var/www/extranet/dvd/*/
 /var/www/extranet/www/tmp/*/
 /var/www/nga-1001/www/flux/*/
 /var/www/nga-1004/www/flux_pericles/*/

---

### Post by antoine2223 on 2012-11-26
sorry error in my part 

/var/www/extranet/tmp/*
 /var/www/extranet/dvd/*
 /var/www/extranet/www/tmp/*
 /var/www/nga-1001/www/flux/*
 /var/www/nga-1004/www/flux_pericles/*

since i am beginer , i added the slash , my fiel looks like this .

---

### Post by vanadium on 2012-11-26
In the command line, I think you must precede each directory you want to exclude by the --exclude option, i.e.
```

rsync -raz --progress --delete-after --exclude-from=/root/exclude.rsync --exclude-from=/www/ --exclude-from=root@vm03.xxxxomain.com:/www/

```

---

### Post by antoine2223 on 2012-11-27
hello vanadium , 

by using the command wont i be loosing  the whole www structure ?

rsync -raz --progress --delete-after --exclude-from=/root/exclude.rsync --exclude-from=/www/ --exclude-from=root@vm03.xxxxomain.com:/www/

---

### Post by vanadium on 2012-11-27
My bad. I neglected that the exclude-from option is an option to provide the exclusion patters from a text file, which is indeed what you do: I was not carefull, sorry.

The format of your text file looks good to me. However, your "from:" directory is "/www/". The paths you mention in your exclude file, though, are outside of that /www directory, under /var/www. Probably your "from" directory should read /var/www/ as well. Otherwise, the /var in tje paths listed may need to be remeoved if /www is really your source.
```

rsync -raz --progress --delete-after --exclude-from=/root/exclude.rsync /var/www/ root@vm03.xxxxomain.com:/www/

```
This way, the rsync command would copy /var/www/* and below, and subdirectories such as /var/www/extranet/tmp/* would be excluded.

---

