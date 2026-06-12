---
title: "broken phpmyadmin install"
date: 2007-06-20
forum: General Help
---

### Post by a.d.gardiner on 2007-06-20
Hey all,

I seem to have broken my installation of phpmyadmin :(

I installed it using:
```
sudo apt-get install phpmyadmin
```

A having it working for a while, then playing about with my apache2 setup I somehow managed to bust pypmyadmin.

There used to be a folder (or was it a link?) named phpmyadmin in /var/www/, but it does't appear to be there anymore? I've tried using apt to remove it and reinstalling but I've had no luck.

Any ideas?

---

### Post by az on 2007-06-20
> **a.d.gardiner said:**
> Hey all,

I seem to have broken my installation of phpmyadmin :(

I installed it using:
```
sudo apt-get install phpmyadmin
```

A having it working for a while, then playing about with my apache2 setup I somehow managed to bust pypmyadmin.

There used to be a folder (or was it a link?) named phpmyadmin in /var/www/, but it does't appear to be there anymore? I've tried using apt to remove it and reinstalling but I've had no luck.

Any ideas?

Did you move the document root in your /etc/apache2/sites-available/default?

---

### Post by a.d.gardiner on 2007-06-20
I'm not sure what you mean? (sorry I'm learning still).

I don't believe there is a file which describes a virtual host for phpmyadmin in my sites-available directory.

In actual fact I'm now running my virtual-host config the old way from httpd.conf.

Do I need a virtual host configuration to describe phpmyadmin?

---

### Post by az on 2007-06-20
> **a.d.gardiner said:**
> I'm not sure what you mean? (sorry I'm learning still).

I don't believe there is a file which describes a virtual host for phpmyadmin in my sites-available directory.

In actual fact I'm now running my virtual-host config the old way from httpd.conf.

Do I need a virtual host configuration to describe phpmyadmin?

Apache2 uses a different set of configurations in seperate files, not one monolythic file. I guess you moved your document root and that's why you can't find phpmyadmin anymore.

You don't need a virtualhost for phpmyadmin, but you need to be able to access the directory it's in....  or symlink it.  Is indexing turned on?

---

### Post by a.d.gardiner on 2007-06-20
Okay after having a poke around I found phpmyadmin installed in /usr/share/ .

It must have been symlinked to here before - I just didn't know at the time - I've moved the whole thing over to  /var/www/ and its works!

I take it there is no real reason why moving the whole thing like I've done would be less secure than having it sitting somewhere else but symlinked?

---

### Post by az on 2007-06-20
> **a.d.gardiner said:**
> Okay after having a poke around I found phpmyadmin installed in /usr/share/ .

It must have been symlinked to here before - I just didn't know at the time - I've moved the whole thing over to  /var/www/ and its works!

I take it there is no real reason why moving the whole thing like I've done would be less secure than having it sitting somewhere else but symlinked?

It depends on the permissions.  If the web server cannot write to that directory, you are good to go.

---

### Post by a.d.gardiner on 2007-06-21
So I just need to set my sites document root permissions to public or something like that?

In the past I've used the 'chmod' command for this, 744 I think? (still really new to linux).

I've just checked and the owner of all directories in my /var/www/ is 'root', which I take it is not good.

---

### Post by neptho on 2007-06-21
The ownership by 'root' is fine, that's standard.

By the way, your missing symlink is to /usr/share/phpmyadmin.

You can fix it like this:

```
%sudo ln -sf /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

### Post by az on 2007-06-21
> **a.d.gardiner said:**
> 
I've just checked and the owner of all directories in my /var/www/ is 'root', which I take it is not good.

Yes, that's fine.  It is not writable by the web server (www-data),  Anything executed by the web server runs as that user, so the fact that it's owned by root is irrelevant.

---

### Post by a.d.gardiner on 2007-06-21
Cheers guys :) Up and running again!

---

