---
title: "Setting up a Virtual Host with working AllowOverride All"
date: 2014-02-25
forum: General Help
---

### Post by jason58 on 2014-02-25
I've been fighting this for many hours now, and I'm very frustrated. Apache just doesn't make sense to me; I'd greatly appreciate any advice. Please read through what I've written, as I've read through dozens of posts and manuals on the subject, and really need specific advice.


I'm trying to accomplish two goals: First, get "Pretty Links" to work on my local Wordpress instance; second, to set up a local domain for the site.


I have a fresh install of Apache 2.4.6 running, and I'll I've done is enable the rewrite and vhost_alias mods. Nevertheless, here's my apache2.conf: [http://pastebin.com/Vag8N1QA](http://pastebin.com/Vag8N1QA)


For the first goal, I understand I need to have AllowOverride set to All. This, I gather, allows .htaccess files within the subsequent directories to alter the apache config. To try one thing at a time, I'm accessing the site from localhost/var/www/dhae/Wordpress (foregoing the domain). I tried altering the 000-default.conf to oblige this: [http://pastebin.com/PwMGF9F2](http://pastebin.com/PwMGF9F2) -- all I added was the <Directory> section. This didn't work, and neither did changing the AllowOverride to All in the apache2.conf.


I wondered if perhaps I needed something more specific to the directory, so I tried using my second goal to accomplish this. I wrote the dhae.conf: [http://pastebin.com/trwWVFLW](http://pastebin.com/trwWVFLW)


I've also added the following line to my HOSTS file:
127.0.0.1 dhae.dev


This hasn't worked either. I've tried virtual host config stuff as much as I could find, and I'm just not having any luck. What I have came from this site ([http://www.apachelounge.com/viewtopic.php?p=24139](http://www.apachelounge.com/viewtopic.php?p=24139)). I'm really at a loss, and I need this to work (especially my first goal), so I can continue my normal work.

---

### Post by SeijiSensei on 2014-02-25
> **jason58 said:**
> For the first goal, I understand I need to have AllowOverride set to All. This, I gather, allows .htaccess files within the subsequent directories to alter the apache config.
On machines where you have direct access to the configuration files, it's usually better to include any directives that would appear in a .htaccess file in the <Directory> container for the DocumentRoot.

However, you can quickly enable .htaccess by editing this part of your apache2.conf:
```

<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>

```
That determines the default for any directory not specified in a <Directory> container.  Change "None" to "All" and restart Apache.  Now your .htaccess files should be working.

---

### Post by jason58 on 2014-02-27
I figured it out! 


There was absolutely nothing wrong with my configuration.. it was how I was restarting Apache. Oops! 


There's a serious difference between 'service apache2 restart' and 'sudo etc/init.d/apache2 restart'. Apparently only the latter actually prompts apache to re-cache the config files! Needless to say, I made an alias for that.


Thanks!

---

