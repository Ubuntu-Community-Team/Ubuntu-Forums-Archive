---
title: "Problem with upload in FTP server using lftp client"
date: 2022-11-09
forum: General Help
---

### Post by gugu88 on 2022-11-09
Hi everybody,
 
 
 I have a problem using lftp client to upload a file to a server. I am 100% newby on ftp (first time I actually try to do something with it) and I probably miss something basic.
 
 
 I followed [this basic guide]("https://www.server-world.info/en/note?os=Debian_10&p=ftp&f=4") to install lftp client and realize basic access to a server.

 
 
 My problem is that when I use the put command to upload a file it gives Access failed: 404 error. However, the file it is shown by !ls command in the current local folder.  

 
 
 I have find[ this discussion ]("https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/lftp-ls-can-see-files-but-get-access-failed-404-filenotfound-%5Creadme-txt-occ-4175419828/")with a similar problem (the opposite, it gives the error trying to download a file that was detected by ls) but I do not understand the discussion… Again, I am a newby.

 
 
 Here the code I used.  

```
guido@guido-debian:~$ lftp -u agc http://capannone.com.br
Password: 
cd ok, cwd=/                                                 
lftp agc@capannone.com.br:/> cd /wp-content/uploads/2022/11
cd: received redirection to `http://agc@capannone.com.br/wp-content/uploads/2022/11/'
Password: 
cd ok, cwd=/wp-content/uploads/2022/11 
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> ls
drwxr-xr-x  --  ..                    
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> !ls -l
total 256
-rwxrwxrwx 1 guido guido  47972 Nov  9 16:43 CardapioDigitalNov2022_FinalGrande.docx
-rw-r--r-- 1 guido guido 123856 Nov  9 19:26 CardapioDigitalNov2022FinalGrande.pdf
drwxr-xr-x 2 guido guido   4096 Oct 28 16:48 Desktop
drwxr-xr-x 2 guido guido   4096 Nov  5 12:27 Documents
drwxr-xr-x 2 guido guido   4096 Nov  5 12:47 Downloads
drwx------ 5 guido guido   4096 Nov  9 20:29 Dropbox
drwxr-xr-x 2 guido guido   4096 Mar 26  2020 Music
drwxr-xr-x 2 guido guido   4096 May  6  2021 Pictures
drwxr-xr-x 2 guido guido   4096 Nov  5 18:06 prova
-rwxr-xr-x 1 guido guido    143 Nov  5 20:24 ProvaCPULimit
drwxr-xr-x 2 guido guido   4096 Mar 26  2020 Public
drwxr-xr-x 2 guido guido   4096 Apr 29  2021 Recordings
drwxr-xr-x 7 root  root    4096 May  7  2021 SharedIES
drwx------ 5 guido guido   4096 Oct 28 16:44 snap
drwxr-xr-x 2 guido guido   4096 Nov  5 12:34 Temp
drwxr-xr-x 2 guido guido   4096 Mar 26  2020 Templates
-rw-r--r-- 1 root  root   23183 Feb 17  2022 usr.lib.snapd.snap-confine.real
drwxr-xr-x 2 guido guido   4096 May  6  2021 Videos
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> put -a CardapioDigitalNov2022_FinalGrande.docx 
put: Access failed: 404 Not Found (CardapioDigitalNov2022_FinalGrande.docx)
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> put CardapioDigitalNov2022_FinalGrande.docx 
put: Access failed: 404 Not Found (CardapioDigitalNov2022_FinalGrande.docx)      
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> 

```

 
 
 
 
 
 
 My system is Debian Buster.  

Thanks in advnce for your hepl

---

### Post by TheFu on 2022-11-09
Let me help you out.

I'm looking through what you've posted.  There seems to be a little confusion between local and remote directories as well as which useraccounts have write permissions where.  When you connect to the remote system as the "agc" account, you can only upload files to directories where agc has write permissions.  

The line:
```
lftp agc@capannone.com.br:/wp-content/uploads/2022/11> ls
drwxr-xr-x  --  ..                    

