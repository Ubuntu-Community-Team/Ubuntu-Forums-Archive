---
title: "Simple setting up of a server"
date: 2005-07-26
forum: General Help
---

### Post by kepardue on 2005-07-26
Hello all,

I'd like to setup Ubuntu as a basic server to test out some web-development work on.  I'm used to Windows in this respect, and am not much on command line (thus being drawn to Ubuntu's users-shouldn't-need-command-line philosophy).  I've installed Apache, MySQL, and PHP from apt-get.  Everything seems to be working fine by going to localhost.

What I'm not familiar with, however, is the best way to edit my files on the server.  The server's location is, in /var/www.  However, I can't just copy and paste files there because I don't have write permissions.  How can I write to these otherwise protected directories?

How do you guys do it?

Ken

---

### Post by Gehaktbal on 2005-07-26
ok i can give u a bit of a hard tip but if it works it is briljant.

Use subversion with apache.

Then u can upload your complete webdevelopment to svn and check it out everywhere and when u want to update your webserver u just have to type

svn update in /var/www and it will get al changes from your repositorie. It doesn't matter anymore were u edit those files.

this sounds kinda vague but i dont really know how to tell this better.

---

### Post by Gehaktbal on 2005-07-26
btw? u dont want to use the command line?

are u running a GUI on a server?

---

### Post by kepardue on 2005-07-28
I'm not sure what you're asking?  Not having any prior web-work-on-linux experience I may not know to expect, but for the little bit of web work that I need to do it would seem that everything would work out of the box.  Apache is running on there, and all of my other software is installed.  I just need to know an easy way of copying new fies into the www/var/apache2-default folder so that I can test them before ftping them up to another server.

Is this something that is very difficult to do?

Thanks,
Ken

---

### Post by Psycho275 on 2005-07-28
Hey kepardue,

Open up terminal, and type this:

```
sudo chmod 777 /var/www
```

When prompted for a password, enter the password of the user you're logged in as. It's worthwhile noting that "chmod 777" will give full permissions to everyone, so do not use it on a public server.

Let me know if that works ok for you,
Dave

---

### Post by kepardue on 2005-07-28
Fantastic, this is exactly what I needed.  I completely understand about the public server issue.  This instance is strictly on my laptop while I toy around with my files before uploading them.

Many thanks!
Kenneth

---

### Post by Sam on 2005-07-28
[QUOTE=Psycho275]Hey kepardue,

Open up terminal, and type this:

```
sudo chmod 777 /var/www
```

When prompted for a password, enter the password of the user you're logged in as. It's worthwhile noting that "chmod 777" will give full permissions to everyone, so do not use it on a public server.

Let me know if that works ok for you,
Dave[/QUOTE]
Don't do that !!! It's a security hole ! ('sudo chmod 755 /var/www' to recover that)

Use
```
$ sudo nautilus /var/www
```instead to open nautilus as root (beware of what you do, you can blow up your system !), then copy your files in that directory.

---

### Post by Psycho275 on 2005-07-28
[QUOTE=Sam]Don't do that !!! It's a security hole ! ('sudo chmod 755 /var/www' to recover that)

Use
```
$ sudo nautilus /var/www
```instead to open nautilus as root (beware of what you do, you can blow up your system !), then copy your files in that directory.[/QUOTE]

[QUOTE=kepardue]Fantastic, this is exactly what I needed.  I completely understand about the public server issue.  This instance is strictly on my laptop while I toy around with my files before uploading them.

Many thanks!
Kenneth[/QUOTE]

Kenneth understands, so it doesn't matter too much. To be honest, when it's used on a closed network like that, I think it poses less of a security risk than using the file browser as root.

Dave

P.S. Kenneth, be sure *not* to chmod the files which you copy in as 777; if you do this then upload, anyone can write to them.

---

