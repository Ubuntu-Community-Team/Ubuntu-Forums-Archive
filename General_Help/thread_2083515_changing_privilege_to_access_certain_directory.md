---
title: "changing privilege to access certain directory"
date: 2012-11-12
forum: General Help
---

### Post by workaround on 2012-11-12
The root owns www directory, what would be the way to let a user have access to that directory? Do I need to change permissions by "chmod" directive and if I need to take it back use the same process?
Thanks.:popcorn:

---

### Post by pkadeel on 2012-11-13
> **workaround said:**
> The root owns www directory, what would be the way to let a user have access to that directory? Do I need to change permissions by "chmod" directive and if I need to take it back use the same process?
Thanks.:popcorn:
If the machine is used in a single user environment, I don't think doing a chown (not chmod) on www will make any difference on apache's working however it will make editing easy for you.

You can also leave www as it is and setup a virtual host on your prefered location. Infact setting up virtual host is more appropriate if you intend to develop more than one sites.

---

### Post by mastablasta on 2012-11-13
> **workaround said:**
> The root owns www directory, what would be the way to let a user have access to that directory? Do I need to change permissions by "chmod" directive and if I need to take it back use the same process?
Thanks.:popcorn:
 
i think you can change it to belong to group www-data . that will give user the necessary access.
 
