---
title: "Are there any FTP servers at all for linux?"
date: 2012-10-19
forum: General Help
---

### Post by colobix on 2012-10-19
Hello.
I have been googeling this forever, and can only find crappy terminal and configuration stuff, and not an actual program.

I need to transfer larger files and was thinking of ftp.
And i don't care if the program is free or open or closed or whatever it is.

---

### Post by kc1di on 2012-10-19
> **colobix said:**
> Hello.
I have been googeling this forever, and can only find crappy terminal and configuration stuff, and not an actual program.

I need to transfer larger files and was thinking of ftp.
And i don't care if the program is free or open or closed or whatever it is.

there are several
Pureftp comes to mind the link is[ here. ]("http://www.pureftpd.org/project/pure-ftpd")

or[ vsftpd]("https://security.appspot.com/vsftpd.html")

---

### Post by Lars Noodén on 2012-10-19
There are several FTP servers available, but unless you are setting up Anonymous FTP you might look to SFTP instead.  It is easier to set up and is secure.  You get it as part of the package openssh-server, and no additional configuration is needed to use it.  On the client side you have Nautilus and Dolphin which can work with files via SFTP.

---

### Post by colobix on 2012-10-19
> **kc1di said:**
> there are several
Pureftp comes to mind the link is[ here. ]("http://www.pureftpd.org/project/pure-ftpd")

or[ vsftpd]("https://security.appspot.com/vsftpd.html")

I couldn't find a deb install file for pureftp
And vsftpd is what I meant when I said configurations and terminal stuff.
I even tried it, and it frustrated me and I couldn't get it working.
I want something easy and simple without text files and terminal stuff. A normal program.
Are there any?

---

### Post by Lars Noodén on 2012-10-19
> **colobix said:**
> I want something easy and simple without text files and terminal stuff. A normal program.
Are there any?

That would be SFTP for you.   You don't need any difficult setup because it is configured to run in OpenSSH-server out of the box.  You'll find OpenSSH-server in Synaptic or the Software Center.  And you don't need any unusual clients because support is built into your file manager, press ctrl-L to connect from inside Nautilus or Dolphin.

---

### Post by juancarlospaco on 2012-10-19
> **colobix said:**
> I couldn't find a deb install file for pureftp

I want something easy and simple without text files and terminal stuff. A normal program.
Are there any?

Its on the software center sir.

---

### Post by colobix on 2012-10-19
> **Lars Noodén said:**
> That would be SFTP for you.   You don't need any difficult setup because it is configured to run in OpenSSH-server out of the box.  You'll find OpenSSH-server in Synaptic or the Software Center.  And you don't need any unusual clients because support is built into your file manager, press ctrl-L to connect from inside Nautilus or Dolphin.
I installed it and couldn't find it in the menu.
I also tried pureftp, but couldn't find that either.

---

### Post by bootedguy on 2012-10-19
> **colobix said:**
> I installed it and couldn't find it in the menu.
I also tried pureftp, but couldn't find that either.
With Nautilus open, go to "File">"Connect to Terminal".

---

### Post by Lars Noodén on 2012-10-20
> **colobix said:**
> I installed it and couldn't find it in the menu.


Servers won't show up in any menus.  They run in the background.  If you want to see them running you can run either of the following in the terminal:

```

service ssh status
pgrep -l sshd
ps -eF| grep sshd

```

But you don't need to do that unless you want to verify that it is running.  

Connecting to the server won't show up in any menu either.  You known it's running on your machine, so use the ip number of your machine and connect in the File Manager (Nautilus) using ctrl-L.  Then enter the URI for the server, including your user name and the ip address of your machine which is running the SSH server.

sftp://colobix@*xx.yy.zz.aa*

That's it.  You should then be connected via Nautilus and can move files back and forth.  

Once you've verified that you can connect via SFTP, you can uninstall the [FTP](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)servers.  It's better to remove unneeded servers.

---

### Post by colobix on 2012-10-20
Thanks. I don't know what you mean by that though.
I want a program that'll let me access my files from somewhere lese.
I don't understand all this terminal and command and configuration stuff.
I want an easy program that I can open and from there start the ftp thing so I can access files from another pc.
Aren't there any for linux?
I looked around on winehq, but none of the suggested ones worked.

---

### Post by The Cog on 2012-10-20
Did you install openssh-server package?
If so, then you don't need to do anything else on that computer. 
It's not in a menu, it Just Works (TM).

So try connecting to it from another computer. You will need to supply a username and password to the ssh client program. What client program were you planning to use?

---

