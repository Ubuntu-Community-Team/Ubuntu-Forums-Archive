---
title: "Apache2 and Name-Based Virtual Hosts"
date: 2007-08-20
forum: General Help
---

### Post by lwranger3 on 2007-08-20
I have set up name-based virtual hosts using Ubuntu and Apache2 and have created a simple index.html document for testing purposes located in /home/vsftp/testsite (rather than /var/www etc). I have added testsite to the server's /etc/hosts file. 

It only seems to work if I open a browser on the server and type in 'http://testsite/index.html'.

I have a file in /etc/apache2/sites-available with the name 'testsite' and a symlink to it in /etc/apache2/sites-enabled. This part seems to be working, hence the index.html page loads correctly.

Does anyone know how I configure Ubuntu and Apache2 so that I can access the site from another computer on the local network without a DNS server, and how I configure it so that all I have to type in is 'http://testsite' rather than 'http://testsite/index.html'?

Thanks in advance.

---

### Post by CheShA on 2007-08-20
[I]
Does anyone know how I configure Ubuntu and Apache2 so that I can access the site from another computer on the local network without a DNS server[/I]

Without a dns server? One way is to add an entry to /etc/hosts on each of the client computers you wish to connect from.  These are simply the format 

IPADDRESS HOSTNAME

e.g. 
```

127.0.0.1 localhost
192.168.0.3 testsite
 
```



*how I configure it so that all I have to type in is 'http://testsite' rather than 'http://testsite/index.html'?*

You use the [DirectoryIndex Apache directive]("http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex") 

e.g. 
```
DirectoryIndex index.html
```

---

### Post by lwranger3 on 2007-08-21
Thank you for the advice. Much appreciated.

I made the changes to the hosts file as suggested and it works. Added the entry to the hosts file on both the server and the Windows client I was using to browse to the site (in the latter case, the hosts file is in C:\windows\system32\drivers\etc).

---

