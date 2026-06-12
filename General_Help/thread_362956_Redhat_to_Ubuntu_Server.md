---
title: "Redhat to Ubuntu Server?"
date: 2007-02-16
forum: General Help
---

### Post by quicksilver1234 on 2007-02-16
Hello all,
Several years ago, I set up a Linux box with a copy of Red Hat to be my web server and mail host. It's been humming a long fine until about 3 months ago, when it was hacked.  Unable to find and close the backdoor, I installed the OS, but it's been hacked again, installing a fake user named spamd and using my email server to send out spam.  Some how he was able to remote login and muck around in my server.  Time to change.

Can anyone tell me, The Ubuntu Server configuration sound like what i want. It's got Linux, Apache, MySQL and PHP.  
Does it also have sendmail and bind for my nameservers and ftp so I can move files in>
I hope it's got sendmail so I can just move over the email files from the redhat environment to the ubuntu environment.
The [http://www.ubuntu.com/server](http://www.ubuntu.com/server) page is really vague on those details. 
I don't use the Linux box for anything else, so I don't think the desktop version is what I want. However, does the server version have a graphic interface or is it command line. I would prefer graphical interface. 
I'm new to the site. Has this been asked and answered repeatedly? If so, can you forward me to the thread or threads?
Thanks.

---

### Post by quicksilver1234 on 2007-02-16
Oh Hey, I said I was new here.  I just found that those Tag links are pretty useful. I clicked on the Red Hat tag. It's lots of messages about red hat conversion.  course I wouldn't have found that unless I posted. Oh well.

---

### Post by WW on 2007-02-16
You should try to figure out how you were hacked before converting.  Are your passwords weak?  Are you using insecure file transfer methods? (I don't know the details, but I have read that plain old ftp is not secure.)  If so, you will probably be as vulnerable with Ubuntu as you were with Redhat.

---

### Post by quicksilver1234 on 2007-02-16
Well, I was at a convention a couple of months back and logged into my web mail account with my personal account with an unsecure wireless network. My personal account has root access. That was stupid user accounting on my part. I was hacked, so I assumed they had got my password from the air. 
With a full install, I assumed any back doors from the password snatch would have been overwritten.  I'm using vsfptd for my ftp program.  I've updated the users so my personal account doesn't have ftp access and my ftp account only has access to to it's home dir. I log in as root and move files around when I need to transfer within the server. 

Now I'm to the point where I think I've got an old application with an exploit the hackers are using for access.  With the access, tt looked like the hacker was able to overwrite the sshd binary. It's time stamp was the same time as the hack changes to passwd and sshd_config.  If Ubuntu is mopre secure, the hackers should be able to do that.

---

