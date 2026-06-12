---
title: "Evolution and HDD crash"
date: 2008-05-21
forum: General Help
---

### Post by matthewboh on 2008-05-21
My laptop hdd finally died, but I was making backups.  I have a backup of the HDD, but I'm having problems figuring out how to get the info from Evolution back.

Evolution will import a backup, but I just backuped the folders - NOT an Evolution backup.  What do I need to put back?  I tried the giant hammer method, but that didn't work too well.

---

### Post by ctn03 on 2008-05-21
I have a slightly different problem but also would like to restore my settings and emails/calender from .evolution folder.  I'm  a newbie...Been using Ubuntu Hardy and Evolution without problems until yesterday when I ran evolution from the terminal --

ctn@ctn-XPS:~$ evolution

(evolution:8728): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/cuong/.recently-used.xbel', but the parser failed: Error reading file '/home/cuong/.recently-used.xbel': Is a directory.

(evolution:8728): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

Evolution would start but it takes me to the Setting Assistant instead of my email accounts...

Thanks a bunch.

---

### Post by SPr on 2008-05-21
> 
My laptop hdd finally died, but I was making backups. I have a backup of the HDD, but I'm having problems figuring out how to get the info from Evolution back.

Evolution will import a backup, but I just backuped the folders - NOT an Evolution backup. What do I need to put back? I tried the giant hammer method, but that didn't work too well.


Not knowing how you backed up your HDD I can't offer any specific edvice.

Evolution stores everything in the hidden folder /home/your_username/.evolution . In Nautilus press ctrl+h to show hidden files. Copy this folder from the backup to /home/your_usename .

---

### Post by matthewboh on 2008-05-21
Excellent!

Found the addressbook files and copied them over - worked great!

---