### Post by mikewhatever on 2012-10-20
> **colobix said:**
> Thanks. I don't know what you mean by that though.
I want a program that'll let me access my files from somewhere lese.
I don't understand all this terminal and command and configuration stuff.
I want an easy program that I can open and from there start the ftp thing so I can access files from another pc.
Aren't there any for linux?
I looked around on winehq, but none of the suggested ones worked.

No, I don't think so. All of them will need to be configured first.

---

### Post by Lars Noodén on 2012-10-20
> **colobix said:**
> Thanks. I don't know what you mean by that though.
I want a program that'll let me access my files from somewhere lese.
I don't understand all this terminal and command and configuration stuff.
I want an easy program that I can open and from there start the ftp thing so I can access files from another pc.
Aren't there any for linux?
I looked around on winehq, but none of the suggested ones worked.

Again, if you've installed openssh-server, then you don't need anything more on your computer.  It works as-is out of the box, giving you [SFTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  No terminal work needed.  No configuration needed.  You can even connect using GUI programs.

---

### Post by colobix on 2012-10-20
> **Lars Noodén said:**
> Again, if you've installed openssh-server, then you don't need anything more on your computer.  It works as-is out of the box, giving you [SFTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  No terminal work needed.  No configuration needed.  You can even connect using GUI programs.
Out of the box?
Then where do I chose directory to show on the internet?
And what's the address?
I know it's suppose to be my IP and the port, but which port is it?And I assume it only has read feature since it's working out of the box.

---

### Post by Lars Noodén on 2012-10-21
It is port 22, but that is the default so if you don't write anything that is the port that gets used.  

Are you using Nautilus or Dolphin to connect?

---

### Post by The Cog on 2012-10-21
> **colobix said:**
> Out of the box?
Then where do I chose directory to show on the internet?
And I assume it only has read feature since it's working out of the box.
SSH offers the whole server, with the same read/write rights as when you log in locally. So when you connect, you see /usr, /home and all the top-level folders.
I believe there is a chroot option so that you can specify a different root directory, but I've never used it.
> And what's the address??
I know it's suppose to be my IP and the port, but which port is it??
By default it listens on :::22 which means "all local IPv4 and IPv6 addresses, port 22".

The config is in /etc/ssh/sshd_config. But the defaults give you a pretty usable server, out of the box.

If you plan to expose the server to the internet, make very sure all your passwords are strong ones, for **every** user.  Actually, you can configure that only certain users can connect from certain remote addresses. And you can configure so that you need certificates to be able to connect and then disable simple password access (I do both on my public ssh server at home).

---

### Post by colobix on 2012-10-21
> **The Cog said:**
> SSH offers the whole server, with the same read/write rights as when you log in locally. So when you connect, you see /usr, /home and all the top-level folders.
I believe there is a chroot option so that you can specify a different root directory, but I've never used it.

By default it listens on :::22 which means "all local IPv4 and IPv6 addresses, port 22".

The config is in /etc/ssh/sshd_config. But the defaults give you a pretty usable server, out of the box.

If you plan to expose the server to the internet, make very sure all your passwords are strong ones, for **every** user.  Actually, you can configure that only certain users can connect from certain remote addresses. And you can configure so that you need certificates to be able to connect and then disable simple password access (I do both on my public ssh server at home).

Thanks. But I don't think this is what I'm looking for.
I tried localhost:22, but it said the site is not accessible.

I want to access my files from another computer.
And from what I've read, that is called FTP.
You know when you set up a free website you get some space to store your files. But I want to transfer larger files, so I need to use my own computer instead of a free website.
I don't want passwords or anything. I want the files to be available without having to type in a password.
Just like with those Index Of / sites if you know what I mean.

---

### Post by frncz on 2012-10-21
Have you tried filezilla? It may do wehat you need.
Regards

Mike

---

### Post by Lars Noodén on 2012-10-22
If you want them to be published without needing a password to begin the download then with FTP that is called Anonymous FTP.  However, using HTTP is much better and IMHO easier to set up using Apache or nginx.  Install either one and just drag the files to /var/www and they are published.

---

### Post by coldraven on 2012-10-22
> **frncz said:**
> Have you tried filezilla? It may do wehat you need.
Regards

Mike

+1 for Filezilla

---

### Post by Paqman on 2012-10-22
> **colobix said:**
> 
I want to access my files from another computer.
And from what I've read, that is called FTP.


FTP is one way of doing that, but there's plenty of others. Have you looked at Ubuntu One? It's preinstalled on your Ubuntu Machines and you can install it on Windows ones too. It syncs everything in your Ubuntu One folder between all the machines. No passwords required, just drop the file into the folder and it'll sync to the other machine automatically. You get 5GB of storage for free, which should be fine for most stuff.

---

### Post by colobix on 2012-10-22
> **coldraven said:**
> +1 for Filezilla

Isn't that just an ftp client?

> **Paqman said:**
> FTP is one way of doing that, but there's plenty of others. Have you looked at Ubuntu One? It's preinstalled on your Ubuntu Machines and you can install it on Windows ones too. It syncs everything in your Ubuntu One folder between all the machines. No passwords required, just drop the file into the folder and it'll sync to the other machine automatically. You get 5GB of storage for free, which should be fine for most stuff.

With ubuntu one I have to upload the files first, plus they have a 5 gig limit or so.
I really don't wanna hassle around with that. Sounds like a waste of money just to export files over.


> **Lars Noodén said:**
> If you want them to be published without needing a password to begin the download then with FTP that is called Anonymous FTP.  However, using HTTP is much better and IMHO easier to set up using Apache or nginx.  Install either one and just drag the files to /var/www and they are published.

Thanks. That sounds like something I'm looking for, yes.
I installed nginx. The other one wasn't there.
Now, what's the address? I assume it's localhost:port, but what's the port?
And where do I configure it to be enabled/disabled and stuff like that?

---

### Post by Lars Noodén on 2012-10-22
FileZilla also supports SFTP.  That is more important. 

About nginx, it serves up your files on port 80 or 443.  But that is the default for the web so if you are using a regular web browser, you do not need to enter anything other than the address.  If you are connecting locally, that might be localhost.  But if you are sharing with others, then you will have to use your external ip address.  Depending on your network setup you might also have to forward ports 80 and 443 from your router/modem to your internal machine.

---

### Post by mexlinux on 2012-10-22
Colobix:
FTP is obsolete insecure technollogy, as they recommend SFTP is the way to go, and it installs as they say with openssh-server and thats it, you can directly access with any sftp client to your IP with your local username/password.

If using a server seems too complicated, can you simply use [Dropbox]("http://db.tt/0pl99Wq")?

---

### Post by colobix on 2012-10-22
> **Lars Noodén said:**
> FileZilla also supports SFTP.  That is more important. 

About nginx, it serves up your files on port 80 or 443.  But that is the default for the web so if you are using a regular web browser, you do not need to enter anything other than the address.  If you are connecting locally, that might be localhost.  But if you are sharing with others, then you will have to use your external ip address.  Depending on your network setup you might also have to forward ports 80 and 443 from your router/modem to your internal machine.

Dude. Please stop confusing. Filezilla is a client, not a server.

Anyway, how do I configure nginx?
What will the address for my files be?
I'm assuming it's localhost or something, because now it says "it works".
And nginx wasn't a program either. At least it didn't show up in the start menu.
So, should I try Apache instead?
I installed that too, but none of them appear in the menu.

Any help please?

EDIT: It works when I type in localhost, but not when I type in my ip address.

---

### Post by colobix on 2012-10-22
Okay. So so I found out that the localhost is 127.0.0.1, but how do I put this on the internet so I can access it from another pc?

---

### Post by Lars Noodén on 2012-10-26
> **colobix said:**
> Okay. So so I found out that the localhost is 127.0.0.1, but how do I put this on the internet so I can access it from another pc?

You will need to forward ports from your router and external IP address to the internal address, assuming you are hooked up with the usual home set up.

If you are making SFTP available, that means forwarding port 22.  If you are making WWW services available that means forwarding ports 80 and 443.  The exact method of forwarding varies depending the make and model of your router.

If you are only talking about accessing from another PC on the same LAN, then you do not need to forward any ports, just connect to that PCs ip address.  You can find it with ifconfig in the terminal or graphically in System Settings-> Network

---

### Post by colobix on 2012-10-26
> **Lars Noodén said:**
> You will need to forward ports from your router and external IP address to the internal address, assuming you are hooked up with the usual home set up.

If you are making SFTP available, that means forwarding port 22.  If you are making WWW services available that means forwarding ports 80 and 443.  The exact method of forwarding varies depending the make and model of your router.

If you are only talking about accessing from another PC on the same LAN, then you do not need to forward any ports, just connect to that PCs ip address.  You can find it with ifconfig in the terminal or graphically in System Settings-> Network
It's in the same house if that's what you mean by lan.
The command you posted gave me a bunch of ip addresses.
This one worked on the same pc 192.168.40.255, but not the other pc. Was that the right ip? The other ips didn't work
Any suggestion?

---

### Post by Lars Noodén on 2012-10-26
> **colobix said:**
> It's in the same house if that's what you mean by lan.
The command you posted gave me a bunch of ip addresses.
This one worked on the same pc 192.168.40.255, but not the other pc. Was that the right ip? The other ips didn't work
Any suggestion?

Yes, you probably have only one LAN in your house.

You can find the ip number of the machine by going to System Settings->Network in the GUI.  Or you can go into the terminal and entering the following:

```

ifconfig eth0 | awk '$1 == "inet" {print substr($2,6)}'

```

Then you can go to the other machines and try connecting to that address with your SFTP client (Nautilus or Dolphin) or your web client (Firefox or Chromium).

That will give you the internal (LAN) address.  If you want to access from outside your house you will have to set up port forwarding on your router.

---

### Post by colobix on 2012-10-26
> **Lars Noodén said:**
> Yes, you probably have only one LAN in your house.

You can find the ip number of the machine by going to System Settings->Network in the GUI.  Or you can go into the terminal and entering the following:

```

ifconfig eth0 | awk '$1 == "inet" {print substr($2,6)}'

```

Then you can go to the other machines and try connecting to that address with your SFTP client (Nautilus or Dolphin) or your web client (Firefox or Chromium).

That will give you the internal (LAN) address.  If you want to access from outside your house you will have to set up port forwarding on your router.

Thanks. But that ip didn't work either. It worked from this pc though.
How do I do the router thing?

---

### Post by qamelian on 2012-10-26
> **colobix said:**
> Dude. Please stop confusing. Filezilla is a client, not a server.

Anyway, how do I configure nginx?
What will the address for my files be?
I'm assuming it's localhost or something, because now it says "it works".
And nginx wasn't a program either. At least it didn't show up in the start menu.
So, should I try Apache instead?
I installed that too, but none of them appear in the menu.

Any help please?

EDIT: It works when I type in localhost, but not when I type in my ip address.
Slightly O/T: Filezilla also produces an FTP server, but it is Windows-only. The link to the Filezilla FTP server is right on their front page. :)
[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by Lars Noodén on 2012-10-26
> **colobix said:**
> Thanks. But that ip didn't work either. It worked from this pc though.
How do I do the router thing?

The router specifics depends on the make and model.  But first step is to get things working on your LAN.  On your server, what is the status of your SSH server?

```

service ssh status

```

If you have a firewall active on that machine, you will have to open port 22 for SSH/SFTP.

```

sudo ufw allow ssh

```

Then on another machine on the same LAN what kind of error are you getting when you try to connect to the server via the terminal's SFTP client?  (Substitute your server's ip.)

```

sftp colobix@*xx.yy.zz.aa*
sftp -v colobix@*xx.yy.zz.aa*

```

---

### Post by colobix on 2012-10-26
> **Lars Noodén said:**
> The router specifics depends on the make and model.  But first step is to get things working on your LAN.  On your server, what is the status of your SSH server?

```

service ssh status

```

If you have a firewall active on that machine, you will have to open port 22 for SSH/SFTP.

```

sudo ufw allow ssh

```

Then on another machine on the same LAN what kind of error are you getting when you try to connect to the server via the terminal's SFTP client?  (Substitute your server's ip.)

```

sftp colobix@*xx.yy.zz.aa*
sftp -v colobix@*xx.yy.zz.aa*

```

Thanks. I've opened the port for ssh, so maybe it'll work now.

ssh service status said   ssh stop/waiting.

Thanks for the filezilla server tip, but I'm not using windows.
The reason why I use ubuntu is because my school had to stop using windows software due to low budget and such.
And now we need to use ubuntu at home because they want us to use the same software and everything. It really sucks:(
I'm sorry. I know a lot of you people love ubuntu, but I find it rather frustrating.

Anyway, when I type in my ip address, I still get the thomson gateway website.

---

### Post by Lars Noodén on 2012-10-27
> **colobix said:**
> 
ssh service status said   ssh stop/waiting.


If that's on the machine you are trying to connect ***to*** then something is wrong.  sshd does need to be running for you to connect to it.

```

sudo service ssh start

```

---

### Post by colobix on 2012-10-27
> **Lars Noodén said:**
> If that's on the machine you are trying to connect ***to*** then something is wrong.  sshd does need to be running for you to connect to it.

```

sudo service ssh start

```
The service is already running.
But the machine I'm trying to connect to doesn't have a terminal.
It's an ipad.
Anyway. The ip address is still my modem's administration site

---

