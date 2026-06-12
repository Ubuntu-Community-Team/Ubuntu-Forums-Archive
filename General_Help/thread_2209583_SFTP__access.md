---
title: "SFTP  access"
date: 2014-03-06
forum: General Help
---

### Post by mark103 on 2014-03-06
Hows it going just have a quick question on Ubuntu server 12.04, i have it all up and running perfect ftp i can ssh into my server from outside my LAN all good. My question is 
i want to add my friend to the server so he log in through SFTP and download files i have for him, but i want him to only see that folder with his files and none of my other folders and files i have on
my server.
 
Now ftp works perfect so does SFTP its just he can see all my files at the moment so i just want to know how lock him out of that , ive looked around but cant really find anything on this any help would be really appreciated.
 I have webmin installed too i tried adding a new user but when i setup he can see all my files and folder ie family pictures and that.

Thanks

---

### Post by Lars Noodén on 2014-03-06
Two things.  Actually three.

First you can change the permissions of the users' home directories so that others cannot read them.

```

sudo chmod 750 /home/*

```

Second you can put him in a group, such as *sftponly* 

```

sudo groupadd sftponly
sudo gpasswd --add someuser sftponly

```

and then edit the SSH server's configuration to lock him into his directory.

```

Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u

```

Which version of openssh-server are you running?  The -d option only was added with the version that is running with Saucy.  If you are running and older version, there is a slightly different way.

---

### Post by mark103 on 2014-03-06
hows it going thanks for getting back to me i have added  my friend to the groupadd sftponly but the third part im not sure about im new to ubuntu is it sudo vim /etc/vsftp.conf

---

### Post by Lars Noodén on 2014-03-06
Oh.  The usual way of getting SFTP access is via openssh-server.  I've stayed away from [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) since SFTP was available.  

With VSFTP, the method is different.

[https://help.ubuntu.com/community/vsftpd#To_chroat_users](https://help.ubuntu.com/community/vsftpd#To_chroat_users)

---

### Post by mark103 on 2014-03-06
ok cool thanks but i can login using sftp using filezilla i have setup an account for my friend its working perfect only problems is i want to hide my files thats all :)

---

### Post by Lars Noodén on 2014-03-06
Are you sure it is SFTP and not FTP or FTPS?

---

### Post by mark103 on 2014-03-06
when i want to login from outside my LAN i use an ftp program but myconnection type is SFTP over SSH and i use my username and password and i can login and grab my files

---

### Post by Lars Noodén on 2014-03-06
Maybe you have the package openssh-server installed.  That would give you functioning SFTP without needing any configuration for basic access.  For chroot, you'd need the steps above.  You can check the installation status:

```

dpkg -l openssh-server vsftpd

```

If the first column in the output there for both is an **i** then you have both installed.  In that case you can remove vsftpd.

---

### Post by mark103 on 2014-03-06
ii  openssh-server              1:5.9p1-5ubuntu1.1          secure shell (SSH) server, for secure access from remote machines
ii  vsftpd                      2.3.5-1ubuntu2              lightweight, efficient FTP server written for security

this is what comes up when i put your command in cheers

---

### Post by Lars Noodén on 2014-03-06
Ok then you have both installed.  If you are using [FTP](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely) then you can keep vsftpd.  Otherwise it is wise to remove it.  
You can test that by turning off vsftpd and trying an SFTP connection.

```

sudo service vsftpd stop

```

I'm pretty sure you can still connect with SFTP after that.  Your SFTP connection is probably being handled by openssh-server.  If not, use 'start' there and forget the following.


However, you have a version older than 6.2 so my instructions on chrooting need to be modified.  First only root can have write access to the user's main directory for chroot to work:

```

sudo chown root:root /home/user

```

Then sshd_config gets lines like these at the end:

```

Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory %h
        X11Forwarding no
        ForceCommand internal-sftp

```

---

