---
title: "ProFTPD and directory permissions"
date: 2005-07-07
forum: General Help
---

### Post by epohs on 2005-07-07
I would like to set up anonymous FTP access (read only) to a directory on my ubuntu box.

The way I'm envisioning this working is that FTP is down until I SSH into my machine and run a custom bash script which both innitiates ProFTPD and mounts the specified directory into /home/ftp/.  The script is written and seems to be working, except that the mounted directory retains the owner and groupid of my local user, thus is inaccessible to the anonymous account.

My main question would be, is there any way to mount ext3 and assign the target a different uid and gid than the source directory?

I'm currently using: [COLOR=DarkGreen]mount -o bind,uid=<ftpuid>,gid=<ftpgid> <targetdir> <sourcedir>[/COLOR] to mount the directory, and it works properly, but doesn't change the uid or gid.

Also, according to [this mini how-to](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html) symlinks do not work with ProFTPD's anonymous ftp.


I realize that this might be a backward way of handling things.  My reasoning for doing it this way is that I don't want the directory open all the time, but when it is open I would like myself and a few others to have easy access to the files.  But, I am open to alternative suggestions to accomplishing this.

Thanks for any help you can offer.

---

### Post by frodon on 2005-07-07
Symlinks will not work with the latest version of proftpd for security reasons, indeed it's the best way to make someone go out the directory where you've locked him.
I also use proftpd (not with anonimous access) and mount -o bind xxxx to mount repertories in my /home/FTP directory and I haven't access problems. So if I understand well (or not !) you're problem is that anonimous users can't access the directory you've mounted.
Can you confirm that I understand well your problem and post your proftpd.conf file. I've spent long time reading proftpd documentation so maybe i can help you if it's a configuration problem. Keep in mind that proftpd use the system permissions not  those you set in proftpd.conf.

---

### Post by epohs on 2005-07-07
Yes, you are correct.  The problem is that the folder I wish to mount is owned by my local user, and is not readable by anonymous when it is mounted into my ftp directory.

```
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd               off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

# Uncomment this if you would use quota module:
#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on

# Port 21 is the standard FTP port.
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
#DelayEngine                    off

# A basic anonymous configuration, no upload directories.

 <Anonymous /home/ftp>
   User                         ftp
   Group                        nogroup

   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias                    anonymous ftp

   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser  on ftp
   DirFakeGroup on ftp

   RequireValidShell            off

   # Limit the maximum number of anonymous logins
   MaxClients                   1

   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
   DisplayLogin                 welcome.msg
  DisplayFirstChdir             .message


   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
      DenyAll
     </Limit>
   </Directory>

  # Uncomment this if you're brave.
   # <Directory incoming>
   #   # Umask 022 is a good standard umask to prevent new files and dirs
   #   # (second parm) from being group and world writable.
   #   Umask                            022  022
   #            <Limit READ WRITE>
   #            DenyAll
   #            </Limit>
  #            <Limit STOR>
   #            AllowAll
   #            </Limit>
   # </Directory>

 </Anonymous>
```

---

### Post by frodon on 2005-07-07
Fisrt if you want anonymous access i suggest you to use " User         nobody"  indeed why specify a particular user if you want to allow anonymous access. When you try to connect to your server, do you see the repertory or not ? What are the permissions of your FTP directory in your /home ? and what are the permissions of the mounted directory ? 

My way to mount and use a directory in my /home/FTP is :
1- create a directory : sudo mkdir test_directory
2- sudo chmod 775 test_directory (no write access)
3- I add in the proftpd.conf these lines (in your case in the anonymous field i think) ```
<Directory /home/ftp/test_directory/>
     <Limit WRITE and also all you want>
      DenyAll
     </Limit>
   </Directory>
```
4- I do a : mount -o bind start_repertory /home/ftp/test_directory

that's all i do

---

### Post by epohs on 2005-07-07
Permissions on my FTP directory, and the mounted directory inside of that are as follows:

/home/ftp/ -- drwxr-xr-x   3 ftp   nogroup

/home/ftp/<mounteddir> -- drwxrw-rw-  4 <localuser> users


I believe the steps that I'm following are the same as yours, except that I set the owner of the /home/ftp folder to "ftp", and force anonymous login to use that user.

Yes, currently I see the FTP root when I log in anonymously, and I see the mounted directory, but access to it is denied.

---

