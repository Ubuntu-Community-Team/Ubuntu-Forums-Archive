---
title: "Setting up WebDav....Can it be any directory?"
date: 2007-08-26
forum: General Help
---

### Post by JungMin on 2007-08-26
Hi, 

I am trying to set up a WebDav server so I can use it as a .Mac account to sync my files on my MacBook.  I am curious if I can have to shared directory be any directory I want??  

For example instead of this directory, 

```
mkdir /var/www/myWebDAV
chown www-data:www-data /var/www/myWebDAV
```

I want to use a different directory on a storage hard drive I use:
```
 /media/harddrive1/macshare
```

Can I do this???  How do I tell the webdav server this??


Thanks!!

---

### Post by JungMin on 2007-08-27
It doesn't appear so......I tried to do it by changing the directory.  But when I access the server it is showing me /var/www.

Is it possible to change it?  I don't want to store my files here.  It isn't a convenient place.

---

### Post by JungMin on 2007-08-27
I made a link in /var/www to the directory that I want to access via WebDav.  Is this safe??  I can access the folder now, but not sure if its a wise thing to do.

---

### Post by moon2js on 2007-10-29
Does .Mac use WebDAV?

I'm sorry I can't help you, but in case anyone in the know comes along, maybe they could kindly point out a good Ubuntu-compatible howto for setting up WebDAV. I'm thinking I will try to set one up.

---

### Post by moon2js on 2007-10-30
Oh, so I [googled my own answer]("http://www.tnpi.net/wiki/Do_It_Yourself_.Mac") about .Mac and WebDAV. I think that's pretty cool, but I wonder if the new .Mac and/or Leopard changes anything. I really like the idea of homebrewing those features though on a 'buntu box.

I've been sifting through WebDAV and I can't seem to find the info I'm looking for. If anyone in the know can give me some hints or point me somewhere, I'd be thankful:

Is WebDAV a good way to give users access to their own /home/username/public_html directory (aka localhost/~username)? Or is that not really possible (permissions-wise, as I may have read)?

---