```
Doesn't show the owner, group or permissions.  Usually the 'lls -l' command is used when ftp is used to see those.  Hopefully, the owner of the upload directory under WordPress is the web server account (i.e. the account that runs the web server, not agc.  That would be a huge issue.  OTOH, the rest of the WP directories should NOT be writable by the web server account.

When we are new to Unix/Linux, we need to remember, constantly, that it is a multi-user OS from the ground up.  If it were me, I'd upload the files to your HOME on the remote system, then worry about getting them to the directory they need to be.  BTW, the Upload directory really shouldn't be accessable from WP for read by anyone.  It should be a directory that accepts files through the WP admin webapp, but doesn't allow anyone using a browser to access any uploaded files. The files need to be moved elsewhere, processed to ensure they aren't malicious, then placed somewhere else to be used or made available through the wordpress site.  For example, allowing uploads of any files that aren't plain text really means those files need some sort of validation/processing.  For example, video file uploads should be transcoded by a trusted tool and the original file deleted.  Same for images, documents, PDFs, unless the source is 100% trustworthy.  Unsafe files in a wordpress site can be used to open a back door and take over the entire server. Be careful out there, please.

Plain FTP shouldn't be used, since around 2000.

Tftp (which is what I initially read in the OP) is only for private networks with specific hardware that ONLY supports tftp and nothing else.  Any device made in the last 10 yrs, should support an HTTP upload method.

I suppose lftp is a little nicer CLI version of plain FTP.  Back in the 1990s, I was using ncftp, which was ok, until everywhere I worked removed plain FTP and switched to sftp for security.

On Linux, if you want to upload a file, use sftp.  Typically, that is enabled by installing the openssh-server package. That way you get sshd (the server) and all it's goodness, along with scp, sftp-server and enable about 50 other tools that use ssh for tunnels and authentication (rsync, NX, sshfs, and nearly every network backup tool made).  ssh is the way that computers connect together around the world in a convenient and secure way.  This may be completely new to Windows people, but every other OS has been using ssh, sftp since around 1995.

There's a built-in sftp client.  Install "openssh-client" package and you'll get it.  Or you can just install the metapackage "ssh" in Ubuntu that installs the ssh client and server. There's little reason NOT to have both on every Unix system.  On Linux, you'll probably want to install "fail2ban" to automatically block brute force ssh/sftp/scp .... connection attempts. Both don't require any configuration to start using, but they support full customization, if you like. So, 
```
sudo apt install ssh fail2ban
```
and you get the ssh client, server, sftp client, server, enable sftp in the file manager and setup brute force protections for password hacking attempt blocking.  I think the default allows 5 or 10 failed attempts per hour, before blocking the IP for a day.  I haven't used a password to transfer files in about 20 yrs - we use ssh-keys for authentication, which only fail if there's some incompatibility, which almost never happens.

Also, nearly every Linux GUI file manager will enable sftp integration as a client when the "ssh" package is installed.  In the address area, use "sftp://xx.yy.zz.aa/ to connect to another system.  That address can be the IP, DNS or mDNS name ... or a configured alias from your ~/.ssh/config file.  So we can drag-n-drop files between our local system and the remote system(s) in a secure way.  Rock on!

Additionally, if you setup ssh-keys between the client and server, those will be automatically used when possible.  Just the initial first use of the ssh-key at every login to the client workstation, but if you don't log out, the keys will remain available for connections to other systems.  I go for weeks connecting to different systems without seeing any prompts.  ssh is the only tool that I know which is both MORE convenient AND more secure.  When I say "ssh is ..." that applies to the 50 other ssh-based tools too.  Really, learn ssh, sftp, rsync and a good versioning backup tool. You'll thank me.  You can use x2go for remote desktops, sshfs to locally mount remote storage over ssh too.  These are awesome tools that leverage ssh.

Heck, the wordpress server probably already has ssh-server installed and working, so I'd bet the sftp-server is there and working already too.  Can't hurt to try it.

Now, it is likely when we get a permission denied error that the userid for the connection doesn't have write permissions to the target directory.  There's little anyone here can do about that except to say that learning Unix file and directory permissions is mandatory.  Spend the time and effort to learn it, to avoid frustration that will certainly waste hours, days, weeks, months. Here's a tutorial: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) . That should take about 15 minutes to work through, but another 30 minutes of "self-study" is needed for everything to "click".    OTOH, in 45 minutes, you can have 90% of what anyone except Unix admins need to know about all Unix permissions for files and directories learned.  Block out an hour and do the work.  Sooner than later.  Git 'er done.   Setup 3 new user accounts and 2 groups. Mix and match the different userids btween the groups, but have 1 userid that isn't in each group.  Open 3 terminals and login to each of those 3 new accounts. cd /tmp/ and start making empty directories and empty files to play with the permissions down there using each of the 3 userids.  See what works and what doesn't.  While there are 3 "groups" of permissions (rwx) for 3 different types of users (own, group, everyone else), once you master 1 of those, the others will become clearer.   When you know why 711 permissions are useful on a directory with 551 permissions on a program file and a script file inside the directory, you'll be done.  Be certain you know which programs work and which won't in a directory with those permissions.  No cheating, since that would miss all the needed learning before that level is reached.

A good resource to learn Linux without a GUI is: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a no-hassle, free, download. You can buy a copy at your local bookstore if you like, but that isn't necessary.  Learning stuff in the most efficient order will save time overall. About the first 230 pgs are necessary to get into beginner level knowledge.  With the basic knowledge it provides, you'll be more able to understand random posts and googling for answers will be significantly safer than it is now.  Seeking "what to type" isn't safe because all of our systems are a little different from each other. There isn't a "standard" system.

---

### Post by HermanAB on 2022-11-10
Hmm, +100 for SSH.  

Really, SSH is all you need in life. OK, a mug of hot chocolate may help too.

Do yourself a favour and read the snailbook [http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by gugu88 on 2022-11-11
Hi TheFu, thank you very much for your comprehensive answer and for the links!! You are completely right, I miss some basic knowledge about file permission and the ftp/ssh protocols. 

I will read the documentation you suggested to better understand what I am doing. 

However, the "agc" user I have been given should have required permission. The former website administrator gave me the access credential to FTP and WP and I supposed them to be with writing permission (maybe wrong supposition).  

However, I am a bit surprised about the following: as you suggested, I installed the "ssh" package on Debian and sftp integration was automatically enabled in Nautilus. If I type sftp://capannone.com.br in the address area, it asks me for user and password but if I type "agc" and the password I was formerly using in my example I get access error (530).
Furthermore, I noticed that using the code:

```
lftp -u XXX http://capannone.com.br
```
whatever I use as "user" I get the same. I mean, I can see all the files in the remote server and apparently I do not have write permission and the line 
```
 lftp try@capannone.com.br:/wp-content/uploads/2022/11> ls
