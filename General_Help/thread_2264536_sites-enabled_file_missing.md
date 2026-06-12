---
title: "sites-enabled file missing"
date: 2015-02-08
forum: General Help
---

### Post by musicweb on 2015-02-08
Recently set up a new server with 14.04.....
Installed Webmin Debian package to manage the server.

When creating a new virtual server, it does not show up online.
I always get the default Ubuntu page....

It seems webmin has created it's own virtual hosts file, and I can't find
the sites-enabled file. Tried a2ensite <mysite> but it says the site doesn't exist.
Probably because the sites-enabled file is gone.

The sites-available file is there.

Is it because I'm using Webmin to create virtual servers?
Is there a better way to do this other than webmin?

---

### Post by TheFu on 2015-02-08
Yes, it is better to use the CLI, so you have complete control AND complete understanding of how it works.
There is no *sites-enabled* file. That is a directory.

---

### Post by musicweb on 2015-02-08
so I should delete the server I created in webmin and use the cli to create one?

---

### Post by TheFu on 2015-02-08
webmin just creates files like you'd do manually in the CLI and restarts the services.  It is a crutch, IMHO.  Generally, it is harder to setup webmin securely than someone new can manage.  I think the real purpose is for an expert to setup webmin so it can be used by people with much less expertise.

BTW, when I started learning Linux, I tried to get webmin running - all the old guys laughed and said I should just learn how to do it the "right way."  That pissed me off, but looking back, I think they were correct.  Never got webmin running and by the time I knew enough to do that, had already learned why it isn't the smartest thing for everyone to use it.  Sure, there are situations where it makes perfect sense, but that's when there is an expert monitoring the systems who doesn't have time to help setup everything for junior admins.

IMHO.

BTW, if you want help - it would be important to say which web server and the version.  Assume "virtual server" isn't about virtual machines, of course. A *virtual server* can have multiple meanings.

---

### Post by musicweb on 2015-02-08
I was using webmin on our old server running Gentoo without problems, but from what I've read Ubuntu uses a different setup for virtual servers. That may be my problem. I'll try the CLI approach and posty back here with results.

---

### Post by TheFu on 2015-02-08
> **musicweb said:**
> I was using webmin on our old server running Gentoo without problems, but from what I've read Ubuntu uses a different setup for virtual servers. That may be my problem. I'll try the CLI approach and posty back here with results.

Don't think that is true.  apache is apache.  Sure, some of the directories may default to different locations, but that should be easy to see and fix, if it is even needed.  Did you check the apache error log?

Did you look for ubuntu webmin install instructions?  google found this: [http://ubuntuhandbook.org/index.php/2013/12/install-webmin-official-repository-ubuntu/](http://ubuntuhandbook.org/index.php/2013/12/install-webmin-official-repository-ubuntu/)  Instructions seem clear.

Or is the person who setup webmin on gentoo available?

---

### Post by musicweb on 2015-02-08
I used the webmin instructions to install it using wget, and getting the deb version from the webmin site. 
I'll uninstall webmin and use the repository approach. Still a lot to learn....

---

### Post by TheFu on 2015-02-08
General order of install preference:
1) official ubuntu repo - modified to fit into the Ubuntu-way of doing things.
2) official PPA from program dev team - choose Ubuntu version, if available
3) unofficial PPA from "trusted source" - be careful with this. Reputation matters HUGELY.
4) .deb file - be VERY CAREFUL doing this - it can and eventually will - breaks APT dependencies in a few months. Soon the system won't patch at all.
5) Source

We all have a lot to learn. I've been doing Linux over 20 yrs now. Lots more to learn for me.

---

### Post by dragonfly41 on 2015-02-08
> ... all the old guys laughed and said I should just learn how to do it the "right way." 

I would not give up on using webmin .. I use webmin 1.730 (from Ubuntu Software Centre). In fact 
I'm experimenting further by building a webmin module to act as a repository/db for the countless 
 tips,  commands and configurations I find in reading this forum and elsewhere.

I found that in the early days of learning Ubuntu commands  CLI companion was a useful tool .. 
but my approach now is to use webmin as an underlying engine / API to allow different batches
command sequences to be run .. both on desktop and headless server(s) in the cloud.

i.e. a tool to automate the running of a sequence of commands and/or bash scripts
after a clean install of Ubuntu (as distinct from loading a cloned image).
See Webmin > Others > Custom Commands as an example.

One advantage of webmin is that it can be used as GUI on a headless server without 
need for SSH session from client.

Now to virtualhosts ...

If you navigate to Webmin > Servers > Apache Webserver > Global Configuration

and open "Edit Config Files"

there is a button "Edit Directives in File" and to the right a drop down menu showing all configuration files including those in sites-available directory

after editing any config file there is a Save button.

I would agree that this workflow could be improved further with a check of syntax when editing config files 
and I would add a custom command to check config files after editing.

sudo apache2ctl configtest
sudo service apache2 restart

...

Sure you can do all this just from command line terminal without need for webmin .. but wait until 
you have many virtualhosts to manage and you are adding in other servers such as tomcat7.

There is another server admin package you can try .. Ajenti .. in Ubuntu Software centre.  Java based.

---

### Post by musicweb on 2015-02-08
This is my current sites-available/000-default.conf file:

