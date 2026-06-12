---
title: "apache configuartion.. almost there, but not quite.. access issue"
date: 2006-11-21
forum: General Help
---

### Post by a.d.gardiner on 2006-11-21
hey guys,

sounds like a silly quesiton, I have just installed apache2, mysql and php4. the apache server is running (or so i believe) but im struggling to understand the manuals on how to create a folder to dump my site in.

when i go to /var/www/ i don't seem to have the permissions to create a folder etc. I know its dumb, but im confused.

The server is going to be used to run a phpbb over my local network at work, we are going to use it to leave eachother notes and things.

Im running xubuntu 6.06 if that helps?

can anybody help?

alex :)

---

### Post by adwait on 2006-11-21
You need to use sudo to write to the /var/www folder. eg:
```
sudo vi /var/www/whatever.html
```

---

### Post by a.d.gardiner on 2006-11-24
Sorted I couldn't access the folder so I just changed its permissions. Probably not the most secure way, but I can use it now.

---

### Post by dumbbeatnix on 2006-11-28
Uncomment the lines in /etc/apache2/apache2.conf that have to do with public_html

Create a public_html directory in your home folder.  Set its permissions to 744, like this:

chmod 744 public_html

Every file you copy into this directory, perform the above chmod command on it.  Or simply:

chmod 744 public_html/*

Now you should be able to do in your browser:

localhost

and hopefully it will show your new web site.

You can also change DocumentRoot to /home/[user-name]/public_html

I hope this helps :-k 

Cheers
dumbbeatnix

---

### Post by a.d.gardiner on 2006-11-29
:) Cheers, that sorted it! many thanks :)

---

