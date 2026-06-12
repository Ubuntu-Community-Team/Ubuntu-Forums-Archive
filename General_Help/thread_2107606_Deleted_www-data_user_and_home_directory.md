---
title: "Deleted www-data user and home directory"
date: 2013-01-22
forum: General Help
---

### Post by SASDOE on 2013-01-22
Ok, first off, I know this is probably the noobiest problem you have ever heard of, I get it ! I'm only two weeks into using ubuntu 12.04 lts, i want it to be a nice home server (never typed a command line before that day). All ready got plex and nfs sharing working nicely at home, but now i want to acces my files from a distance. There's for context.

Stupidly i had owncloud working but deleted a file and broke it, so I tried to reinstall it exactly as i had the first time, to no avail. I was all ready really frustrated which could explain what follows : thinkg i had to delete all files and every thing related to owncloud to reinstall it, and never having heard of the www-data user, i though he had been created during the installation, so i went on and promptly deleted him and his home directory and all the related files.

Obviously now i get a maintenance notice whenever i enter the server's ip address, when i used to get the "it works" message, and (ip)/owncloud gives me a 404.

My question is, how do i fix this, other than reinstalling ubuntu that is ?

Thank you for reading and hopefully helping me out !

---

### Post by SeijiSensei on 2013-01-22
Run "sudo nano /etc/passwd" to edit the password file as root and add this line:

```
www-data:x:33:33:www-data:/var/www:/bin/sh
```

Now edit /etc/group by the same method and add:

```
www-data:x:33:
```

Finally use these to recreate the /var/www directory:

```

sudo mkdir /var/www
sudo chown www-data:www-data /var/www
sudo chmod 755 /var/www

```

That should replace everything you removed.  If it still isn't working, post the error, particularly any errors in /var/log/apache2/error.log, and we'll see what we can do.

I'm afraid any files you had in /var/www are gone.  You'll have to rebuild the web site.  For testing, let's just create a little index.html file like this:

```
sudo echo '<h3>Hooray!</h3>' > /var/www/index.html
```

---

### Post by SASDOE on 2013-01-22
You Sir are AMAZING ! Thank you for the unbelievably prompt and correct reply. Both the server and owncloud are back. Is there any sort of "thank button" ?

Not close to closing any account here, maybe with time I'll be able to help as well (I'd sure love to!)

---

### Post by SeijiSensei on 2013-01-22
Glad I could help!

---

