---
title: "Setting up a File Server"
date: 2006-11-05
forum: General Help
---

### Post by the_french_canadian on 2006-11-05
Hello All

I would like to enable other PC's to access the files on my computer. The client must not have to install any new programs and must have a password prompt to enter my files? any suggestions?

I'm quite new to Ubuntu so step by step help would be appreciated!

---

### Post by mithras86 on 2006-11-05
To share files in a network you can use Samba. If you set up correctly your domain or workgroup, it's really easy to do that. 
Right mouse button on the folder you want to share and choose 'Share folder'.  If you have not shared a folder before (like you did), you can install 2 types of a file server, choose SMB. Ubuntu will install then the smb package.
When it's installed, you can choose to share the folder, and set up a name and description: done!

To set up the right domain or workgroup, you should start the shares-admin and then you can fill in your domain or workgroup. If you changed that property, you should restart samba. Open a terminal and type:
sudo /etc/init.d/samba restart
Type in your password and it's all ready to go!

/edit: 
@Rashid584: the_french_canadian si asking for a *file server*, not a ftp server ;)

---

### Post by Rashid584 on 2006-11-05
I think ftp would be an easier solution

open a terminal and type ```
sudo aptitude update
sudo aptitude install pure-ftpd
```

Follow the prompts, if any, and it should start pure-ftpd. And your done!

Now someone else can connect to your computer via a web browser or an ftp client. I'd recommend creating a seperate account just for ftp users (the installation may even do that for you, not sure)

For someone else to access your files, send them the link:

[ftp://user@xx.xx.xxx.xx/home/path/to/files](ftp://user@xx.xx.xxx.xx/home/path/to/files)

where "user" is replaced with their username, the Xs are replaced with your IP number, and /home/path/to/files is replaces with the path to the files/folder you want to share

Hope that helps

-Rashid

---

### Post by the_french_canadian on 2006-11-05
I followed Rashid584's advice. When i type [ftp://chris@xxx.xx.xxx.xx/home/](ftp://chris@xxx.xx.xxx.xx/home/) it asks for a password (to which i enter my login password) but it then says

530 Not Logged In

HELP??

---

### Post by Rashid584 on 2006-11-05
Hmm...check your log files should be in /var/log (or use ksystemlog)

Try doing it from the command line and tell us what other info you get, if at all

Also, you should try creating a seperate user for ftping, and loggin in with that user (is the user you tried to log in with in /etc/ftpusers ?)

-Rashid

---

