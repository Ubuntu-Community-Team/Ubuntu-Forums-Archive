---
title: "Permissions for program created folders"
date: 2012-11-17
forum: General Help
---

### Post by zetanuxi on 2012-11-17
I'm running sabNZBd on 12.10. I cannot access any of the folders it creates over samba.
How do I get sabNZBd to create it's folders with 777 permissions so I can access them from my windows machine? 
I don't want to have to set permissions for every created folder.

Yes, I am fully aware that 777 permissions are incredible insecure, but that's how I want to run it.

---

### Post by bab1 on 2012-11-17
> **zetanuxi said:**
> I'm running sabNZBd on 12.10. I cannot access any of the folders it creates over samba.
How do I get sabNZBd to create it's folders with 777 permissions so I can access them from my windows machine? 
I don't want to have to set permissions for every created folder.

Yes, I am fully aware that 777 permissions are incredible insecure, but that's how I want to run it.

What does the directory structure that is created by sabNZBd really look like?  Where are the directories and file created?

There is no need to set the permissions at 777 on any data directory.

What is output of the following command when used on the directory that sabNZBd stores the files```
ls -l
```

---

### Post by zetanuxi on 2012-11-18
I've got it set up in a sabNZBd folder. Under it, is /comp and /temp.
When the program is downloading files, it starts in /temp, then unpacks and moves it to /comp when it's done. Other programs handle post-processing from there.

Structure is setup like this:
/media
|----/media
       ____|------/sabNZBd
                 _________|------/comp
                 _________|____|-----/[file folder]
                 _________|_________|-----/[files]
                 _________|------/temp
Output of ls -l:
```
ls -l /media/media/sabNZBd/
total 8
drwxrwxrwx 8 root root 4096 Nov 17 13:45 comp
drwxrwxrwx 8 root root 4096 Nov 17 13:37 temp
```Only thing I can see that might cause this is the folders belong to root, but the folders being created inside belong to user. Those are the ones I can't access.
The samba share requires no login and has guest enabled.

---

### Post by bab1 on 2012-11-18
> **zetanuxi said:**
> I've got it set up in a sabNZBd folder. Under it, is /comp and /temp.
When the program is downloading files, it starts in /temp, then unpacks and moves it to /comp when it's done. Other programs handle post-processing from there.

Structure is setup like this:
/media
|----/media
       ____|------/sabNZBd
                 _________|------/comp
                 _________|____|-----/[file folder]
                 _________|_________|-----/[files]
                 _________|------/temp
Output of ls -l:
```
ls -l /media/media/sabNZBd/
total 8
drwxrwxrwx 8 root root 4096 Nov 17 13:45 comp
drwxrwxrwx 8 root root 4096 Nov 17 13:37 temp
```Only thing I can see that might cause this is the folders belong to root, but the folders being created inside belong to user. Those are the ones I can't access.
The samba share requires no login and has guest enabled.
I need to see the permissions of the files and folders that you are referring to.

The folder eXecute permissions allow the user to descend into (traverse) the subdirectories.  I want to see what the application uses as user on these files and directories.  let's see the permissions on the subdirectories of [COLOR="Red"]**../comp**[/COLOR]```
|----/media
       ____|------/sabNZBd
                 _________|[COLOR="Red"]**------/comp**[/COLOR]
```

Also provide the output of ```
getent group |grep samba
```

I believe in setting up the shared directory with the proper permissions.  This means you will have minimal Samba configuration to do.  What does the Samba share configuration look like?

[COLOR="Blue"]Edit:  I assume that the files in ../temp are okay as they are.  We are only talking about: */media/sabNZBd/comp.  Is that correct?* [/COLOR]

---

### Post by zetanuxi on 2012-11-18
Here's /comp:
```
$ ls -l
total 12
drwx------ 2 roark roark 4096 Nov 18 13:15 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot
drwx------ 2 roark roark 4096 Nov 18 13:23 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot.1
drwx------ 2 roark roark 4096 Nov 18 13:37 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot.2

```These failed, but even the successful downloads have the same permissions and issue.

Here's getent:
```
$ getent group | grep samba
sambashare:x:109:roark