### Post by mark103 on 2014-03-06
ok cool stopped vsftp and im using SFTP thats working fine, now i added this to my command line [COLOR=#000000][FONT=Ubuntu Mono]sudo chown root:root /home/user user being me is what i added
then for the last line i have gone sudom vim /etc/sshd_config and when i hit enter it says new directory and theres nothing in it do i addthis to it then 

[/FONT][/COLOR]Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory %h
        X11Forwarding no
        ForceCommand internal-sftp

---

### Post by Lars Noodén on 2014-03-06
Close.  It's /etc/ssh/sshd_config

Be sure to make a backup copy before editing, just in case.

---

### Post by mark103 on 2014-03-06
ok im in there now i just add those lines of code u said to ? plus i dont know how to make a backup all new to me 
i appreciate all your help thanks

---

### Post by Lars Noodén on 2014-03-06
Yep.  You can make a backup like this.

```

sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig

```

Then you can edit the file, putting those lines at the end.

```

sudo vim /etc/ssh/sshd_config

```

Then you can reload the configuration for sshd.

```

sudo service ssh restart

```

Then check to make sure you can log in with your normal account with SSH and with the sftp-only account using SFTP.

---

### Post by mark103 on 2014-03-06
it wont let me in now ? using SFTP

---

### Post by mark103 on 2014-03-06
but once i take that code away u send me im back in

---

### Post by Lars Noodén on 2014-03-06
Did you have "Subsystem sftp ..." in there twice?  The first one needs to be commented out by putting a pound (#) at the beginning of the line.

---

### Post by mark103 on 2014-03-06
ok i done that i commented out the first line not your on in the edit file and my ftp works fine now thank you

---

### Post by mark103 on 2014-03-06
but my problem is now when i try to connect as my friend it wont let me in ?

---

### Post by Lars Noodén on 2014-03-06
Your friend is in the group sftponly, so the rules after the Match should apply to him.  For the chroot to work, his home directory has to be owned by root, as mentioned above.  

```

sudo chown root:root /home/friend

```

He'll still be able to write to the subdirectories, but the main home directory is not writable.  That's annoying but part of the requirements of using the built-in chroot with SFTP.

That can be undone if needed:

```

sudo chown friend:friend /home/friend

```

---

### Post by mark103 on 2014-03-06
ok i have added this [COLOR=#000000][FONT=Ubuntu Mono]sudo chown root:root /home/friend

then i can get in SFTP but cant do anything else after than i cant add files to it either [/FONT][/COLOR]

---

### Post by mark103 on 2014-03-06
Unable to change directory [permission denied]

---

### Post by mark103 on 2014-03-06
it would be great if i coud just lock him to his own directory and then i can add files to that directory

---

### Post by Lars Noodén on 2014-03-06
Yes, that's an unfortuante limitation of [SFTP chroot](http://manpages.ubuntu.com/manpages/saucy/en/man5/sshd_config.5.html).  

You can make subdirectories for him in that root-owned home-directory that he owns and can write to.  That's how Canonical does it for some of its Ubuntu sites.  They lock down the home directory and put in a single subdirectory owned by the user, the user can then work with that subdirectory completly normally.

---

### Post by mark103 on 2014-03-06
ok but i cant change directory or nothing when im logged in as him and cant transfer files across as him even if i login as me i cant getting into his folder am i missing something ?

---

### Post by Lars Noodén on 2014-03-06
Do you have a subdirectory for your friend to try to write?

```

sudo mkdir /home/friend/Files
sudo chown friend:friend /home/friend/Files

```

When logged in as yourself, you should have access to your own folders / home directory, but not his.  If you need write access you can make group and add that to the Files folder.

---

### Post by mark103 on 2014-03-06
i have to go out for a few hours but ill be online tomorrow and ill try then, kinda confused as i have tried that but doesnt work its very confusing all i want to do is let him login to my server under his username and his directory and get the files that i put there for him and he doesnt see my files thats all 

i really appreciate all your help thanks

---

### Post by mark103 on 2014-03-06
im just new to ubunut so command line is a little hard for me thats all :)

---

### Post by Lars Noodén on 2014-03-06
It's ok.  The shell takes some getting used to, but it is the least ambiguous when working over forums or e-mail.  In the long run, it is also far more powerful.  You'll feel comfortable with it.

I've been working on a spare machine and two more changes might be needed for just his directory since it is the one owned by root.

```

sudo chmod 755 /home/friend/

```

That should allow him to read the files in the directory so he can get  at the folder where he does actually have write access.

---

### Post by mark103 on 2014-03-07
got it all working thanks to you cheers for al the help :) really appreciate that

---

