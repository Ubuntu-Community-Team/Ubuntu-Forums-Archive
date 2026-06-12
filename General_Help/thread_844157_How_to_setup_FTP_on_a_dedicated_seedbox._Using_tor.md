---
title: "How to setup FTP on a dedicated seedbox. Using torrentflux and need to dl files"
date: 2008-06-29
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-29
Hi every1,

Well yesterday I dedicated server I bought was finally setup. I'm using it as a seedbox ( the speeds are crazy with OVH by the way )
I have webmin and ssh setup and I've filled up over half of my 250 GB drive already! I need to get some of my completed files down.

I intend to setup a sFTP to get my files. ( the flux built in downloader is a bit tempermental, when I click on 'zip & download' the download is all of 0bytes. ) I'd rather use ftp anyway.

I've located a [guide ]("http://ubuntuforums.org/showthread.php?t=79588")on here ( thanx Frodon ) it's from 2005. I've installed proftpd mainly for this guide and the webmin module.

My question is this:

How do I setup the default FTP directory to be my /home/torrents/fluxadmin folder?

It will only be me and my brother who uses it ( hopefully! )so we only neeed one account. I've got as far as editing the /etc/shells config with /bin/false. I assume I wont need shell access to delete old downloads from the server.
I thought about setting up a user with the same home directory ( /home/torrents/fluxadmin ) but I can see that logically this wouldn't work.
I then thought about adding the torrentflux user to use ftp but when I look in the webmin module I have no 'torrentflux' user ( i blindly followed a guide to set it up. ) 
So what's the best way of doing this? Finding the user that owns that home directory?

Any help would be really appreciated guys, thanx.

Gareth

p.s. Also I think I'm running mysql as root? is this bad?

---

### Post by garethsimpsonuk on 2008-06-29
I've just logged in to webmin file manager to see who owns that home dir ( it's www-data ) and I get this msg in the sidebar:

> Security Warning 	
Warning! Webmin has detected that the program 'my server url' was linked to from an unknown URL, which appears to be outside the Webmin server. This may be an attempt to trick your server into executing a dangerous command.

If your browser does not send the Referer header needed, you can turn off this check as follows :

    * Login to Webmin normally.
    * Go to the Webmin Configuration module.
    * Click on the Trusted Referrers icon.
    * Check the Trust links from unknown referrers box, and click Save.

Alternately, you can configure Webmin to allow links from unknown referers by :

    * Login as root, and edit the /etc/webmin/config file.
    * Find the line referers_none=1 and change it to referers_none=0.
    * Save the file.

What do I do? How do I check logs to make sure evrything is o.k?

edit: firefox crashed and needed to restart b4 this happened. are they linked?

---

### Post by garethsimpsonuk on 2008-06-29
anyone?

---

### Post by Scorpuk on 2008-06-29
The following is purely guess work as I'm away from my linux server to try anything out. :-)


Change the install of proftpd from the guide you used as follows.

1. Dont add a new user
2. chmod 755 your /home/torrents/fluxadmin
3. follow step three from the guide changing these bits:

```

UserAlias alias-name server-logon-name


ServerName			"Whatever you want to call it here"
ServerType 			standalone
DeferWelcome			on
```

```
DefaultRoot /home/torrents/fluxadmin
```


```
<Directory /home/torrents/fluxadmin>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```



Since I cant try them myself these are guesses, hopefully educated ones. :D

Forgot to say delete these lines from the setup file:

```
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by garethsimpsonuk on 2008-06-29
you're a legend m8. i'll give it a go now and post results. thanx

---

### Post by garethsimpsonuk on 2008-06-29
it 'fails to connect' but I that's probably because I've done so much messing about with it. 

Am I right in thinking where it says > UserAlias alias-name server-logon-name


That I can put torrents as alias and www-data as server log on name?

How would I remove proftpd and start again? I've added users and direcories trying to get it to work and I wish I hadn't.

Thanks for your help

---

### Post by Scorpuk on 2008-06-29
server-logon-name is the account your server logs on with. (Probably the user you installed as or run the torrent program with)

alias-name is any ole name you want so that the real system logon account is never displayed.

to remove proftpd look in synaptic for it and tell it to completely remove it and all settings for it. One of the options you get when you click on the lil box.

---

### Post by garethsimpsonuk on 2008-06-29
i don't have a gui, I'm running the server OS on a dedi box in a data centre. I've been here since this morning trying to set it up!

I'm thinking of reinstalling everything again as I can't get it to work. With the data centre I log in as root as they don't let let you do the install yourself ( they just reinstall a disk image ).

Do you reckon you could have a look? I'll let you in with webmin and putty? I'll return the favour anyway I can ( maybe you would like something downloaded on a 100Mbit connection? )

Thanks for your help

---

### Post by Scorpuk on 2008-06-29
try this:
```

