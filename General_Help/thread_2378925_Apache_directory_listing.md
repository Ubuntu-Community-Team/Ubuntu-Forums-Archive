---
title: "Apache directory listing"
date: 2017-11-29
forum: General Help
---

### Post by asai on 2017-11-29
Hi,

I have an issue with my apache web server.
I want to be able to list the directory content of a specific folder.
In my apache.conf I have done this:

```

Alias /documents "/home/terje/Dropbox/server_backup/documents/Regnskap/"
<Directory /home/terje/Dropbox/server_backup/documents/Regnskap/>
	Options +Indexes
	AllowOverride All
	Require all granted
</Directory>

```

However, when I go to this directory from a browser, it says:
**Forbidden**
You don't have permission to access /documents on this server.

---

### Post by irv on 2017-11-29
What I do is this: from my laptop, I use Filezilla, and log in to my server and I can view everything in any directory.
Make sure you use SFTP - SSH File Transfer Protocol when setting up Filezilla.
Did you use sudo to view documents?

---

### Post by Holger_Gehrke on 2017-11-29
Check the permissions of the directory in the file system. Apache has to be able to read the directory and change to it. AFAIK apache runs as user:group www-data:www-data, so your best bet is to change the group of the directory to that and allow read and execute for the group:
```
sudo chgrp www-data /home/terje/Dropbox/server_backup/documents/Regnskap/
chmod g+rx-w /home/terje/Dropbox/server_backup/documents/Regnskap/
```

Holger

---

### Post by asai on 2017-11-30
> **Holger_Gehrke said:**
> Check the permissions of the directory in the file system. Apache has to be able to read the directory and change to it. AFAIK apache runs as user:group www-data:www-data, so your best bet is to change the group of the directory to that and allow read and execute for the group:
```
sudo chgrp www-data /home/terje/Dropbox/server_backup/documents/Regnskap/
chmod g+rx-w /home/terje/Dropbox/server_backup/documents/Regnskap/
```

Holger

Thanks for your reply, but this is not the problem.
I think it has to be something with the apache configuration. If I put a index.html file in the folder, the file is shown.
So, is there any way to override the use of index files for spesific folders?
The directory listing is not wished on the root folder of my web server...

---

### Post by Holger_Gehrke on 2017-11-30
If I make the directories you use in my home directory, add your configuration to my apache2.conf and change it to use my username instead of 'terje', it works. I tried what would happen if the autoindex-module was disabled ('sudo a2dismod autoindex'), but that gives 'Not found', not 'Forbidden'. The file permissions are out, if you can access files by naming them in the address or naming them 'index.html'. You could check whether there's a '.htaccess' file in there that contains 'options -indexes', that's the way i could reproduce the behaviour you describe.

Holger

---

### Post by asai on 2017-11-30
> **Holger_Gehrke said:**
> If I make the directories you use in my home directory, add your configuration to my apache2.conf and change it to use my username instead of 'terje', it works. I tried what would happen if the autoindex-module was disabled ('sudo a2dismod autoindex'), but that gives 'Not found', not 'Forbidden'. The file permissions are out, if you can access files by naming them in the address or naming them 'index.html'. You could check whether there's a '.htaccess' file in there that contains 'options -indexes', that's the way i could reproduce the behaviour you describe.

Holger

Thanks, I think we are on to something now...
I have a .htaccess file in the root folder for the server, but not in this specific folder.
The .htaccess file has this line:
```
# Don't show directory listings for URLs which map to a directory.
Options -Indexes
```

Is this .htaccess file overriding everthing?
How should the .htaccess file look like and should I have a special one in the specific folder to still have security on the root folder?

---

### Post by SeijiSensei on 2017-11-30
If you control the server, you should avoid .htaccess files.  Put any directives that would go in .htaccess into the appropriate <Directory> stanza in the configuration file.

.htaccess is a kludge designed to let hosting providers give their clients some control over their sites.  If you control everything, don't use .htaccess.

---

### Post by Holger_Gehrke on 2017-11-30
Quoting the apache documentation (emphasis mine):
> .htaccess files (or "distributed configuration files")     provide a way to make configuration changes on a per-directory basis. A     file, containing one or more configuration directives, is placed in a     particular document directory, and the directives apply to that     directory, **and all subdirectories** thereof.
Since you have complete control over this server, the first sentence of this part of the docs also applies:
> You should avoid using .htaccess files completely if you have access to     httpd main server config file. Using .htaccess files slows down your Apache http server.     Any directive that you can include in a .htaccess file is better set in a Directory block, as it will have the same effect with better performance.
So get rid of those .htaccess-files and put the options either in apache.conf or (better & cleaner, imho) in configurations in '/etc/apache2/sites-available/'.
If you can't - or don't want to - get rid of the .htaccess, you could put another .htaccess in /home/terje/Dropbox/server_backup/documents/Regnskap/ with "Options Indexes" in it.

Holger

---

### Post by asai on 2017-12-01
A pretty simple solution, not very elegant, but it works.
Made a folder under web server root folder.
Then mounted it to the folder /home/terje/Dropbox/server_backup/documents/Regnskap
Works fine. :)

---