```And here's my smb.conf:
```
[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[Media]
        comment= Media Server
        path = /media/media
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0777

```Would I just need to add ```
security = user
unix password sync = yes
``` to [Global], remove 'guest ok' from the share and just log in? I'll try that real quick.

**Edit:** Okay, it's not exactly how I wanted to have it set up, but it's working now.
I added 'security = user' and 'unix password sync = yes' to [Global], removed 'guest ok = yes' from [Media], installed libpam-smbpasswd then used 'smbpasswd -a roark'.

Know of any way to get this working without a password?

---

### Post by bab1 on 2012-11-18
> **zetanuxi said:**
> Here's /comp:
```
$ ls -l
total 12
drwx------ 2 roark roark 4096 Nov 18 13:15 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot
drwx------ 2 roark roark 4096 Nov 18 13:23 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot.1
drwx------ 2 roark roark 4096 Nov 18 13:37 _FAILED_Last.Resort.S01E07.Custom.DKsubs.720p.HDTV.x264-G.Spot.2

```These failed, but even the successful downloads have the same permissions and issue.

Here's getent:
```
$ getent group | grep samba
sambashare:x:109:roark

```
I assume you are the user roark.  Are you the user roark on all hosts in the network (other computers)?  Can you open these files from the local host? > 
And here's my smb.conf:
```
...
[Media]
        comment= Media Server
        path = /media/media
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0777

```
Is the share ([Media]) where you expect to see the files from /media/sabNZBd/comp?  If so the path is wrong.  It should reflect where the files your sharing are (i.e. /media/sabNZBd/comp).> 
Would I just need to add ```
security = user
unix password sync = yes
``` to [Global], remove 'guest ok' from the share and just log in? I'll try that real quick.
I don't think you will need the create mask either.  

What is the output of this command```
sudo pdbedit -L
```

I'm a little confused as to why you are trying to use guest settings in the first place.  In addition the group and others permissions are unusual.  I assume you have set that in he sabNZBd app somewhere.

---

### Post by zetanuxi on 2012-11-18
> **bab1 said:**
> I assume you are the user roark.  Are you the user  roark on all hosts in the network (other computers)?  Can you open these  files from the local host?
Yes, all the computers that need to access this have the same user name. The files can be manipulated locally with said account.

> **bab1 said:**
> Is the share ([Media]) where you expect to see the files from  /media/sabNZBd/comp?  If so the path is wrong.  It should reflect where  the files your sharing are (i.e. /media/sabNZBd/comp).
The sabNZBd directory is under /media/media, but it's not the only thing in there. /media/media is my LVM and my final folders are under here as well under a different sub-directory. The permissions in there are just fine.

pdbedit -L outouts 'roark:1000:roark'.

I used guest setting initially because I didn't want to make the other end users accounts and all of the content originated from the end users, so I never ran into this problem.

I have sabNZBd set up to run under 'roark' and create files and folders under the same user. I just wasn't able to access them as a guest from the samba share without changing permissions manually.

I think I can live with how it's set up now. Having to log in really isn't that big of an inconvenience and will help keep the rest of the family from changing things. Since I'm accessing it from a unix account now, I'm going to change the permissions to 0755 instead.
Thanks for your help, bab!
Will mark as [Solved].

---

### Post by bab1 on 2012-11-18
> **zetanuxi said:**
> Yes, all the computers that need to access this have the same user name. The files can be manipulated locally with said account.


The sabNZBd directory is under /media/media, but it's not the only thing in there. /media/media is my LVM and my final folders are under here as well under a different sub-directory. The permissions in there are just fine.

pdbedit -L outouts 'roark:1000:roark'.

I used guest setting initially because I didn't want to make the other end users accounts and all of the content originated from the end users, so I never ran into this problem.

I have sabNZBd set up to run under 'roark' and create files and folders under the same user. I just wasn't able to access them as a guest from the samba share without changing permissions manually.

I think I can live with how it's set up now. Having to log in really isn't that big of an inconvenience and will help keep the rest of the family from changing things. Since I'm accessing it from a unix account now, I'm going to change the permissions to 0755 instead.
Thanks for your help, bab!
Will mark as [Solved].

So you are accessing the share from another computer as roark now?

The reason you couldn't access these with the guest account is that there are no permissions for "others".  Without that only roark can access them.

---

### Post by zetanuxi on 2012-11-18
> **bab1 said:**
> So you are accessing the share from another computer as roark now?

The reason you couldn't access these with the guest account is that there are no permissions for "others".  Without that only roark can access them.

I am. I set the security settings to require login using my linux account. So other than having to log in, it's working fine now. :)

---

### Post by bab1 on 2012-11-18
> **zetanuxi said:**
> I am. I set the security settings to require login using my linux account. So other than having to log in, it's working fine now. :)

We have replies that have crossed.  When you had the permissions on the files like this ```
drwx------ 2 roark roark 4096 Nov 18 13:15 
```...and you had guest access. You should not have been able to access these files.  The reason is guest access means that you connect as the user *nobody*.  With the above permissions you exclude everyone but the user *roark* (e.g the permissions are 700).

If you have it working then great!  I'm not sure you understand all the configuration settings available or that Linux permissions can conflict with Samba permissions.  The Linux permissions are always have the final say so.

Once again if you have it running like you want it then its all good.  Of not...

---

