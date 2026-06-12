---
title: "Sync files on a dual boot system."
date: 2007-12-15
forum: General Help
---

### Post by Innomado on 2007-12-15
I am dual booting Vista Business and Ubuntu 7.10 and want to share the files in the htdocs directory of XAMPP on Ubuntu so that they can be accessed through WAMPServer or XAMPP on Vista. I have NTFS-3g but do not have a way of accessing ext3 file systems from windows.

Within Ubuntu I can use links to access files located outside of the htdocs directory but only when the directory I am linking to is inside of my Ubuntu partition, the only files I have tested this with have been inside my ~/ directory. When the files are located on another partition that could be read by windows, NTFS or FAT32, I am told that I don't have permission to access that directory through my server.

Is it possible to have a a single directory that can contains all of the files I am working on to be accessed through the test servers on either OS?

If not is there a simple way to sync the contents of the XAMPP htdocs directory with the coresponding directoy of my windows test server?

I would apreciate any help or direction that can be given.

---

### Post by jken146 on 2007-12-15
[http://www.fs-driver.org/](http://www.fs-driver.org/) This is a windows driver for ex2/3 filesystems.  I don't know about your permissions problem with NTFS partitions though,

---

### Post by Innomado on 2007-12-15
Thanks, but being able to interact with my ext2/3 filesystems from windows doesn't get at my main problem, which is syncing the contents of the directories that each local test server uses as the document root when serving files up to my browser. I could sync things up  manualy but that is a hassle and prone error, Any suggestions.

---

### Post by HermanAB on 2007-12-15
Simple - don't synch things up.  Only use a single store, either on Ext3 or on NTFS, don't duplicate the information it just wastes disk space anyway.

Cheers,

H.

---

### Post by Innomado on 2007-12-15
Well yes, like I said in my first post I would prefer one single file, syncing multiple files is my second option. What I am wondering is how to achieve this, I have spent over two days trying to get it to work with no success.

---

### Post by r-mo on 2007-12-15
If you get the driver working in windows to access your ubuntu partition that's probably easiest as I'm unsure of the permissions to use to make linux apache access an ntfs volume (I added www-data to the plugdev group when I did it, which was probably horribly insecure)

Anyway to get windows apache to point to your linux web root.

Open c:\program files\Apache...\conf\httpd.conf

and find the line 
```
DocumentRoot c:\some\kind\of\path
```
then do a find+replace on the path to change it to point to your /var/www

If you'd rather go down the linux pointing to ntfs route, in a normal apache install (not sure about xampp) the config file to modify is /etc/apache2/sites-available/default and replace /var/www with /media/windows/whereever

Hope this helps

---

### Post by Innomado on 2007-12-16
Thanks r-mo, that should be what I am after. I was thinking today that the next thing to look at would be changing the designated document root for apache. I would prefer to make the changes on the linux side but you have given me several things to look into that should get me to a solution. Thanks again.

---

