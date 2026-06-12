---
title: "error opening Apache2"
date: 2006-10-24
forum: General Help
---

### Post by leveliv on 2006-10-24
here is what I typed in my terminal and also what I got when I typed it: ```
goodwhite@ChrisRoom:~$ sudo apache2
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```
hmm what is that?

---

### Post by ~LoKe on 2006-10-24
Think you've got something else running on port 80.  Is Apache already loaded?

---

### Post by leveliv on 2006-10-24
I'm not sure...I don't really know how to check. I'd like to also check to see what ports are running what? is there a way I can do that?

---

### Post by ~LoKe on 2006-10-24
Not sure about your ports, but you could try...

```
sudo /etc/init.d/apache2 restart
```

---

### Post by leveliv on 2006-10-24
okay, that works fine now I just have to learn how to use apache...thank you

---

### Post by ~LoKe on 2006-10-24
> **leveliv said:**
> okay, that works fine now I just have to learn how to use apache...thank you

You should be able to just stick all your files (index.htm(l)/index.php) in /var/www/ for it to work.  Perhaps you use a different path.

---

### Post by leveliv on 2006-10-24
hmm I will have to check...okay they are all there like they should be, now can I redirect that to say my NTFS mount? so instead of it looking for var/www/ it would look for /media/windows/blah blah blah?

---

### Post by ~LoKe on 2006-10-24
You've have to edit one of the configuration files which I haven't used in a while; I believe you have to great a virtual host.  Ubuntuguide.org has some info on it, if I recall correctly.

---

### Post by leveliv on 2006-10-24
alright I will check that out thanks for your help.

---

### Post by matthewstory on 2006-10-24
the config file in question is /etc/apache2/sites-available/default, you'll need to change the ServerRoot directive to equal the place on the hard drive.  However, you'll need to make sure that www-data has read priveleges on your NTFS mount, or else nothing will work.

---

### Post by matthewstory on 2006-10-24
My bad, it's the DocumentRoot directive, not the ServerRoot directive, ServerRoot is specified in the /etc/apache2/apache2.conf file and specifies the location of the config files (default: /etc/apache2) as opposed to DocumentRoot which is in /etc/apache2/sites-available/default and specifies the root of documents to be served via HTTP.

---

### Post by leveliv on 2006-10-24
ahhh okay thanks lol..

---

### Post by mssever on 2006-10-25
For future reference, you control servers (and services, to use a Windows term) by typing ```
/etc/init.d/servername start
``` using stop or restart instead of start as appropriate. This goes for mysql, as well. Look in the /etc/init.d directory sometime to see what sort of stuff is there.

To find out if a process is running, type ```
ps -ef | grep processname
```For example, ps -ef | grep apache.

---

### Post by harisund on 2006-10-25
> **leveliv said:**
> I'm not sure...I don't really know how to check. I'd like to also check to see what ports are running what? is there a way I can do that?

```
sudo netstat -plantu
```

---

