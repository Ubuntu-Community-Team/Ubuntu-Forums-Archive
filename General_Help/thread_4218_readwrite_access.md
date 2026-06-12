---
title: "read/write access"
date: 2004-11-12
forum: General Help
---

### Post by stoop on 2004-11-12
I searched the forums for root/sudo help and could not find any.  If anyone can direct me to an easy walkthrough that would be great.

This is my first install of linux to really try out with any seriousness.  My objective is to setup apache, php, and mysql.

The problem I am having resides in the fact that I can not modify or write over the index.html file located in the apache directory in /var/www.  I do not have the correct rights to do this.  Sadly I do not know what commands to use to copy or edit that html file.

It wont allow me to log in as root (Ive read that this is disabled on purpose)
I cant log in as 'sudo' either.  I can only login with the name that I setup during installation.

Could someone please provide me some commands to type in at a terminal so that I can modify or write over files that are in directories other than my 'home' directory?

Thanks

---

### Post by jdodson on 2004-11-12
there is a selection in some menu in the panel, check like the configuration or system selection(sorry i dont have ubuntu here in front of me) that allows you to open a 'root console'.  select this root console and then type 'passwd'.  you will then be prompted to enter the password twice.  close the root console and you can then 'su' as root and overwrite the .html files for apache.  

i know ubuntu is very sudo, and i do use it, however sometimes, aint nothin to beat root.

---

### Post by jdodson on 2004-11-12
just realized you could also use sudo to copy the files over for instance if you wanted to copy the /home/user/htmlFiles/ directory to /var/www/html then you could type

```
sudo cp /home/usr/htmlFiles/* /var/ww/html
```

---

### Post by stoop on 2004-11-12
Thank you.  I was able to copy the html file I wanted into that directory.

Is this the best way to develop things?  have a 'development' directory in 'user' space (my home directory) then sudo cp it into areas that I wouldnt normally have read/write to?

---

