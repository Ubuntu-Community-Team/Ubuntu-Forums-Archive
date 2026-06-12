---
title: "server questions"
date: 2007-11-22
forum: General Help
---

### Post by g35x on 2007-11-22
well I've been looking around this site at the tutorials on how to set up ubuntu / xubuntu servers, and I'm still a bit confused as to how it works.

after you get the server set up, how do you designate which files can be downloaded by people accessing your server? It can't be that users can just download anything on your hard drive, I was wonder If there was a seperate directory or something?

basically what I want to do is set up an ftp server so I can download small files like openoffice documents from my server where ever I am. I want it set up so I can just type something into a web browser and be able to grab those files from my server.

is this possible?

---

### Post by mellowd on 2007-11-22
Yes it is. Once apache is installed then by default anything in your /var/www directory will be your "website" Fell free to put what you want there. You can set up permissions and the like on files you don't want the world to see. You can also setup an ftp server in a similar fashion

---

### Post by Prospero2006 on 2007-11-22
You use samba for turning directories into 'network drives' that can be mapped by other Windows machines. Of course, you can set up ftp or something similar as well.

It's wide open.

---

### Post by g35x on 2007-11-22
is this easy to do without a GUI?

what I was reading said that a GUI for a server was completely unneccesary, so I'm not really understanding how you get files into certaint folders without a GUI...

---

### Post by mellowd on 2007-11-23
it takes a little while to learn the commands but its easy once you know how.

lets say i have my website in a folder in my home dir as follows:

/home/mellowd/new_website

and I want to put it here: 

/var/www


there are a number of ways I could do this, this is one of them:

```
mv /home/mellowd/new_website /var/www
```

---

