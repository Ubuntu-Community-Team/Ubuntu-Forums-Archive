---
title: "Adding User Web Access to /var/www"
date: 2013-02-03
forum: General Help
---

### Post by lourendo on 2013-02-03
Hello, I am fairly new to linux but i am managing.  I manage several websites and I have my sites subdivided into directories within my /var/www/ 

I am looking to adding a directory of file to my www directory and having it downloadable to clients once i grant them access by simply typing in IP.IP.IP.IP/file.zip   the browser then prompts for a password and download commences.

I created a group called {file-access}
I was thinking that i chown the file to $user:file-access
then i remembered that apache2 uses {www-data}

what is the easiest way to accomplish this.  

The end result needs to be very simple as my simpleton clients will be need to use this.

Thank you all for your help!
, Louis

---

### Post by omeomi on 2013-02-04
Wouldn't it be much easier to just use [.htaccess]("http://httpd.apache.org/docs/2.2/howto/htaccess.html") for that?

---

### Post by lourendo on 2013-02-04
> **omeomi said:**
> Wouldn't it be much easier to just use [.htaccess]("http://httpd.apache.org/docs/2.2/howto/htaccess.html") for that?

just set up .htaccess.  works great but i cannot seem to set up specific users for specific content.  any suggestions on where I can learn about this?

for example {john} only has access to /var/www/john/junk.zip    and {bob}  has access to /var/ww/bob/stuff.zip as well as /var/www/john/junk.zip

thanks

---

### Post by omeomi on 2013-02-04
I'm not sure what you want exactly. If you want to limit certain users to certain directories you can just put a separate .htaccess file in each of those directories.

If you want to make it more complicated as in your example, you would need something like this:
```

# Restrict outside access
AuthUserFile /path/.htpasswd
AuthGroupFile /dev/null
AuthName "Login"
AuthType Basic

# Restrict access to certain file to certain user
<Files ~ "^john\junk.zip$">
    require john
    require bob
</Files>

<Files ~ "^bob\junk.zip$">
    require bob
</Files>

```

Another option would be to use groups (note that AuthGroupFile is now assigned):
```

# Restrict outside access
AuthUserFile /path/.htpasswd
AuthGroupFile /path/.htgroup 
AuthName "Login"
AuthType Basic

# Restrict access to certain file to certain groups
<Files ~ "^john\junk.zip$">
    require group somepeople
</Files>

<Files ~ "^bob\junk.zip$">
    require group otherpeople
</Files>
```
The AuthGroupFile (.htgroup) would look like this:
```
somepeople: bob john
otherpeople: bob
```

---

### Post by lourendo on 2013-02-04
That is the problem.  in htaccess, when i write `require {user}` i cannot login  when i change it to `require valid-user` it works

---

### Post by omeomi on 2013-02-04
Does this work?

```
# Restrict outside access
AuthUserFile /path/.htpasswd
AuthGroupFile /dev/null
AuthName "Login"
AuthType Basic

<Files "*">
   require valid-user
</Files>

# Restrict access to certain file to certain user
<Files ~ "^john\junk.zip$">
    require john
    require bob
</Files>

<Files ~ "^bob\junk.zip$">
    require bob
</Files>
```

---

### Post by lourendo on 2013-02-04
I figured it out.  

I was reading the documentation and i noticed that group requirements were formatted as 

```
require group {xxxxx}
```

so i decided to try 

```
require user bob
```

i must designate that i am specifying a group or user.  this seems to be lacking in apache documentation.  

Thank you for your help!

---

