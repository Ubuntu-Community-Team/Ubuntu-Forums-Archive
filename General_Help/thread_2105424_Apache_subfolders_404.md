---
title: "Apache subfolders 404"
date: 2013-01-16
forum: General Help
---

### Post by gellpak on 2013-01-16
I have apache up and running well for my root folder and subfolders which I create, but installed owncloud and the subfolder it created 404s even though I can see the folder from the server side.

I don't have any aliases or sites defined in apache2.conf or sites-enabled that speak to that subdirectory.

The directory is owned by www-data:www-data and has permissions drwxr-xr-x.

When I create subdirectories myself they resolve fine.

---

### Post by eenofonn on 2013-01-16
did you do a chown -R www-data:www-data on the owncloud directory?

---

### Post by gellpak on 2013-01-16
> **eenofonn said:**
> did you do a chown -R www-data:www-data on the owncloud directory?

The www-data:www-data ownership comes from the owncloud installer, I assume. I didn't do that. Just ran it- still getting a 404.

---

### Post by eenofonn on 2013-01-16
oh... did you install from the repository?

I just did a fresh install in between those posts on my local server and it's working fine for me but I downloaded the package from their site and extracted it etc. I did manually chown the directory myself but forgot to look at the ownership before I did so

---

### Post by gellpak on 2013-01-16
I originally installed from the repot (apt-get install owncloud) but had issues and reading the forums it was mentioned that the repo version was old/broke somehow, so I used their installer from the site.

Had it running fine when I installed it from a subdirectory (I put it in /cloud, but then ended up with a url of [http://[server]/cloud/owncloud](http://[server]/cloud/owncloud)). I think the install is fine, there's just a funky redirect happening that goes nowhere, and I can't track down what's causing it.

---

### Post by eenofonn on 2013-01-16
are you by chance still using the same sql db?

---

### Post by gellpak on 2013-01-16
> **eenofonn said:**
> are you by chance still using the same sql db?

Nope, I dropped the database after the last install, and haven't gotten to a point in the install this time where it asks for it. It tells me it's installed then loads the next screen (the config screen if I remember right) and it hits the 404.

When I uninstalled last time I deleted the owncloud dir in the web root, as well as dropping the database in mysql. Is there another location that I should clear out as well to make sure I'm doing a completely clean install?

---

### Post by eenofonn on 2013-01-16
what about the same username?

---

### Post by gellpak on 2013-01-16
> **eenofonn said:**
> what about the same username?

I don't get far enough for it to ask for any information. Step one verifies the server environment, step 2 copies files I believe, step 3 is a success message, then it loads /owncloud to finish the setup and that directory doesn't like me.

---

### Post by eenofonn on 2013-01-16
ok lets have a look at the instructions you're using. :)

  I asked about the username because I had a problem trying to install it on a different system where I installed 4.0.7 and had to remove that to install 4.5 the install process creates a db for the user as well and I had to remember to drop that otherwise the install process didn't work for me.

---

### Post by gellpak on 2013-01-16
> **eenofonn said:**
> ok lets have a look at the instructions you're using. :)

  I asked about the username because I had a problem trying to install it on a different system where I installed 4.0.7 and had to remove that to install 4.5 the install process creates a db for the user as well and I had to remember to drop that otherwise the install process didn't work for me.

Instructions are literally just a part of their installer file: [http://owncloud.org/support/install/](http://owncloud.org/support/install/) (under 'try the web installer'. I just copy that to my webroot, chmod it, and hit it from the web side.

---

### Post by eenofonn on 2013-01-16
so you're trying to use that php script?

Here's the method I've used so far

download the archive with wget to my /tmp folder

tar -xvf owncloud-xx-whatever

mv owncloud /var/www/

setup my virtualhost (which it doesn't sound like you should need to do)

open the url in my browser

enter the like five fields that it asks you for and voila you're logged in

---

### Post by gellpak on 2013-01-16
> **eenofonn said:**
> so you're trying to use that php script?

Here's the method I've used so far

download the archive with wget to my /tmp folder

tar -xvf owncloud-xx-whatever

mv owncloud /var/www/

setup my virtualhost (which it doesn't sound like you should need to do)

open the url in my browser

enter the like five fields that it asks you for and voila you're logged in

Still getting the 404. I'm pretty convinced that it's an apache config issue that's doing something funky to the /owncloud directory rather than an install error. If I put this in a different directory, say, /test, it all works fine.

---

