---
title: "Giving my user permissions to write files in directory"
date: 2013-05-18
forum: General Help
---

### Post by Quick99 on 2013-05-18
I have an Apache web server running on my Ubuntu Server installation. I have some html, javascript and php files that I have been working on. I was trying to use scp to transfer the files from my local machine to the /var/www/ dir on the server. But my user on the server does not have permission to write files there. I can't for the life of me figure out the unix file permissions, and I don't want to blindly try stuff that will mess up my Apache installation.

How can I modify the directory permissions so that I can put files into that directory?

Or is there a more efficient way to transfer the files into that directory? How do most people do it?

Thanks.

---

### Post by dave0109 on 2013-05-19
There are many ways to achieve what you want.  For example, you could:
a) Change the permissions and group of /var/www to allow your user to add files.  I don't recommend this though.
b) Change the Apache config to serve files from your home directory on the server.  This requires you to allow the Apache process to read those files, which again can be done by changing permissions.  This is a better way in my opinion as it's much more flexible.  You can also scale it to work for any number of users, unlike option (a).

So in your Apache config, you want to add another Alias and Directory clause, something like...

```

	Alias /Quick99/ /home/Quick99/www/
	<Directory /home/Quick99/www/ >
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

Then, create your www directory, change the permissions to 750 and change the group to be www-data.  Then copy the files that you want to serve into there.

The options above may not be suitable for you, so read up on the various settings within the Apache web pages.

---

