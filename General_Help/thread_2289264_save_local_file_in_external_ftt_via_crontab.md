---
title: "save local file in external ftt via crontab"
date: 2015-08-02
forum: General Help
---

### Post by capitan.noobgmail on 2015-08-02
Hello, I want to save a local file in the directory "tmp/motion" to a external FTP, unfortunately I don't know the correctly steps.
[COLOR=#333333][FONT=Tahoma]1. I have create a script "scriptforftp"[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]sudo nano /usr/bin/[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]scriptforftp[/FONT][/COLOR]

[COLOR=#333333][FONT=Tahoma]2.[/FONT][/COLOR]script content[FONT=Tahoma, Verdana, Arial, sans-serif][COLOR=#333333]:[/COLOR][/FONT]
[COLOR=#333333][FONT=Tahoma]#!/bin/sh[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]ftp &#8208;i &#8208;n [/FONT][/COLOR][http://ftp.pippo.com]("http://ftp.pippo.com/")[COLOR=#333333][FONT=Tahoma] <<EOF[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]user utentepippo1 passwordhello[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]lcd /tmp/motion/[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]put index.html[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]quit[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]EOF[/FONT][/COLOR]

[COLOR=#333333][FONT=Tahoma]3. [/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]In the crontab I have write the word[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]*/5 * * * * /pathto/sh /usr/bin/[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]scriptforftp[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma] >/dev/null 2>&1[/FONT][/COLOR]

Where am I wrong? Thank you in advance

---

### Post by TheFu on 2015-08-02
a) plain FTP should have died in 1992.
b) sftp should be used, if at all possible. It uses ssh authentication methods - and the command interface is designed to be a drop-in replacement for ftp
c) if you have no other choice, take a look at the .netrc file - create/edit the one in your HOME. **man netrc** has the details. It is a simple file. Be certain to set the permissions so that only the userid can read it - not the group and not the world.

You may want to check out **ncftp** - last time I used it (2000-ish), it was highly script-able and allowed the full path to be specified in the URL arguments - no need to lcd/cd .

Do you really need this running as root?  From here, that doesn't seem necessary. Running a non-secure program like plain ftp is to be avoided, especially as root.

Good luck!

---

### Post by nerdtron on 2015-08-02
change /bin/sh to /bin/bash as they are different in Ubuntu.

Also, have you tried to run your script manually? is it working? You should be able to run the script manually and confirmed that it is working before you put it as a cron entry.

---

### Post by Lars Noodén on 2015-08-03
Remove the extra reference to the shell, it's already in the script in the first line.  

```

3. In the crontab I have write the word
*/5 * * * * [s]/pathto/sh[/s] /usr/bin/scriptforftp >/dev/null 2>&1

```

Then make sure that you've set permissions to executable (+x) for the script.


And +1 to all TheFu wrote about using SFTP.  There are a few edge cases where FTP is still useful, but they are few in number and getting fewer all the time.  If you have control over the server, I'd recommend removing FTP and using SFTP instead.

---

### Post by capitan.noobgmail on 2015-08-03
Hi at all, I very noob, I tried to modify the script in this mode:

in the usr/bin/ i have create a script nome "[COLOR=#333333][FONT=Tahoma]scriptforftp"
[/FONT][/COLOR]
#!/usr/bin/bash
ftp -i -n ftp.domain.com <<EOF
user pippo1 pluto
cd /folderinthexternalftp/
lcd /tmp/motion/
put index.html
quit
EOF

---
After, I tried to put a permission with this word:  
sudo chmod -R 777 /usr/bin/[COLOR=#333333][FONT=Tahoma]scriptforftp
----
[/FONT][/COLOR]When I execute the script:
sudo service [COLOR=#333333][FONT=Tahoma]scriptforftp[/FONT][/COLOR] start
[COLOR=#333333][FONT=Tahoma]----
[/FONT][/COLOR]I obtain this message:   
fileftp: unrecognized service
---
where am I wrong? 
After I'll try sftp.






[COLOR=#333333][FONT=Tahoma]

[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-08-03
Well, the permissions should be 755 or 751 or something like that.  Also the -R is not needed for a single file, with [chmod](http://manpages.ubuntu.com/manpages/trusty/en/man1/chmod.1.html) it means recursion and would be only useful in certain situations where you want to affect a directory and any subdirectories and all the files within them.  

Then the better [place for homemade scripts](http://manpages.ubuntu.com/manpages/trusty/en/man7/hier.7.html) would be /usr/local/bin/

```

sudo chmod 751 /usr/local/bin/scriptforftp

```

Then you would not need the [service](http://manpages.ubuntu.com/manpages/trusty/en/man8/service.8.html) program at all at this stage.  That would be for something you have prepared an Upstart recipe for.   It is enough to name the script and it will run, if everything else is in order:

```

/usr/local/bin/scriptforftp

```

And, again, SFTP would be the way to go if you don't want the whole network to know the user name, password and data.  Plain FTP leaks all of that to the world and should not be used in most cases.  Why are you trying with FTP instead of SFTP?

---

### Post by capitan.noobgmail on 2015-08-05
[SIZE=2]Hi I have install vsftpd but now i don't know how send the files on external folder via crontab.

I write a new fase:
step.1 
[/SIZE][COLOR=#333333][FONT=Verdana][SIZE=2]install vsftpd + openssl + configuration and block anonymous access

step.2
check via filezilla if vsffpd run, test OK work.

step.3
I can try to reconfigure "[COLOR=#000000][FONT=Ubuntu Mono]scriptforftp"[/FONT][/COLOR] I'm not able :-/
#!/usr/bin/bash# Put FTP server details here
SERVER=ftp.pippo.com                                       (no space after the =)      
USERNAME=pippo1@mydomain.com                   (no space after the =) 
PASSWORD=pluto                                              (no space after the =) 
# local directory containing source backup file
SOURCEFILES=/usr/local/motion/ 
# remote server directory path in which backup needs to be put in
BACKUPDIRCTORY=/folderpippo/
# login to remote server
ftp -n -i $SERVER <<EOF
user $USERNAME $PASSWORD
cd $ BACKUPDIRCTORY
mput $ SOURCEFILES/*.tar.gz
quit
EOF

step.4
[COLOR=#000000][FONT=Ubuntu Mono]sudo chmod 751 /usr/local/bin/scriptforftp[/FONT][/COLOR]

step.5 
reconfiguration crontab
* 5 * * * /usr/local/bin/[COLOR=#000000][FONT=Ubuntu Mono]scriptforftp [/FONT][/COLOR]>/dev/null 2>&1

result don't run :-/, can you help me?[/SIZE]


[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-08-05
Take a look at ncftp, a much better FTP client than the standard ftp program. 

There's a companion program, ncftpput, that is designed specifically for scripted uploads.

---