```
<VirtualHost *:81>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com

    ServerAdmin webmaster@localhost

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
Alias /webmail/ /usr/share/squirrelmail/
DocumentRoot /var/www/html
ServerName localhost

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

<VirtualHost *:81>
DocumentRoot /home/biz/public_html
ScriptAlias /cgi-bin/ /home/biz/public_html/cgi-bin/
ServerAlias www.wm-mw.biz
ServerName wm-mw.biz
</VirtualHost>

```

Apache has been set to run on port 81 while we are setting up the new server.
When I try to bring up wm-mw.biz, I get the default Ubuntu page in /var/www/html, instead of the 
pages in /home/biz/public_html.

Apache was restarted.... same results. I'm missing something.....

We are running a single static IP on this server.

---

### Post by SeijiSensei on 2015-02-08
Where is the 000-default.conf file located?  It should be in /etc/apache2/sites-available/. In /sites-enabled/ you should see a symbolic link that points to the file.
```

/etc/apache2$ ls -l sites-available
total 12
-rw-r--r-- 1 root root 1332 Jan  7  2014 000-default.conf
-rw-r--r-- 1 root root 6437 Jan  7  2014 default-ssl.conf

/etc/apache2$ ls -l sites-enabled
total 0
lrwxrwxrwx 1 root root 35 Aug 17 09:33 000-default.conf -> ../sites-available/000-default.conf

```
When you run "sudo a2ensite 000-default" this link is created, or recreated if /sites-available/000-default.conf points to some other file or link.  What do you see in those directories?  Did you run a2ensite?  Did you restart Apache with "sudo service apache2 restart"?

Have you read the Ubuntu Server Guide section on Apache?  [https://help.ubuntu.com/14.04/serverguide/httpd.html](https://help.ubuntu.com/14.04/serverguide/httpd.html)

Rather than rewriting 000-default.conf, I would create an entirely separate file, say /sites-available/wm-mw.conf, with the configuration for that virtual host. Then use "sudo a2ensite wm-mw" to activate your site and restart Apache.  Restore the original /sites-available/000-default.conf file to handle traffic that doesn't match a virtual host specification.

When you tried to connect to the site on port 81, you were using the URL [http://wm-mw.biz:81/](http://wm-mw.biz:81/), correct?  Do you have a DNS entry or an entry in /etc/hosts that points wm-mw.biz to the correct IP address?

---

### Post by dragonfly41 on 2015-02-08
What do you have in /etc/hosts (if this is localhost server)?

---

### Post by TheFu on 2015-02-08
I'd be very careful about pointing apache at any files in /home too.  Sure, if this is for an individual where the URL is [www.example.com/~user/](www.example.com/~user/) then that is fine, but for a virtual host, those files really need to be outside any HOME directories - mainly for file permissions.

Also - I'd split each virtualhost into a separate file with a leading number for priority and the virtual domain name for clarity.  This is very common and is a "best practice."

BTW, is your apache set to listen on port 81? /etc/apache2/ports.conf has a listen directive to be modified.

---

### Post by musicweb on 2015-02-08
The file is in the proper directory.

```
 a2ensite 000-default
Site 000-default already enabled

```

Not working using wm-mw.biz:81

This is hosts file:

```
127.0.0.1    localhost
127.0.1.1    wmmw

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
192.168.0.104    wmmw
```

wmmw is the host name

---

### Post by SeijiSensei on 2015-02-08
Not according to your Apache configuration:
```

ServerAlias www.wm-mw.biz
ServerName wm-mw.biz

```
These have a hyphen; the entry in /etc/hosts does not.

What does "ping wm-mw.biz" return?  192.168.0.104?  Or "not found?"

The names must all match exactly.

---

### Post by musicweb on 2015-02-08
```
ping wm-mw.biz
64 bytes from wm-mw.biz (192.168.0.104): icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from wm-mw.biz (192.168.0.104): icmp_seq=2 ttl=64 time=0.038 ms
64 bytes from wm-mw.biz (192.168.0.104): icmp_seq=3 ttl=64 time=0.039 ms
```

and so on....

Oh, and I did install apache as part of a LAMP install if it matters....

---

### Post by dragonfly41 on 2015-02-08
Further points to add to your growing checklist ..

[1] In post #10 you refer to "/home/biz/public" and "/home/biz/public[COLOR=#ff0000]**_html**[/COLOR]"
      Which of these paths are correct for DocumentRoot (unless you have now changed them)?

[2] Check permissions of  DocumentRoot folder recursively. 
      Apache2 expects ownership of DocumentRoot and contents below as www-data (not root or biz).

[3] Check version of apache2 in use since virtualhost Directives have changed between apache 2.2 and 2.4.
     You might need to use ... for apache 2.4 ..
        AllowOverride all
        Require all granted

[4] Any scripts placed in /cgi-bin/ folder need to be executable.

[5] Post here your final creation of /etc/apache2/sites-available/wm-mz.conf

---

### Post by musicweb on 2015-02-08
OK.... I can get the site to come up if I move all the files over to /var/www/html/biz/public_html

I would like to be able to put our sites under the /home/~user directory....
Other, I would have many, many changes to makes to our scripts and pages.

What can be done in this case? Is this the AppArmor software doing this?

---