### Post by frodon on 2005-07-07
[QUOTE=epohs]I believe the steps that I'm following are the same as yours, except that I set the owner of the /home/ftp folder to "ftp", and force anonymous login to use that user.[/QUOTE]

Well sorry I explain really bad, i also set the owner of the /home/ftp folder to "ftp" by i add a directory field for each repertory present in /home/ftp folder (also because i have different permission for some upload directories). But just for try, add one more directory field in the anonymous field as i do. For me your permissions are good, you would access the directory. They also do that in this exemple : [http://www.proftpd.org/docs/configs/anonymous.conf](http://www.proftpd.org/docs/configs/anonymous.conf).

---

### Post by epohs on 2005-07-07
Thank you for that link, It is helpful.

Although, I tried to add several Limits and none of them seemed to work.  Will attributes assigned in /etc/proftpd.conf take precedence over file permissions?


Here is my "Anonymous" section of proftpd.conf: ```
 <Anonymous /home/ftp>
   User                         ftp
   Group                        nogroup

   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias                    anonymous ftp

   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser  on ftp
   DirFakeGroup on ftp

   RequireValidShell            off

   # Limit the maximum number of anonymous logins
   MaxClients                   1

   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
   DisplayLogin                 welcome.msg
  DisplayFirstChdir             .message

   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
      DenyAll
     </Limit>

     <Limit LOGIN>
      AllowAll
     </Limit>
   </Directory>

   <Directory /home/ftp/<mountdir>/>
     <Limit LOGIN>
      AllowAll
     </Limit>

     <Limit WRITE>
      DenyAll
     </Limit>

     <Limit READ>
      AllowAll
     </Limit>
   </Directory>

  # Uncomment this if you're brave.
   # <Directory incoming>
   #   # Umask 022 is a good standard umask to prevent new files and dirs
   #   # (second parm) from being group and world writable.
   #   Umask                            022  022
   #            <Limit READ WRITE>
   #            DenyAll
   #            </Limit>
  #            <Limit STOR>
   #            AllowAll
   #            </Limit>
   # </Directory>

 </Anonymous>


```

---

### Post by frodon on 2005-07-07
[QUOTE=epohs]Thank you for that link, It is helpful.

Although, I tried to add several Limits and none of them seemed to work.  Will attributes assigned in /etc/proftpd.conf take precedence over file permissions?[/QUOTE]

System permissions overwrite proftpd permissions (It's why i like proftpd), for exemple if you set write access to a directory in proftpd.conf but system permissions are set for no write access the result is no write access.
Be careful I think you syntax is wrong here : <Directory /home/ftp/**<**mountdir**>**/> it would be <Directory /home/ftp/mountdir//>.
I think you can perform a syntax check with the command : ```
proftpd -td5
```
If the syntax of a path is wrong (or the path itself), it will not work.

---

### Post by epohs on 2005-07-07
running [COLOR=Green]sudo proftpd -td5[/COLOR] outputs several lines, but does not give any errors.

I have tried changing the path in [COLOR=Green]<Directory /home/ftp/<mountdir>/>[/COLOR] to several things, such as [COLOR=Green]<Directory <mountdir>>[/COLOR] and [COLOR=Green]<Directory <mountdir>/*>[/COLOR], but nothing seems to help.  I continue to get "550: Permission Denied" errors.


My file permissions seem to be set to allow read/write access by everyone... I'm a little bit stumped here.

:(


If I manually chown /home/ftp/<mountdir> to ftp:nogroup, after I have mounted the source directory into it everything works, but (as expected) it also changes the ownership of the source directory, which is not something I want to do.

---

### Post by frodon on 2005-07-07
ok 550: Permission Denied error signify for me that is a really stupid thing that make it doen't work, i had this error when my directory path was wrong. In your case you must try one by one to change small details like set user to nobody.

I give you here my proftpd.conf : ```
#
AllowForeignAddress off
AllowRetrieveRestart on
AllowOverwrite on
AuthAliasOnly on
UserAlias sauron userftp

ServerName			"ChezFrodon"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 40
TimeoutStalled 10
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# Autoriser l'usage de /etc/ftpusers
UseFtpUsers off

# On autorise les reprises des téléchargements interrompus :
AllowStoreRestart		on


# Port 21 is the standard FTP port.
Port				2014


#Ratios on

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  userftp
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

# Laiser à off sauf si les utilisateurs sont gérés par NIS.
PersistentPasswd		off

# Nombre maximum de clients simultanés
MaxClients 8

# Nombre maximum de clients ayant le même login
MaxClientsPerHost 8

MaxClientsPerUser 8

MaxHostsPerUser 8

# Message d'accueil après une connexion réussie
AccessGrantMsg "attention j'te voit mon salaud !!!!"

ServerIdent                  on       "Tu recherche l anneau ????"

# Default root can be used to put users in a chroot environment.
# As an example if you have a user foo and you want to put foo in /home/foo
# chroot environment you would do this:
# Répertoire racine, les connectés au ftp ne verrons que lui et son contenu
DefaultRoot /home/FTP-shared

#Pour bloquer TOUS les users dans leur home (important pour mon usage)
DefaultRoot ~

#Pour limiter la saturation de la ligne
MaxLoginAttempts    5

#protection contre les acces telnet
#UserAlias	userftp		guest

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/Divers/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/Dessins_animes/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>


<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>

	#<Limit MKD XMKD RNRF RNTO DELE RMD XRMD STOR>
	#AllowAll
	#</Limit>
</Directory>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

```in my case i allow only user access with the good password

---

### Post by epohs on 2005-07-07
Ok, I seem to've gotten it working by chmoding /home/ftp/<mountdir> to 765..

// more specifically, "others" need excecute permission in order to browse that directory.


I'm not really sure what this changed, as it appears to've been 766 previously, but it worked.

If it's obvious to anyone else why this worked, I am curious.


Thank you very much for your help, frodon.

---

### Post by frodon on 2005-07-07
cool  :razz: 

I remember when I created my upload directory with 777 permission it doesn't work and when i set /home/FTP to 777 also ... it has worked. To conclude i think the heart of proftpd problems is to set the good system permissions.
Don't hesitate to post other question about proftpd in this thread or also post interesting thing you learn about proftpd.

Use "ftptop" command to see in real time who download on your server (press "t" to see the download rate).

---

### Post by epohs on 2005-07-07
you wouldn't happen to know if mod_quota is installed by default would you? :)


or, how i would set a maximum filesize on an upload directory?..


// or, "mod_quotatab" rather..

---

### Post by frodon on 2005-07-08
I don't know exactly what feature are compiled with synaptic but I think it include ratio and quotas features, to list all the features installed by the deb file ```
proftpd -l
```
I find something interesting for debug : [http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)

To limit bandwidth : [http://www.proftpd.org/localsite/Userguide/linked/x950.html](http://www.proftpd.org/localsite/Userguide/linked/x950.html)
For ratio I think you need mod_ratio module, use proftpd -l to see if you have it and have a look at the section 4.10 of this link : [http://linux.tnc.edu.tw/techdoc/proftpdfaq-full.htm](http://linux.tnc.edu.tw/techdoc/proftpdfaq-full.htm)
Here an exemple with ratio control : [http://www.freebsdhowtos.com/63.html](http://www.freebsdhowtos.com/63.html)

---

### Post by epohs on 2005-07-08
hmm.. well, both "mod_quotatab.c", and "mod_quotatab_file.c" are listed in [COLOR=Green]proftpd -l[/COLOR], but, I'm not sure where my limit and tally tables are located (I need them right?).

and [COLOR=Green][ftpquota](http://www.castaglia.org/proftpd/modules/ftpquota.html)[/COLOR] also doesn't seem to be on here.


If I specify a location using the [COLOR=Green]QuotaLimitTable[/COLOR] directive in proftpd.conf, will it create the table for me automatically?



// I'm not so concerned with ratios, as I am about forgetting and leaving anonymous uploads open and my harddrive filling up.  :)

So, I'd just like to set a maximum size on the upload directory, and then manually prune it every so often.

---

### Post by frodon on 2005-07-08
[QUOTE=epohs]I'm not sure where my limit and tally tables are located (I need them right?).

If I specify a location using the [COLOR=Green]QuotaLimitTable[/COLOR] directive in proftpd.conf, will it create the table for me automatically?[/QUOTE]

I'never use quotas but i think the best way is to make some tests
The link is not really clear about where are located the tables ... i suggest you : ```
sudo updatedb
locate ftpquotas
```updatedb create a database (or update it) and locate search in this database.
Sorry i haven't any knowledge about ftpquotas  :roll: , but maybe if you post a thread about it in unbuntu server talk you will find someone who's got this knowledge.

---

### Post by epohs on 2005-07-08
Thank you very much, frodon.

You've been extremely helpful.

:)

---

