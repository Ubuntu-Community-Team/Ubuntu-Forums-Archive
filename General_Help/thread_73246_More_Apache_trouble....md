---
title: "More Apache trouble..."
date: 2005-10-08
forum: General Help
---

### Post by XtremeGamer99 on 2005-10-08
For some reason, mod_rewrite.so isn't working. I downloaded Apache2 from a package. Here's what i found in the config file for loading modules:

```
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
```

File in  /etc/apache2/mod-enabled/ directory link to files in /ect/apache2/mods-available/. The files in mods-available/ load modules from /usr/lib/apache2/modules/. I've already verified that mod_rewrite.so is in /usr/lib/apache2/modules/ and I can see that it's loading when I do phpinfo(). 

However, my .htaccess file doesn't work. this is what it looks like:
```
RewriteEngine On
RewriteRule ^cds/?$ cds.php [L]
RewriteRule ^cds/([0-9]+)/?$ cds.php?cd=$1 [L]
RewriteRule ^cds/([0-9]+)/song/([0-9]+)/?$ cds.php?cd=$1&song=$2 [L]
RewriteRule ^cds/artist/([0-9]+)/?$ cds.php?artist=$1 [L]
RewriteRule ^news/?$ news.php [L]
RewriteRule ^news/([0-9]+)/?$ news.php?id=$1 [L]
RewriteRule ^polls/?$ past_polls.php [L]
RewriteRule ^polls/([0-9]+)/?$ results.php?id=$1 [L]
RewriteRule ^scripts/?$ scripts.php [L]
RewriteRule ^login/?$ login.php [L]
Rewriterule ^logout/?$ logoff.php [L]
```

I don't know why it's not working. I don't know if it's the modules fault or the .htaccess fault. My guess is that .htaccess is disabled, but I don't know how to enable it. Any help is greatly appreciated.

---

### Post by DJ_Max on 2005-10-08
A little reading should solve this issue. 
[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)
[http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride)

---

### Post by XtremeGamer99 on 2005-10-08
The only thing I added was this:

```
<Directory "/var/www">
    AllowOverride All
</Directory>
```

It still doesn't seem to work...

---

### Post by DJ_Max on 2005-10-08
hrmm, Apache is fairly large and can be complicated. Are you sure that code works?

Do you have a entry that looks like
```
<Directory />
    Options FollowSymLinks
    AllowOverride All
</Directory>
```

---

### Post by XtremeGamer99 on 2005-10-08
No I do not. Do I need to add it?

---

### Post by XtremeGamer99 on 2005-10-08
Well, wether I need it or not - I added it. Nothing.

---

### Post by XtremeGamer99 on 2005-10-09
v_v bump

---

### Post by XtremeGamer99 on 2005-10-09
Anyone?

---

### Post by XtremeGamer99 on 2005-10-11
'Nother Bump.

---

### Post by DJ_Max on 2005-10-11
This thread must have slipped my mind.

This could be a mod_rewrite issue, or .htaccess issue.

1.)Make sure you have the mods loaded
```

LoadModule rewrite_module modules/mod_rewrite.so
AddModule mod_rewrite.c

```
Now, this is usually the case when you compile from source. But when you use a third-party binary, the packager may have a different way. I'm assuming you don't need the first line, though I may be wrong.

2.) Check the code and make sure it's correct.
3.) Make sure the .htaccess file is in /var/www or whatever the directory your HTML files are int
4.) Try some basic code
```

RewriteEngine On
Redirect / http://ubuntulinux.org

```

Also, look here [http://ubuntuforums.org/showthread.php?t=47669&highlight=.htaccess](http://ubuntuforums.org/showthread.php?t=47669&highlight=.htaccess)

---

### Post by XtremeGamer99 on 2005-10-13
It works now. Thanks so much for that link. It was the stupid defualt file.

EDIT: Nevermind. The Rewrite code you gave works, but now my custom one doesn't.

---

### Post by DJ_Max on 2005-10-13
[QUOTE=XtremeGamer99]It works now. Thanks so much for that link. It was the stupid defualt file.

EDIT: Nevermind. The Rewrite code you gave works, but now my custom one doesn't.[/QUOTE]
Hrmm, I need to get Apache installed. Is that from a open source script, or thats something you whipped up?

---

### Post by XtremeGamer99 on 2005-10-13
My .htaccess file? Something I made.

---

### Post by DJ_Max on 2005-10-13
[QUOTE=XtremeGamer99]My .htaccess file? Something I made.[/QUOTE]
Ok, the reason I asked because it looks like it's a problem with your code. Have you tried some rewrite code you've found on the net?

Note: The Apache 2 mod_rewrite engine is fairly different from the earlier Apache 1.

---

### Post by XtremeGamer99 on 2005-10-13
I doubt it's the code, because before I switched to Linux, I had the Windows version of Apache 2.0.54. The Apache I'm using now is the same version, only I installed it from a package. When I had Windows running as the server, the .htaccess was working perfectly.

I've also looked at the old configuration file, the one when I had Windows as the server. It's almost the same.

---

### Post by DJ_Max on 2005-10-13
Check to make sure the modrewrite is loaded.

```

<IfModule mod_rewrite.c>
Redirect / http://ubuntulinux.org
</IfModule>

```

---

### Post by XtremeGamer99 on 2005-10-13
I put that in the config file. it worked. However it also worked in the .htaccess file.

This doesn't work either;
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^cds/?$ cds.php [L]
RewriteRule ^cds/([0-9]+)/?$ cds.php?cd=$1 [L]
RewriteRule ^cds/([0-9]+)/song/([0-9]+)/?$ cds.php?cd=$1&song=$2 [L]
RewriteRule ^cds/artist/([0-9]+)/?$ cds.php?artist=$1 [L]
RewriteRule ^news/?$ news.php [L]
RewriteRule ^news/([0-9]+)/?$ news.php?id=$1 [L]
RewriteRule ^polls/?$ past_polls.php [L]
RewriteRule ^polls/([0-9]+)/?$ results.php?id=$1 [L]
RewriteRule ^scripts/?$ scripts.php [L]
RewriteRule ^login/?$ login.php [L]
Rewriterule ^logout/?$ logoff.php [L]
</IfModule>
```

Maybe I'm not meant to have Rewrite. v_v

---

### Post by DJ_Max on 2005-10-13
So all the code is working except your code? 

I wish I knew more about Apache (but I no longer use Apache). I'm not sure if the Windows API differs from the Unix API. 

Maybe a google search, or asking in a programming forum, if the only code not working is your custom code.

---

### Post by hpn on 2006-01-02
[QUOTE=DJ_Max]So all the code is working except your code? 

I wish I knew more about Apache (but I no longer use Apache). I'm not sure if the Windows API differs from the Unix API. 

Maybe a google search, or asking in a programming forum, if the only code not working is your custom code.[/QUOTE]

well, I'm having a similar issue here. I'm using the standard .htacces files that are available with drupal, wordpress - and still rewrite isn't working. The phpinfo() shows mod_rewrite as a loaded module.

---

### Post by hpn on 2006-01-03
ok, 

[http://ubuntuforums.org/showthread.php?t=47669](http://ubuntuforums.org/showthread.php?t=47669)

solved the problem for me.

Nothing was wrong with modrewrite. Only that .htaccess wasn't working :P

---

### Post by clauder357 on 2006-05-24
If you have this section in Apache2.conf

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

everything should be OK if  rewrite.load contains 
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

hope this helps

---

