---
title: "apache2 virtual hosts"
date: 2004-12-13
forum: General Help
---

### Post by MatthewMetzger on 2004-12-13
Hello,

I'm at my wit's end trying to figure out how virtual hosts work in the apache2 installation (installed via apt-get - universe I believe). I have found no good tutorials or examples on how the "sites-available" and "sites-enabled" folders work. I've tried messing around with it, but all my efforts have not resulted in the ability to have several development virtual hosts.

Can anyone help me with this or point me in the right direction. I tried the apache documentation and there was no mention or examples of how to use the "sites-enabled" folder. I know that I'm supposed to symbolic link files from "sites-available" to "sites-enabled", but what should the config code look like in each of those files. I'm assuming there's supposed to be a file for each virtual host. Please let me know if I'm wrong.

Thanks in advance for any help you may be able to give me.

MatthewMetzger

---

### Post by machiner on 2004-12-14
Have you tried webmin. It's a great tool - I still use the command line for mysql, but for apache webmin makes things really easy and quick.

-------------
machiner

---

### Post by MatthewMetzger on 2004-12-14
I did try webmin, but it seems to be built for apache 1.3 (at least the webmin downloadable through apt-get) and it is another layer that I don't really need. I just want to understand how the configs work (which I do for the most part). XAMPP works perfectly for me with all of the virtual hosts stated at the bottom of the httpd.conf file. I've switched back to XAMPP because the default ubuntu install made it near impossible for me to get virtual hosts running correctly.

---

### Post by machiner on 2004-12-14
I had no such problems with apache2 and webmin...but I downloaded and compiled webmin-1.170 instead of using the one from the repository.

WHen I first started using it, I had to go find all the file locations that webmin wanted -- you know, in the module configuration page for setting up apache....

The only real difference btwn 1.3 and 2, as far as locations for webmin is a "2"...example:

/etc/apache
  or
/etc/apache2

Webmin is really great -- too bad you had a problem. Maybe some other time.

Good luck doing it the hard way.

----------------
machiner

---