drwxr-xr-x -- ..
```
still does not show owner, group or permission…
This makes me suspect that I was actually logging in as anonymous user (or something similar). 

The point is that I am not the website administrator, I am just an amateur Linux user who is helping out making some change to the website of this restaurant and to do so I was given the access credential by the former administrator. I am beginning to believe that there is something wrong with those credentials.... 

The former administrator told me the following:

Host: ftp.capannone.com.br
User: [EMAIL="agc@capannone.com.br"]agc@capannone.com.br[/EMAIL]
Pass: ***************

I get “denied login” in Nautilus ([ftp://capannone.com.br](ftp://capannone.com.br)) regardless I use only "agc" or the whole "agc@capannone.com.br". 

However, I guess I will take some time to carefully read the suggested documentation and to better understand the ftp/ssh protocols. In the meanwhile, I will reach the former administrator to confirm the access credentials. 

Thanks again for your help, I believe you pointed me in the right direction!

---

### Post by TheFu on 2022-11-11
> **gugu88 said:**
>  
However, the "agc" user I have been given should have required permission. The former website administrator gave me the access credential to FTP and WP and I supposed them to be with writing permission (maybe wrong supposition).  

Don't assume that.  Use ssh to login and visit the specific directory, run an 'ls -la' on the directory. I bet the permission are such that the account provided doesn't allow write.  If the remote server doesn't allow ssh, you need a better provider.  Actually, the fact that they allow plain FTP is a huge warning that they should be fired ASAP, since they don't take network security very serious.  

BTW, it is possible for a plain FTP connection to have zero, nothing, nada, to do with a local user account.  I haven't seen that in a few decades, but I fired the last web host with plain FTP around 2002.

Admins often forget little details, like ensuring a specific userid has access to write files in specific locations.
Before you contact the old admin, I'd strongly suggest copying the files to your HOME directory using the credentials provided first.  Then tell them where you'd like those files to be located, with the owner, group, and permissions required.  That way, the files are already there and you don't have to waste time for his mistake, if a mistake was made.  Chances are, he will copy/move the files to the location you want and set the permissions as needed or requested, assuming you don't ask for the wrong stuff that would make the entire WP site hackable.

---

