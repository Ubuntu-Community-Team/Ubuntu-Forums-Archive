---
title: "FTP tool for Ubuntu"
date: 2008-07-06
forum: General Help
---

### Post by masoud23 on 2008-07-06
Can some one recommend a good FTP tool for up v down loading file to web server.

Tanks in advance

---

### Post by FrostDust on 2008-07-06
Filezilla is pretty friendly to use.

---

### Post by andrew.46 on 2008-07-06
Hi,

If you are after a gui ftp program the easiest to use would probably be gftp. I have never encountered problems with this program although I know some have reported odd errors and freezes.

The easiest CLI program would be ncftp although a substantial failing of this is lack of support for secure connections.

    Andrew

---

### Post by hal8000 on 2008-07-06
Well Gnome has its very own gFTP program so you can use synaptic or apt-get if you'd like to try it out.

However if youre updating a web site then may I recommend sitecopy.

sudo apt-get install sitecopy

With sitecopy you create a couple of local configuration files, after this uplaoding a web site is pretty easy
sitecopy -uko MYSITE  (where MYSITE) is the location of your local sitecopy config file. The advantage is that sitecopy knows exactly what files have changed and its wasy to keep track of web site changes.
[http://freshmeat.net/projects/sitecopy/](http://freshmeat.net/projects/sitecopy/)

and also  man sitecopy
will help in setting up.

Hope that helps

---

### Post by lswb on 2008-07-06
Do you access the web server with ssh? If so check out the sshfs package or zssh. sshfs in particular is pretty cool, it essentially lets you mount a directory on a remote system as a local directory. Then you can just do regular cp commands to transfer files or even open the directory with nautilus or another file manager and drag & drop your files to the remote system.

The zssh package lets you transfer files from a regular ssh session, you switch to the file transfer mode by using a hotkey. It's really handy for casual file transfer, I always use it for ssh sessions just in case. 

If you still want to use ftp, are you looking at some kind of client with extra features or do you mean to set up a server on your local system? There is a lightweight ftp server from the repositories called vsftpd that is easy to set up.

---

### Post by masoud23 on 2008-07-06
Tanks, I am new in linux, now i have down loaded the Filezella. How do i install it. also the comman i use at Terminal?

---

### Post by fragos on 2008-07-06
As a new user who probably uses Firefox, I recommend the the FireFTP extension. It's very newbie friendly and works well. For a stand alone GUI package, I'd also recommend gFTP.

---

### Post by lamego on 2008-07-06
First you should understand that software on Ubuntu is installed differently from windows, FileZilla is available by going into Applications -> Add/Removed .

For FTP you can also use the nautilus integrated client, from your top bar just use Places -> Connect to server .

---

### Post by AaronMT on 2008-07-06
What's wrong with ?

```
sftp
``` ```
man sftp
```

---

