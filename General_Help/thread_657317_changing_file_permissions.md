---
title: "changing file permissions"
date: 2008-01-03
forum: General Help
---

### Post by gleble on 2008-01-03
I am trying to change file permission on a file on my website. I have tried gFTP and Filezilla but neither retain any changes made, Any ideas?

---

### Post by Kzin on 2008-01-03
Use ssh and chmod, assuming you are connecting to a unix/linux web server.

---

### Post by gleble on 2008-01-03
I can't chmod without downloading the file. Is that right?

---

### Post by ~LoKe on 2008-01-03
chmod 775 or whatever you want on the file, then re-upload it.

Example:
```
chmod 775 index.html
```

**EDIT**: Oh, you can't download the file?  Then the above is right, you'd have to ssh into the server and chmod it from there.

---

### Post by gleble on 2008-01-03
How do I upload without using gFTP or Filezilla. They both change the cmod to write. I want read-only

---

### Post by Kzin on 2008-01-03
> **gleble said:**
> How do I upload without using gFTP or Filezilla. They both change the cmod to write. I want read-only

Once u use the ftp program to upload, you ssh to the server, go to where the file is, and ```
chmod a-w fileName
```

---

### Post by Kzin on 2008-01-03
Almost forgot...
You can use the command scp. 
```
man scp
```

---

### Post by Kzin on 2008-01-03
Oh, I just did something here at work...
I needed to get a website up to a windows web server.  There was a shared folder on there, so I went to Places >> Connect to server.  I put in my credentials and connected (thru a VPN so its already pretty secure, if you are connecting thru the www I would think twice)  I was then just able to "Drag and Drop" and set permissions thru the connect to server dealie.

---

### Post by gleble on 2008-01-04
Still stuck (newbie) trying to ssh and I get this
```
neil@neil-laptop:~$ ssh pigpen@climatecalm.org
ssh: connect to host climatecalm.org port 22: Connection timed out
neil@neil-laptop:~$ ssh pigpen@climatecalm.org -p 21
ssh_exchange_identification: Connection closed by remote host
neil@neil-laptop:~
```
Should I be entering a password. What command? seeing as -p is port

---

### Post by Kzin on 2008-01-04
Hmmm, it doesn't look like ssh is running on the server?  21 is the ftp port, ssh is 22 by default.

Is the server you are trying to connect to yours or managed by somebody else?  Do you have access to it otherwise, or just ftp up to this point?  Is it a linux server?

---

### Post by gleble on 2008-01-04
The website is climatecalm.org . I have administrative permissions
It is hosted by Dataflame   Only ftp access I think it's windows, 
should I ask them to change it to Linux?

---

### Post by Kzin on 2008-01-07
> **gleble said:**
> The website is climatecalm.org . I have administrative permissions
It is hosted by Dataflame   Only ftp access I think it's windows, 
should I ask them to change it to Linux?

If this is the case, then any of the tips we gave you so far are for naught, as they are all linux commands.

That being said, I would skip that step and use the cPanel provided by your host.  
[http://www.dataflame.co.uk/cpanel_tutorials_xskin_enduser/cpanel_xskin2_filemanager.htm](http://www.dataflame.co.uk/cpanel_tutorials_xskin_enduser/cpanel_xskin2_filemanager.htm)
It covers file permissions.

---

### Post by Kzin on 2008-01-07
Oops,
That was the Linux file manager,
Here is the windows tutorial.  I watched it and it shows permissions.
[http://www.dataflame.co.uk/tutorials/PSA7.x/EU/plesk7_eu_filemanager.htm](http://www.dataflame.co.uk/tutorials/PSA7.x/EU/plesk7_eu_filemanager.htm)

---

### Post by Kzin on 2008-01-14
Did this work?

---

