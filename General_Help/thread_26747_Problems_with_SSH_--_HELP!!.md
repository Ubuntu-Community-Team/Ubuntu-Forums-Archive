---
title: "Problems with SSH -- HELP!!"
date: 2005-04-13
forum: General Help
---

### Post by crazybill on 2005-04-13
I am not able to use putty or WinSCP from a windows computer to log onto my Ubuntu5.04 Linux machine via SSH on port 22.  The programs crash from any computer on my network when the login attempts.

I have had no probelms logging onto my FreeBSD and OpenBSD servers.
I have tried logging in directly as root and with a username that I formed.
Yes, I used the correct password and  gave the user sudo privilidges.
Yes,  I installed ssh on the machine and the csh shell.
Yes, I placed /bin/csh as the users login shell.
Yes, I checked to see if SSH is running and it is.
Yes, I rebooted the machine and checked if all was still set up  as above: it was.

After updating and upgrading
I installed ssh with apt-get install ssh
I installed csh with apt=get install csh

The Ubuntu5.04 machine's IP address pings back and the server shows up in SAMBA.  I can open the /home/username folder in SMB.

However, when I ssh to it with putty, the login screen shows up.. but after putting in username and password, it closes down with error.
WindSCP will also not open. 

Help anyone?

---

### Post by dataw0lf on 2005-04-13
You have installed the openssh-server package, correct?

---

### Post by az on 2005-04-13
"I have tried logging in directly as root and with a username that I formed."

You mean logging in as your user, right?

---

### Post by crazybill on 2005-04-13
That is affirmative to both datawOLF and AZZ.

**_DETAILS_** 
Yes, the SSH server seems to be set up ok.
I set up the SSH server with **apt-get install ssh**
The process is running on the server.
When I run **top**  or **ps aux**  it shows sshd running in /usr/sbin/sshd

I made no changes to the default config files at **/etc/ssh/ssh_config      /etc/ssh/sshd_config** 

I restarted **/etc/init.d/ssh**  several times and it showed the process stopping and starting and again the **top**  and **ps aux**  commands show the ssh daemon running.

Indeed when I putty into the server,  the login command appears.. but then upon entering the password, putty generates errors and closes.  This is not an error in Windows because the putty program can log into other ssh servers. I also tried logging in from several computers and they all gave the same results.

When I try logging in with WinSCP, I get the error mesage:*PUBLIC KEY PACKET NOT RECEIVED* 

The initial shell of my user was /bin/bash. I prefer the /bin/csh shell, but I noticed there was no shell at that location after initial setup of Hoary Hedgehog Linux. Thus I installed csh  with **apt-get install csh** and changed the user's shell to /bin/csh. I rebooted the computer and again checked the user shell. It showed /bin/csh still as the user's shell

I did not install the csh shell until after setup of Ubuntu 5.04 . I noticed that a chosice of shells was /bin/csh but there was no shell present. Hense, I installed csh with  **apt-get install csh** . Then I changed the shell of my user. I would not think that would be a big thing. I am just giving all of the facts.. so if anyone out there has a solution or an idea of why I can not log onto SSH.

By the way, I know that most errors of this type are trivial user mistakes, and I know that  the username and password is case sensitive and the correct username and password was entered many times... all with the same negative results.  I am hoping that I will wake up tomorrow and see the dumb thing that was not done... but if any of you can speed up the process for me, that would be great.

And, yes, I know that SSH uses port 22 and the default settings in  /etc/ssh/sshd_config confirm that. I was attempting log-in with both putty and WinSCP in port 22.

Again, my problem in connecting to the Ubuntu5.04 server  is not a network problem because I can ping to it and obtain a reply. In addition,  I can connect with the computer via SMB (samba).  I also installed vsftpd and can read and write by  ftp to the server without any problem..

However, I prefer SSH to FTP, so I hope there is a solution. Thanks for any help that anyone can give.

---

### Post by kulti on 2005-04-14
Hi crazybill,

I had the same problem you discribed above and I found a solution.
Try this:

1. vi /etc/ssh/sshd_config
2. change 'PasswordAuthentication' to 'yes'
3. save
4. /etc/init.d/ssh restart

Now you should be able to login via putty :)

Does it work?

greetz,
kulti

---

### Post by crazybill on 2005-04-15
I had finally figured that out after trying going between ssh and ssh2, etc. It is usually the simple things! What you wrote, though, was exactly what I finally did to make it work. Thanks for replying!

---

### Post by crazybill on 2005-04-24
Kulti,

Changing the /etc/ssh/sshd_config file configuration from 

PasswordAuthentication no

to

PasswordAuthentication yes

which is OK for a private network... but I want to eventually put some Ubuntu machines on our public IP network.

The problem was actually not with the Ubuntu Linux out-of-the-box setup but with older versions of putty/winSCP or atleast defaulty configurations of those programs. By downloading the newest versions of putty and WinSCP, I was able to get all of the computers on my network to log onto the Ubuntu servers, even keeping

PasswordAuthentication no

---

