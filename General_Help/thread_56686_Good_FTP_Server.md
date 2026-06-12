---
title: "Good FTP Server?"
date: 2005-08-13
forum: General Help
---

### Post by Freddie on 2005-08-13
Hi! I am looking for a good, and low memory footprint FTP server, which will work with ubuntu (Mac PPC). Can anyone help me?

---

### Post by invalid on 2005-08-13
I use proftpd

Cheers,
Cb

---

### Post by mcmuffy on 2005-08-13
pureftpd is good also.

---

### Post by Freddie on 2005-08-13
[QUOTE=mcmuffy]pureftpd is good also.[/QUOTE]
 I typed 'apt-get install proftpd' at the command line (as root) and I got an error saying that the package could not be found. I then went into add/remove programmes and clicked on advanced. I searched for both pureftpd and proftpd but found nothing. At the bottom I says that there are 34xx packages available and that 84x of them are installed. Am I missing some repostaries (I did re-build my cache)?

---

### Post by invalid on 2005-08-13
sounds like it,
search the Hoary forms for what you should have in your list.

---

### Post by Freddie on 2005-08-13
[QUOTE=invalid]sounds like it,
search the Hoary forms for what you should have in your list.[/QUOTE]
 What list? Sorry, but I have never had to do this before, is there a certian repository which I should add?

---

### Post by invalid on 2005-08-13
edit your /etc/apt/sources.list to look like this:

```
#Main Archive
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

##major bug fix updates
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

#Security Updates Main
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

#Security Updates Universe
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Backports Staging
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
```

then just update your synaptic listing.

---

### Post by Freddie on 2005-08-13
Okay, I have installed proftpd, where do I find the setting file for the programme?
Thank you for all of your help!

---

### Post by mcmuffy on 2005-08-13
I think the easyest way to set up both pure and proftpd would be via webmin. This gives you a browser based interface as opposed to manually editing (and finding) the scripts.

---

### Post by mird on 2005-08-14
[QUOTE=Freddie]Okay, I have installed proftpd, where do I find the setting file for the programme?
Thank you for all of your help![/QUOTE]
The configuration file is located at [font=fixed]/etc/proftpd.conf[/font].  The layout and format of the file is (purposely) very similar to Apache, so if you've had experience editing Apache configs before you should find thing relatively easy.

There is a wealth of very good information and [documentation](http://www.proftpd.org/docs/) on the [ProFTPD website](http://www.proftpd.org/docs/) should you get stuck at all.

---

### Post by invalid on 2005-08-14
I agree with mcmuffy, you should definetly set up webmin.

You can find this in synaptic.

You will also need to install the module of the ftpd you chose. Just search for the ftpd, and you should see something named ftpd-webmin (or similar).

Cheers,
Cb.

---

### Post by Freddie on 2005-08-14
I went to the terminal prompt and typed in:
apt-get install webmin
[...]
apt-get install webmin-proftpd

I was expecting it to ask me about ports and users etc but the only config box I got was one saying a load of stuff (I cant remember what it was). So, what am I meant to do now?

---

### Post by Freddie on 2005-08-14
Well, I went to [https://localhost:10000](https://localhost:10000) and it is asking me to log in. Now according to the documentation my username will be root and my password will be my root password. So I typed in root and then my root password but it would not let me in, then the dumb thing locked me out of my own server!
I am using the same password that I use when I use the package manager, start up the root terminal and the one I had to type in when I ran my first 'sudo xxxxxxx' command. Can someone help.

---

### Post by Freddie on 2005-08-14
I have managed to change the password on webmin and am able to get it. I do not understand one bit of the ProFTPd modules options, nothing like 'Add User' or anything like that (what I am used to seeing) all I see is stuff about virtual ftp servers and messages to display. Can someone tell me how to set this darned thing up? ](*,)

---

### Post by Sam0r on 2005-08-14
What exactly do you want to be able to do with the ftp server?

I'm trying to set up proftpd myself, on an x86 server, but its not going too well with Hoary!

---

### Post by Freddie on 2005-08-14
I want to be able to use ftp to access my hard disk remotely (so have a root user) as well as be able to create users, who can only view certian folders (read/write privilages).

I have just tried vsftpd, which also turned out to be well, a load of junk. No idea of users what so ever, could not understand it one bit. The only thing which I have found out today is that anything that ends in '*ftpd' is hard to configure, has very few options and will not do what I want. I am used to using filezilla (server) which is a [i]real[i] ftp server, you add a user, give them a folder and some permissions and you're done. Am I really asking that much? I just want to be able to access my files from a remote computer and allow some other people access to the server. Yet none of the three ftp servers I have tried (pro/pure/vs:ftpd) have been able to do it. I can uderstand why none of them have GUI's but I cant understand why they do not have the features which I am used to. I will keep at it, there has to be a good server or a good guide to a server somewhere...

---

### Post by invalid on 2005-08-14
You need to set up users in System > Users & Groups (using webmin), not the ftpd module.

After you set up a user, you can give him or her certain restrictions through the ftpd module.

---

### Post by Freddie on 2005-08-15
I have chosen to put my ftp folder at /home/ftp, but my user does not have rights to it. How can I give myself rights to that folder (as my user is the one which proftpd runs under). I think it is something like chown folder owner .

---

### Post by Freddie on 2005-08-15
It is now kinda working, got my user set up and I can/read files fine. But, I want to add anonymous user support. I have a folder called home/ftp/shared which I want to be the root folder for all anonymouse users and I do not want them to have any form of write abilities. proftpd runs off of the user 'freddie' which owns the home directory. Can someone please help me with the config folder! Here is my current one :
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

AllowOverwrite on
AuthAliasOnly on

UserAlias macservroot freddie

ServerName			"MacServ"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

#DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

DefaultRoot /home/ftp

<Directory /home/ftp/>
	umask 022 022
	AllowOverwrite on
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	AllowAll
	</Limit>
</Directory>

```
Thanks for all of your help.

---

### Post by Freddie on 2005-08-15
I have tried the following code to allow anonymous users, however it does not work when I connect to the ftp server I am still asked for my login detail even if I type in anomymous/ftp as my username it still does not work. I am not sure what I am doing wrong, can someone please help me out here?
```

 <Anonymous /home/ftp/junkpit>
   User				nobody
   Group				nogroup
   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias			anonymous ftp
   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser	on ftp
   DirFakeGroup on ftp
   
   RequireValidShell		off
 
   # Limit the maximum number of anonymous logins
   MaxClients			10
 
   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
       DenyAll
     </Limit>
   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
 </Anonymous>


```

---

### Post by Freddie on 2005-08-16
I have done it! I found what I was looking for, a GUI frontend for proftpd. It is called 'gproftpd' (it is written in GTK+) and allows me to monitor in real time the active users and what they are doing as well as create new users. The package itself was not an easy find as I had to download the .deb file and then run it using dpkg. But I am happy now it works.

---