and then if necessary add user to the group: [http://www.cyberciti.biz/faq/ubuntu-add-user-to-group-www-data/](http://www.cyberciti.biz/faq/ubuntu-add-user-to-group-www-data/)

---

### Post by Wim Sturkenboom on 2012-11-13
```

sudo chgrp yourprimaryusergroup /var/www
sudo chmod 775 /var/www

```
The first command makes that the group of the file is going to be your primary group. The second command will set the permissions correct so the users in the group have full access.

As an alternative, you can use [setfacl](http://linux.die.net/man/1/setfacl) which allows more fine-grained control.

But the, in my opinion, best solution is to NOT use /var/www. Just put the files for a website in a user's home directory and point the document root to it (for a single site) or use virtual hosts (as mentioned by pkadeel) with document roots somewhere in user's home directories.

---

### Post by workaround on 2012-11-13
Well, to "pkadeel", how would I set up the virtual host? Ubuntu changed the setup for Apache and that changed the environment for virtual hosting, I do not modify any more ```
httpd.conf
``` like used to!?
I got two Apache servers on my machine, the Ubuntu that is running while using the Ubuntu configuration and the old setup Apache that does not want to load PHP due to the conflict with "mod_unixd.so". I would like to remove this one but I am not sure what trouble I might run into again of reconfiguring all to get it to work.
I did consider 775 mode but the root owns the directory and so it does not allow me (the user) to use it without the sudo!?
The only way I see it is to use 777 mode on the www directory(!?), not sure about that.
:confused:

---

### Post by pkadeel on 2012-11-13
> **workaround said:**
> Well, to "pkadeel", how would I set up the virtual host? Ubuntu changed the setup for Apache and that changed the environment for virtual hosting, I do not modify any more ```
httpd.conf
``` like used to!?
I got two Apache servers on my machine, the Ubuntu that is running while using the Ubuntu configuration and the old setup Apache that does not want to load PHP due to the conflict with "mod_unixd.so". I would like to remove this one but I am not sure what trouble I might run into again of reconfiguring all to get it to work.
I did consider 775 mode but the root owns the directory and so it does not allow me (the user) to use it without the sudo!?
The only way I see it is to use 777 mode on the www directory(!?), not sure about that.
:confused:
Creating a virtual host is a very simple and straight forward procedure. You don't have to modify any existing file just an apache restart would be required.

create a new blank file. Name it "your_site_name". Put the following text in it making the changes required.
```

<VirtualHost [COLOR=Red]127.0.0.1[/COLOR]:80>
    ServerName [COLOR=Red]yoursite_domain_name[/COLOR]
    ServerAdmin admin@[COLOR=Red]yoursite_domain_name[/COLOR]
    DocumentRoot [COLOR=Red]/full/path/to/your/site/root[/COLOR]
    <Directory  [COLOR=Red]/full/path/to/your/site/root/[/COLOR]>
        Options Indexes FollowSymLinks
        IndexOptions FancyIndexing
        AllowOverride All
        Order Deny,Allow
        Allow from all
    </Directory>
    DirectoryIndex index.php index.html
#    RewriteLog ${APACHE_LOG_DIR}/[COLOR=Red]sitename[/COLOR]-rewrite.log
#    RewriteLogLevel 5
    ErrorLog ${APACHE_LOG_DIR}/[COLOR=Red]sitename[/COLOR]-error.log
    CustomLog ${APACHE_LOG_DIR}/[COLOR=Red]sitename[/COLOR]-access.log combined
</VirtualHost>

```If the site is being used for development purpose only and is accessed  from localhost then you can use a dummy domain name like "mysite.loc"  and put its entry in /etc/hosts file on a new line.
```

127.0.0.1               mysite.loc

```

Now put this file in /etc/apache2/sites-available folder and enable it. You can also check it for errors before apache2 restart. code is included below.
```

sudo cp /path/to/newfile /etc/apache2/sites-available
sudo a2ensite your_site_name
sudo apache2ctl -S
sudo service apache2 restart

```
As far as changing permissions is concerned, I said earlier that chmod doesn't apply here. what you need is chown (means change the owner of the www folder.)

---

### Post by Lars Noodén on 2012-11-13
The www-data user and group are reserved for privilege separation of the web server's processes.  If you are sharing access to the vhost, then you'll need a group, such as 'webmasters'

```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /full/path/to/your/site/root/ -type d -exec chmod g=rwxs "{}" \;
sudo find /full/path/to/your/site/root/ -type f -exec chmod g=rws "{}" \;

# repeat for each user:
sudo gpasswd --add workaround webmasters

```

---

### Post by workaround on 2012-11-14
I get error while calling: sudo a2ensite mfspace.net
```

ERROR: Site mfspace.net does not exist!
``````
<VirtualHost 127.0.0.1:80>
    ServerName mfspace.net
    ServerAdmin admin@mfspace.net
    DocumentRoot /home/pesh/workspace/public_html
    <Directory  /home/pesh/workspace/public_html/>
        Options Indexes FollowSymLinks
        IndexOptions FancyIndexing
        AllowOverride All
        Order Deny,Allow
        Allow from all
    </Directory>
    DirectoryIndex index.php index.html
#    RewriteLog ${APACHE_LOG_DIR}/mfspace-rewrite.log  // sitename-error.log
#    RewriteLogLevel 5
    ErrorLog ${APACHE_LOG_DIR}/mfspace-error.log
    CustomLog ${APACHE_LOG_DIR}/mfspace-access.log combined
</VirtualHost>

```I did setup the hosts:
```

# 127.0.0.1    localhost
127.0.0.1       mfspace.net
127.0.1.1    one
...

```The directory is created and it has an index.php file.
Also, I changed the path but still don't get the right results.
Thanks much. :confused:

---

### Post by workaround on 2012-11-14
I renamed the file from mfspace to mfspace.net in sites-available and it works BUT it still conflicts with something!?:confused:
This is the output:
```

pesh@one:/etc/apache2/sites-available$ sudo service apache2 reload
 * Reloading web server config                                                  
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


```
Any suggestion why is not reconfiguring?

---

### Post by Wim Sturkenboom on 2012-11-14
That's just a warning. It is reconfigured and should now work.

---

### Post by workaround on 2012-11-14
Actually, IT IS WORKING!
I typed in the new name for the local host and it works!:guitar:
Thank U for your help pkedeel!

---

### Post by pkadeel on 2012-11-14
> **workaround said:**
> I renamed the file from mfspace to mfspace.net in sites-available and it works BUT it still conflicts with something!?:confused:
This is the output:
```

pesh@one:/etc/apache2/sites-available$ sudo service apache2 reload
 * Reloading web server config                                                  
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


```Any suggestion why is not reconfiguring?
First of all congrates. You did it.
Secondly in your /etc/host file you have a line
```
# 127.0.0.1    localhost
```Now you shouldn't comment out the localhost entry in /etc/hosts file. It can cause other problems which you might not be aware of right now so its better to un-comment it. If you choose not to un-comment it then skip the next code block.

And finally if you want to avoid the apache2 warning quoted above do as follows
```

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
sudo service apache2 restart

```

---

