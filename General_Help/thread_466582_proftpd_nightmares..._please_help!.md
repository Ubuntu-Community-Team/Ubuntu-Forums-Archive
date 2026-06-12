---
title: "proftpd nightmares... please help!"
date: 2007-06-06
forum: General Help
---

### Post by Darth_tater on 2007-06-06
ok, i tried to the best of my ability to follow the guide posted here on these forums [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)


that having been said, this FTP server is part of a file server designed for multiple users.

is there an easy way to get the ftp server to work per user and only work in their home directory?

EG;  lets say there are three users folder inside the /home directory

1) bob
2) janet
3) cindy

how can i make it so that if bob logs in, then he is locked to ONLY his home directory, and from there he can do what ever the hell he wants to any of *his* files.  he cannot browse to another folder outside of his home directory.  he cannot modify any other file/folder outside of his home directory.

the same goes for janet and cindy.  

i think it is doable, but i jsut need somebody to tell me how  (a step by step would be nice, but i can understand if you are not able to do this.

thanks soooo much for any/all help you can provide.


ps: i know/i am sure that there are more people out there that would love to see this written up as a guide, as the proftpd guide on here is already usefull, but not useful for the needs i am requesting.

---

### Post by Darth_tater on 2007-06-07
Wow!  I actually got what I wanted just by tinkering w/ my setup.  This is a first!

What I wanted – a server that could: 	
[INDENT]1) Work with *any* user on my system; use their default user name and their system password.
2) Lock them to their /home directory only... nobody can get out of their directory for any reason!
2b) Allow them to do *anything* except overwrite existing files in their home directory. [/INDENT]

So, in order to do this, I began to follow the guide here
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

I followed each step, just copying and pasting each line into the terminal.  I had to do this because it served as a test.  A test to see if I could get a FTP server up and running, so I would know whether or not it was my configurations that had gone awry.  Now I could confirm that my server was in fact working; granted it was not serving the right directories, and it would only work with one user, but I had a working server.  Once you have confirmed that your server is working, make a backup of the configuration files

```
 sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf.BACKUP 
```

Now you need to edit your configuration file to look like mine

```


# To really apply changes reload proftpd after modifications.
#i think this is to keep files from being overwritten… can somebody post below and correct me?
AllowOverwrite off

#set you server name here
ServerName            "my uberl33t server"
ServerType             standalone 
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message 
ListOptions                    "-l"

# still, make sure to adjust user properties so that any user who is for FTP ONLY has a shell of /bin/false #instead of a real shell.  This is obviously not the case if you have a user that will use this machine #LOCALLY and for FTP.  
RequireValidShell         off

# this is measured in seconds…
TimeoutLogin 30

#do not, uner any circumstances, change this!  It is a HUGE security problem if your root user can login
RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log 
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me) 
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want) 
Port                1337

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works 
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 5

# Set the user and group that the server normally runs at. 
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022 

PersistentPasswd        off

MaxClients 5
MaxClientsPerHost 5
MaxClientsPerUser 5
MaxHostsPerUser 5

# Display a message after a successful login
AccessGrantMsg "welcome!  Now, go away!"
# This message is displayed for each access good or not 
ServerIdent                  on       "you're at home"

# Set /home directory as home directory, this is VERY important if you plan on multiple users!!!

DefaultRoot /home

# Lock all the users in home directory, ***** really important ***** 

DefaultRoot ~ 

# I would set this to a very low number, say, no more than maby 5
MaxLoginAttempts    3

#VALID LOGINS.  This is the syntax for multiple users, obviously if oyu only have one.. .then you delete #the other names!
<Limit LOGIN>
AllowUser Bob Alice John Cathy Stan Kyle Kenny  
DenyALL
</Limit>

# VALID DIRECTORIES… VERY IMPORTANT THAT YOU MAKE ONE OF THEESE FOR EACH USER OF YOUR #SYSTEM!!!!
#make one for Bob, Alice, John, Cathy, Stan, Kyle and Kenny
#i don’t believe that this is necessary (correct me if wrong) if you plan on having *all* users w/ the same #directory permissions!  However, if you need special permissions for a different user then be sure to #adjust them here!

<Directory /home/bob/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD> 
    DenyAll
    </Limit>
</Directory>


```

---

### Post by c4taclysmicPr0posal on 2007-07-11
So, what your saying, is that when you edit that last bit, it automatically makes those dir's?


#VALID LOGINS.  This is the syntax for multiple users, obviously if oyu only have one.. .then you delete #the other names!
<Limit LOGIN>
AllowUser Bob Alice John Cathy Stan Kyle Kenny  
DenyALL
</Limit>

# VALID DIRECTORIES&#8230; VERY IMPORTANT THAT YOU MAKE ONE OF THEESE FOR EACH USER OF YOUR #SYSTEM!!!!
#make one for Bob, Alice, John, Cathy, Stan, Kyle and Kenny
#i don&#8217;t believe that this is necessary (correct me if wrong) if you plan on having *all* users w/ the same #directory permissions!  However, if you need special permissions for a different user then be sure to #adjust them here!

<Directory /home/bob/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD> 
    DenyAll
    </Limit>
</Directory>

so to do this you must do

<quote>sudo mkdir /home/bob
sudo mkdir /home/alice
sudo mkdir /home/john </quote>


do you need to set permissions on these???

e.x
<quote>
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
</quote>

---

### Post by Darth_tater on 2007-07-11
> **c4taclysmicPr0posal said:**
> So, what your saying, is that when you edit that last bit, it automatically makes those dir's?


no.  proftpd will *not* make the directories.  i am sorry if my previous post(s) confused you, but you must make your own directories on your own.  also, you must set your permissions through chmod as well as the proftpd configuration file. 

then for each users's directory (assumeing that is their /home directory) you must make an additional entry into the proftpd file.


```
<Limit LOGIN>
AllowUser Bob Alice John Cathy Stan Kyle Kenny
DenyALL
</Limit>  
```


means that you need to have a 

```
<Directory /home/<username>/*>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>
```

for each person that will be accessing the server.

---

### Post by nix4me on 2007-07-11
defaultroot ~ is what locks them into their home dir.

nix4me

---

### Post by Darth_tater on 2007-07-11
> **nix4me said:**
> defaultroot ~ is what locks them into their home dir.

nix4me


right, but the way i have posted allows for a bit more flexibility because you can specify proftpd access options per users directory that wont conflict with the global user access defaults (its useful if you need to allow multiple things to write to the same directory, but proftpd needs to be restricted...)

also, if you only have /home/bob and /home/janet  and you attempt to login withe the user kenny, its a potential security problem as proftpd will look for /home/kenny

---

