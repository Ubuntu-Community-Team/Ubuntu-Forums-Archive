---
title: "phpmyadmin package does not install under /var/www"
date: 2007-10-25
forum: General Help
---

### Post by acambre on 2007-10-25
When I install phpmyadmin using **apt-get install phpmyadmin**, it appears to put it everywhere *except* **/var/www** according to **find**. The package wasn't even nice enough to give me a symbolic link.

Where do I find instructions on the "proper" way of using phpmyadmin through the apt package? Do I just need to forget about using the apt package and install from source? (Yeah, I know, it's not hard, but I like brainless installs. :))

---

### Post by mannih2001 on 2007-10-26
The phpmyadmin package install the files to /usr/share/phpmyadmin.

But it also creates a symlink in /etc/apache2/conf.d and restarts apache so that you should be able to go to localhost/phpyadmin immediately.

At least that all happens on my system when I install the package with Synaptic and with the default /etc/apache2/apache2.conf.

So either you changed your apache2.conf so that it no longer includes files in conf.d or apt-get install does something a little different than synaptic.

---

### Post by mannih2001 on 2007-10-26
> **mannih2001 said:**
> ... or apt-get install does something a little different than synaptic.

Indeed. I just tried it and although "apt-get intall phpmyadmin" asks which server it should configure, it does not create that symlink.

All you need to do is create a symlink in /etc/apache2/conf.d/ to /etc/phpmyadmin/apache.conf.

---

### Post by acambre on 2007-10-26
> **mannih2001 said:**
> Indeed. I just tried it and although "apt-get intall phpmyadmin" asks which server it should configure, it does not create that symlink.

All you need to do is create a symlink in /etc/apache2/conf.d/ to /etc/phpmyadmin/apache.conf.

Thanks. Shouldn't that have been set up automatically? Is that a package bug? If so, where is it reported?

---

### Post by mistervino on 2007-10-29
I've been experiencing the same problem.  I got it fixed, though!

The only thing that's missing is the symbolic link to the phpMyAdmin directory.

Run the following command and you'll have a folder called "phpmyadmin" in your localhost.

```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

Now you can access phpMyAdmin at [http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/")

Hope that helps!

---

### Post by acambre on 2007-10-29
> **mistervino said:**
> I've been experiencing the same problem.  I got it fixed, though!

The only thing that's missing is the symbolic link to the phpMyAdmin directory.

Run the following command and you'll have a folder called "phpmyadmin" in your localhost.

```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

Now you can access phpMyAdmin at [http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/")

Hope that helps!

Yup, that's basically what I did. Where can we report this apparent bug in the package?

---

### Post by mannih2001 on 2007-11-01
I just tried this again (using aptitude) and it seems that the user (i.e. me) was the problem. The text-interface asked me which web server I wanted to configure and I guess that I simply hit return when the apache2 entry was highlighted the last time I tried this. However, that's not enough. You have to explicitly select apache2 by hitting space before hitting return. Duh.

The same goes for apt-get.

---

### Post by ruibernardo on 2007-11-01
You don't need any link to /var/www/. You can remove that link try:

[_http://localhost/phpmyadmin_]("http://localhost/phpmyadmin")

It will work. 

The phpmyadmin alias in apache is set in /etc/phpmyadmin/apache.conf and this one is linked to /etc/apache2/conf.d/phpmyadmin.conf, so there is no need to add a link to /var/www/, unless you want it to be clearly visible to others.

---

### Post by mahousaru on 2007-11-02
> **epimeteo said:**
> You don't need any link to /var/www/. You can remove that link try:

[_http://localhost/phpmyadmin_]("http://localhost/phpmyadmin")

It will work. 

The phpmyadmin alias in apache is set in /etc/phpmyadmin/apache.conf and this one is linked to /etc/apache2/conf.d/phpmyadmin.conf, so there is no need to add a link to /var/www/, unless you want it to be clearly visible to others.

Also if you have multiple users on your system you should avoid allowing following links.  Using the alias statement as epimeteo has stated followed up by a directory one is the standard course of actions.

If you want to be really secure and access the site via https and restrict it to only specific addresses then something on the lines of:

Remove the symlink to the php file that I believe exists in /etc/apache2/conf.d it should point to a file that looks like:

```

    <Directory /usr/share/phpmyadmin>                                                                                        
            Options Indexes FollowSymLinks                                                                                   
            DirectoryIndex index.php                                                                                         
                                                                                      
                                                                                                                             
            # Authorize for setup                                                                                            
            <Files setup.php>                                                                                                
                # For Apache 1.3 and 2.0                                                                                     
                <IfModule mod_auth.c>                                                                                        
                    AuthType Basic                                                                                           
                    AuthName "phpMyAdmin Setup"                                                                              
                    AuthUserFile /etc/phpmyadmin/htpasswd.setup                                                              
                </IfModule>                                                                                                  
                # For Apache 2.2                                   


```

Copy the contents of the file and add to your ssl definitions that with the added alias and the following lines marked in red

```

    
    Alias /phpmyadmin /usr/share/phpmyadmin

     <Directory /usr/share/phpmyadmin>                                                                                        
            Options Indexes FollowSymLinks                                                                                   
            DirectoryIndex index.php                                                                                         
            [COLOR="Red"]Order deny,allow                                                                                                 
            Deny from all                                                                                                    
            Allow from 127.0.0.1                                                                                             
            Allow from 10.0.0.0/24  [/COLOR]                                                                                         
                                                                                                                             
            # Authorize for setup                                                                                            
            <Files setup.php>                                                                                                
                # For Apache 1.3 and 2.0                                                                                     
                <IfModule mod_auth.c>                                                                                        
                    AuthType Basic                                                                                           
                    AuthName "phpMyAdmin Setup"                                                                              
                    AuthUserFile /etc/phpmyadmin/htpasswd.setup                                                              
                </IfModule>                                                                                                  
                # For Apache 2.2                                   

```

---

### Post by enixon on 2007-12-20
After Installing phpmyadmin through synaptic an through the terminal, it still wasn't linked to my www folder. mistervino 's fix took care of it completely. Thanks for the info.

---

### Post by ruibernardo on 2007-12-20
Hi enixon,

what ubuntu release are you using? I ask this because the OP of this thread is using **7.10 Gutsy**. In this release the phpmyadmin isn't suppose to create that symlink (read the thread about it).

From the [phpmyadmin debian changelog for Gutsy]("http://changelogs.ubuntu.com/changelogs/pool/universe/p/phpmyadmin/phpmyadmin_2.10.3-1ubuntu0.1/changelog"):
> phpmyadmin (4:2.10.1-1) unstable; urgency=high

  * New upstream release.
    - Security fix: PMASA-2007-4: Cross Site Scripting.
  * **Warn about obsolete /var/www/phpmyadmin symlink**.
  * Install translators.html as documentation for proper crediting.

 -- Thijs Kinkhorst <thijs@debian.org>  Thu, 26 Apr 2007 11:17:13 +0200In older releases this might not apply.

---

### Post by pannerrammer on 2007-12-28
> **mannih2001 said:**
> I just tried this again (using aptitude) and it seems that the user (i.e. me) was the problem. The text-interface asked me which web server I wanted to configure and I guess that I simply hit return when the apache2 entry was highlighted the last time I tried this. However, that's not enough. You have to explicitly select apache2 by hitting space before hitting return. Duh.

The same goes for apt-get.

Spot on. Had same problem with phpmyadmin and Gutsy.  ie [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) failed to find page.

I removed phpmyadmin with 
```
sudo apt-get remove phpmyadmin
```then installed it again with
```
sudo apt-get install phpmyadmin
```This time I pressed space to select the apache2 option... and it now works. 

This solution has the benefit of brevity :)

---

### Post by Rick Z on 2008-02-13
Hi Everyone,

I probably should post this into another thread, but I thought I ask here before first...

I am able to install phpmyadmin using apt-get install phpmyadmin.  Everything works fine, but the SSL.

How do I enable the SSL so that all the transaction goes through https:// instead of http://

The server I setup is running ssl as far as I know.  I was searching for the doc how to change within the phpmyadmin, but I couldn't find the files that needs to change the $cfg['Servers'][$i]['ssl'] boolean and $cfg['ForceSSL'] boolean.  According to [http://www.phpmyadmin.net/documentation/#setup](http://www.phpmyadmin.net/documentation/#setup) , I should be able to look into config.inc.php and made the change.  I am wondering if apt-get install may move the config.inc.php into different directory.

Please help.

---

