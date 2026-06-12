---
title: "apache DocumentRoot"
date: 2005-04-28
forum: General Help
---

### Post by flightcrank on 2005-04-28
hi all,

first of all ubuntu is the best ! however

im having a bit of trouble with apache. Basicly i installed it fine from the CD via the synaptic package manager, pointed my browser to "http://localhost" and confirmed that the server was operational. 

however i want the server to point to "/var/www/html" directory insted of the default "/var/www" directory, so i edited my apache2.conf file and added

```
DocumentRoot /var/www/html
```

restarted apache by typing

sudo /etc/init.d/apache2 restart

it restarted succesfully yet when i entered "http://localhost" it sill pointed to the "/var/www" directory not the "/var/www/html" directory i specifed ?

any ideas on how i can do this or what i am doing wrong ? and no i didnt include the " "

thanks

---

### Post by heimo on 2005-04-28
Check your /etc/apache2/sites-enabled/ directory. Theres a file with default in its name (or something like that, probably only one file). You should do site spesific configuration to files in this directory.



:) And welcome to Ubuntu!



EDIT: Below is a more correct version of this advice.

---

### Post by shakin on 2005-04-28
You want to edit /etc/apache2/sites-available/default

That is the config for the default web site. Near the top is the document root config. If and when you want to add more vhosts you simply create a copy of 'default' with a new name, then edit the paths as necessary. You can add as many as you want in the sites-available directory and any ones you want to enable are symlinked from the sites-enabled directory. It's a bit awkward at first, but I actually really like this way of doing it now that I'm used to it. It's better than tons of VirtualHost directives in httpd.conf

---

### Post by flightcrank on 2005-04-28
thank you so much, heimo and shakin for a quick reply.

the advice you gave worked ! i havent worked wit virtual hosts before so i was a bit puzzled as to why DocumentRoot didnt work.

but thank you so much for clearing that up for me. not only is unbuntu the best distro ive used, but these forums make it even better !

---

### Post by Spleenie on 2005-06-02
[QUOTE=flightcrank]thank you so much, heimo and shakin for a quick reply.

the advice you gave worked ! i havent worked wit virtual hosts before so i was a bit puzzled as to why DocumentRoot didnt work.

but thank you so much for clearing that up for me. not only is unbuntu the best distro ive used, but these forums make it even better ![/QUOTE]
 Let me also add my thanks to shakin and heimo, just searched the forums for this exact problem

I agree with flightcrank. Ubuntu (and Kubuntu) are great, but places like ubuntuforums.org and  ubuntuguide.org make it superb!

Thanks again!

- Spleenie

---

