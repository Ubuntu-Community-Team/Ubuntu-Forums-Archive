---
title: "Apache &amp; Mounted Drives"
date: 2005-06-09
forum: General Help
---

### Post by boosted on 2005-06-09
Is it possable to have someone download a file by clicking on a hyperlink, but the file is on another Hard Drive?  The hard drive is mounted to /media/winblows/  but the server is in /var/www/  is this possable someway?  with out moving the file to the /var/www/  directory?

---

### Post by defkewl on 2005-06-09
Could you please state what you're trying to achieve more briefly?

---

### Post by boosted on 2005-06-09
alright, ubuntu is installed on a 40gb HDD I want to run a web site with a forum and a whole bunch of videos etc...  the forum is fine to be running on my 40gb but all my videos and big files are on a 250gb HDD that is mounted in /media/winblows/  so I am asking how to make apache see that 250gb HDD and let me create hyper links to those videos for people to download!   Hopefully  I explained this good enough  LoL
Thanks

---

### Post by boosted on 2005-06-10
can anyone help me out here? this is the only thing holding me back right now.....
Thanks!

---

### Post by boosted on 2005-06-10
well, I kinda have it worked out!  I mounted hda1 to /var/www/   instead of /media/winblows/  now my question is ... is there a way to just mount certain directories from /hda1  instead of the whole drive?  say like mounting a folder called "downloads" from hda1 to /var/www/  ???   is this possable?

---

### Post by Zifnab on 2005-06-10
Create a symlink (with the "ln" command) in your /var/www/ directory that points to the /media/winblows/ directory, then make sure the user called www-data has read access to that media directory. (If you do this by modifying your /etc/group file, you'll need to reboot before the change takes effect.)

I'm sure there are more direct ways to do this with the config files, but I've yet to take the time to figure those out, and this should work quite well.

---

### Post by boosted on 2005-06-10
thanks for the reply....  I am a Linux noob!  could you please explain a sym link?  Not sure exactly what this is or how to set it up right.  
thanks

---

### Post by boosted on 2005-06-10
hhmm.....  i just found this on unofficial ubuntu guide...  just kinda stubled accross it.  I havn't tried it yet but here it is!

Q: How to map URLs to folders outside /var/www/?

   1. Read General Notes
   2. Read How to install Apache HTTP Server for HTTP (Web) Server service?
   3.

sudo gedit /etc/apache2/conf.d/alias

   4. Insert the following lines into the new file

Alias /URL-path /location_of_folder/

<Directory /location_of_folder/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>

   5. Save the edited file (sample)
   6.

sudo /etc/init.d/apache2 restart

   7. [http://localhost/URL-path](http://localhost/URL-path)

---

### Post by Zifnab on 2005-06-10
The "ln" command creates links. The -s option creates symbolic links, or symlinks.

So do this:

```
cd /var/www/
ln -s /media/winblows/ winblows
```

This will create a symbolic link in your www folder to the winblows folder. Meaning that /var/www/winblows/ goes to the same place as /media/winblows/. Since everything under /var/www/ can be seen on the web, now your media folder can too!

Though as I said before, make sure the user www-data has read access to that folder. If you don't want to deal with groups, just make it so everyone has read access.

---

### Post by boosted on 2005-06-10
Tanks!  that workd great!  I would like to make at least 2 symlinks example:
from /media/winblows/downloads
and
from /media/winblows/from laptop/downloads

to the dir
/var/www/fs/files/  

I can get the first one to work with the command you gave me but when I try to do the second one I get this error?

ln: when making multiple links, last argument must be a directory

I tried all kinds of different ways but just keeps giving me that same error.. any ideas?

---

