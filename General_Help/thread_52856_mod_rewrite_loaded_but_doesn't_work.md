---
title: "mod rewrite loaded but doesn't work"
date: 2005-07-29
forum: General Help
---

### Post by mephisto56 on 2005-07-29
In my phpinfo I see have mod_rewrite loaded, so I think I did all the correct steps to get it working. However it fails to work (no single mod rewrite rule works). Any ideas?

---

### Post by heimo on 2005-07-29
directive RewriteEngine on?
[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

---

### Post by mephisto56 on 2005-07-29
Yes, my htaccess file even comes from a working setup under windows and an online host that runs linux.

---

### Post by heimo on 2005-07-29
[QUOTE=mephisto56]Yes, my htaccess file even comes from a working setup under windows and an online host that runs linux.[/QUOTE]

Yeah, ok - that one would have been quite obvious. Any chance that AllowOverride (or what it was) is not set to allow .htaccess changes to Rewrite? Have you tried putting the Rewriterules in site spesific config file?

---

### Post by mephisto56 on 2005-07-29
The allowoverride seems only to apply to icons and Directory "/usr/share/apache2/error". There doesn't seem to be any problem there. 

> Have you tried putting the Rewriterules in site spesific config file? 

I'm not sure what you mean here. 
Thanks for your help btw.

---

### Post by heimo on 2005-07-29
You have the Rewriterules in .htaccess file now? You can put them in the file where other configuration is done for the site - typically something like (I can't verify these at the moment) /etc/apache2/sites-enabled/00mysite.conf

Or if you keep the rules in .htaccess - try putting AllowOverride All (or what ever the syntax is) so that it applies to the directory where your .htaccess file is located. Hopefully I make some kind of sense. :)

[http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride]("http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride")

---

### Post by mephisto56 on 2005-07-29
Tnx for the suggestions, but they also don't work.  :???:

---

### Post by heimo on 2005-07-29
You do remember to restart apache after configuration changes? Probably... I really don't have any more ideas. Maybe you should try to do some other changes and see if those take effect.

---

### Post by Burgresso on 2006-08-03
I'm having the same issues with mod_rewrite...no luck. I can't find any refferences to it in my apache2.conf. I just want to make sure its enabled for a framework I'm playing with - any ideas?

---

### Post by martinhej on 2006-08-04
Hi, same problem as stated above....

I have tried everything, I guess and mod_rewrite just ignores all rules defined in .htaccess. For sure the mod is enabled as phpinfo() spits it out and my .htaccess file is from working configuration (debian sarge). Here is also a part example of my apache2.conf dealing with the mode. 

<Directory /home/*/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        Allow from all
        #AllowOverride FileInfo AuthConfig Limit
        #Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

AccessFileName .htaccess

<Files ~ "^\.ht">
        Order allow,deny
        Deny from all
        Satisfy All
</Files>

UseCanonicalName On

Anybody has some ideas? ..Thanks

---

### Post by Slav Erik on 2006-12-04
OK, I'm not trying to imply anything, mostly because I've done it myself, but check your (dot).htaccess file hasn't turned into a (comma),htaccess file. If at anytime you moved the file through windows, (download from server etc) windows won't play with a (dot).htaccess.
It's worth a check.

---

### Post by yeehawjared on 2006-12-15
has anyone got .htaccess files to be recognized by mod_rewrite?  I'm trying to do the exact same thing...

---

### Post by NoWhereMan on 2006-12-16
same here; please I need it :/

EDIT: sudo a2enmod rewrite

bye

---

### Post by yeehawjared on 2006-12-16
After many hours I finally figured out what I was doing wrong:

In your .htaccess file, you need the <IfModdule> tags.   Here's an example:

<IfModule mod_rewrite.c>
RewriteEngine On
</IfModule>

---

### Post by obiyoda on 2007-01-12
I had the same problem. I fixed it by going into /etc/apache2/sites-enabled/ and editing the default file in there 000-default on my system. And changing the variable AllowOverride all Started working for me. Hopes this helps some one else out.

---

### Post by tomgallagher on 2007-02-07
> **obiyoda said:**
> I had the same problem. I fixed it by going into /etc/apache2/sites-enabled/ and editing the default file in there 000-default on my system. And changing the variable AllowOverride all Started working for me. Hopes this helps some one else out.

I can confirm that this works. If you are using .htaccess rules then you need to give them permission to override the default settings. Works fine now, many thanks.

Tom

---