sudo apt-get purge proftpd
```

---

### Post by garethsimpsonuk on 2008-06-29
I've got another problem that has been there from the start. When I do certain things it pops up. It looks like this:

> 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
-bash: 0: command not found
root@ks361702:~# Need to get 0B/922kB of archives.
    are supported and installed on your system.
-bash: Need: command not found
root@ks361702:~# After this operation, 2552kB of additional disk space will be used.
-bash: After: command not found
perl: warning: Falling back to the standard locale ("C").
 * Starting ftp server proftpd                                                                                                                                                    - warning: the DisplayFirstChdir directive is deprecated and will be removed in                                                                                                  a future release.  Please use the DisplayChdir directive.
                                                                         [ OK ]
root@ks361702:~# perl: warning: Setting locale failed.
-bash: perl:: command not found
root@ks361702:~# perl: warning: Please check that your locale settings:
-bash: perl:: command not found
root@ks361702:~#         LANGUAGE = (unset),
-bash: syntax error near unexpected token `('
root@ks361702:~#         LC_ALL = (unset),
-bash: syntax error near unexpected token `('
root@ks361702:~#         LANG = "en_GB.UTF-8"
-bash: LANG: command not found
root@ks361702:~#     are supported and installed on your system.
-bash: are: command not found
root@ks361702:~# perl: warning: Falling back to the standard locale ("C").
-bash: syntax error near unexpected token `('
root@ks361702:~# locale: Cannot set LC_CTYPE to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# locale: Cannot set LC_MESSAGES to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# locale: Cannot set LC_ALL to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# Preconfiguring packages ...
-bash: Preconfiguring: command not found
root@ks361702:~# Selecting previously deselected package proftpd.
-bash: Selecting: command not found
root@ks361702:~# (Reading database ... 39682 files and directories currently installed.)
-bash: Reading: command not found
root@ks361702:~# Unpacking proftpd (from .../proftpd_1.3.1-6ubuntu1_i386.deb) ...
-bash: syntax error near unexpected token `('
root@ks361702:~# Setting up proftpd (1.3.1-6ubuntu1) ...
-bash: syntax error near unexpected token `('
root@ks361702:~# perl: warning: Setting locale failed.
-bash: perl:: command not found
root@ks361702:~# perl: warning: Please check that your locale settings:
-bash: perl:: command not found
root@ks361702:~#         LANGUAGE = (unset),
-bash: syntax error near unexpected token `('
root@ks361702:~#         LC_ALL = (unset),
-bash: syntax error near unexpected token `('
root@ks361702:~#         LANG = "en_GB.UTF-8"
-bash: LANG: command not found
root@ks361702:~#     are supported and installed on your system.
-bash: are: command not found
root@ks361702:~# perl: warning: Falling back to the standard locale ("C").
-bash: syntax error near unexpected token `('
root@ks361702:~# locale: Cannot set LC_CTYPE to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# locale: Cannot set LC_MESSAGES to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# locale: Cannot set LC_ALL to default locale: No such file or directory
-bash: locale:: command not found
root@ks361702:~# perl: warning: Setting locale failed.


But that's beyond the scope of this thread. It looks like something is wrong with the local settings / languages. The server is abroad. I guess I need to get onto the provider about that. Anyway that's preventing me from doing a reinstall of proftpd.

Thanks for your help mate.

---

### Post by earthmeLon on 2008-06-29
Maybe you could just change the download location in tf to the ftp directory.

Could you create a link between the two directories?

---

### Post by Scorpuk on 2008-06-30
not sure that would work as part of the setup locks the ftp user to the specified ftp directory as a security measure. Therefore it probably would not follow a symbolic link.

---

### Post by garethsimpsonuk on 2008-06-30
yea i've looked at that m8. it's because the ftp user has to have minimum access.

I'm thinking of doing a reinstall ( I don't really wanna lose 120GB of data tho ) and then I could setup the ftp first, once i know that's workin I can install LAMP and Flux.

All yesterday it wouldn't work and had a look this morning, with no joy.

Can n e 1 advise me on an anonymous FTP setup just so I can get the files off?

---

### Post by hyper_ch on 2008-06-30
why don't use use SSH/SCP to get the files from the box to your computer?

---

### Post by garethsimpsonuk on 2008-06-30
would that be slower than HTTP? Do u mean like via putty? the files are downloading via http now but they will probably take all day!

Man I thought Samba was hard.

Thanx 4 the post I'll look into that

---

### Post by hyper_ch on 2008-06-30
it would be a bit slower but not noticeably... if you're on windows you can use WinSCP ([http://www.winscp.com](http://www.winscp.com)). That looks like a normal ftp client but makes scp/ssh connections. Just use your normal (ssh) login.

---

### Post by garethsimpsonuk on 2008-06-30
oh excellent i'll give that a try then. i've already started downloading the files from my server to my box using the flux in built http downloader ( i've done around 500MB @ 70 / 80 KB/s x 5 ) is it worth stopping them and starting with winscp or just leaving them? They're gonna take all night anyway.
Thanks for the help

---

### Post by hyper_ch on 2008-06-30
winscp should be able to resume a download... even if it's started with some other program.

---

### Post by garethsimpsonuk on 2008-06-30
thanx m8. i'm gonna do a reinstall and setup ftp first. that way if anything goes wrong, i just reformat it. but until then this will help me get the files down i've already got.
Also I think mysql is running as root, i'm pretty sure it shouldn't be so i need to sort that out

---

