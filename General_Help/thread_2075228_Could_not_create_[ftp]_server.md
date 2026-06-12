---
title: "Could not create [ftp] server"
date: 2012-10-23
forum: General Help
---

### Post by Wampyra on 2012-10-23
Hey ubuntu lovers!

Here I am again with a new problem.

I want to setup a simple ftp server to share the files with authenticated user[s].

Problem is that whichever ftp service i install i always get the same errors. 
```
critical error
could not connect to server
```

It was working for one whole day and then I added Webmin. After that, something changed. Wish I knew what.

Do you have any suggestions?

I was going through all the forum posts that i could find on this topic [there are soooo many.....] but nothing seams to work for me.

P.S. I hope that posting the question will make me figure it out somehow, as that's what usually happens anyhow...

---

### Post by Wampyra on 2012-10-23
I removed everything [proftpd, vsftpd, webmin, samba, everythign i was experimenting with]
Now I tried with "simplest" solution - vsftpd. Except that it seams that it's not simple for me.
Now I get 530 Login incorrect 
Argh...

Keep trying - I know

BTW, Lovely talking to myself... :popcorn:

---

### Post by Wampyra on 2012-10-23
530 Login incorrect ?!

How can it be? Not even anonymous is working :confused:

---

### Post by Lars Noodén on 2012-10-23
The simplest solution to create a server to share the files with authenticated users would be SFTP.  So I'm going to recommend SFTP.  It's a built-in part of the package [OpenSSH-server](apt:openssh-server), which you probably already have installed, and needs no additional configuration.  

You can connect to it using Nautilus or Dolphin.  Press ctrl-L and then enter the URI for the server:  sftp://wampyra@*xx.yy.zz.aa*/~

As far as FTP goes, there are other disadvantages besides being hard to set up.

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

---

### Post by Wampyra on 2012-10-23
> **Lars Noodén said:**
> TSo I'm going to recommend SFTP.

YES YES YES! 
:KS

I'm IN! Although I had to download and install ssh-server...

Now I wonder how to make a user that would be in control of only one directory where he can party or whatever...
Any suggestions...

I'm so close to resolving this...

---

### Post by Wim Sturkenboom on 2012-10-23
What you're looking for is a *chroot jail*. Do a search, I don't know how to do it with SSH (it used to be a mission).

---

### Post by Lars Noodén on 2012-10-23
> **Wampyra said:**
> Now I wonder how to make a user that would be in control of only one directory where he can party or whatever...

Well, any users will have write access to their home directory, if nothing has changed. 

If you want to lock them down to only reading one directory that can be done if you modify the ssh server's configuration file.  You can [chroot](https://help.ubuntu.com/community/BasicChroot) users belonging to a certain group.  The only drawback to this method is that the chroot directory does have to be owned by root and not writable by anyone else.  The way around that is that the subdirectories have no such restriction.

Even though the process is very simple, there are tons of tutorials and howtos around.  In short, to chroot the users in the group sftponly substitute/add the following lines to /etc/ssh/sshd_config

```

Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory %h
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

What that does is forces them into SFTP, disabling the shell for them (ForceCommand).  And it locks them into their home directory and its subdirectories (ChrootDirectory).  Again, their home directory must be owned by root and not writable by others.  The subdirectories can be still owned by the users.

If you just want to lock them into SFTP but not worry about chroot, then just remove the line with ChrootDirectory.

---

### Post by Wampyra on 2012-10-29
For some reason I can't access ftp anymore. It seams like it's randomly working / or not.

I wish there was an easy way to fix this...

I'm not even thinking about jailing users anymore

---

