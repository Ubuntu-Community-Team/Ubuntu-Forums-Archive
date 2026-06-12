---
title: "Can I copy file from a machine to my local PC"
date: 2014-08-20
forum: General Help
---

### Post by chase7 on 2014-08-20
Hello everyone. Before i ask my question i wanted to say i am still pretty new to ubuntu and Linux as a whole.

Alright i have purchased a dedicated server from a hosting company to run game server on and i have created a cron job that will make a .zip copy of my servers and then move that to another directory whilst adding a date code to the file name. It should then remove any files that are older then 10 days.

```
@daily zip -r servers.zip /home/game/servers && mv /root/servers.zip  /home/servers/servers-$(date "+%b_%d_%Y").zip && find /home/servers* -mtime +10 -exec rm {} \;

```

However i would like to add to this and make a copy on my PC running Windows 7 as well.

I know you can do this using scp. 

Now my question is to do this do i need to create a FTP server on my machine or have an open port or how would i do this?

Any input and suggestions would be awesome thanks in advance.

---

### Post by ian-weisser on 2014-08-20
> **chase7 said:**
> do i need to create a FTP server on my machine

Not FTP.
The machine you are connecting FROM (the client) needs to have openssh-client install. Happily, all flavors of Ubuntu except Minimal include this package with the default install.
The machine you are connecting TO (the server) needs to have an ssh server installed. In Ubuntu, this software is provided by the openssh-server package, which is not included in the default install but is merely a Software Center click away.

 > **chase7 said:**
> or have an open port or how would i do this?

The client need open nothing.
The server needs an open port (usually 22) in the firewall. SSH server needs to be running. You need an account on the server to log into.
If the server faces the internet, additional security (ssh keys and other measures) are *most strongly* recommended.

Then, on the client, run the desired scp command.

At great trove of information for beginners is at [https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)

---

### Post by chase7 on 2014-08-21
So in other words i need something like this on my windows computer

[http://www.worldgoneweb.com/2011/installing-openssh-on-windows-7/](http://www.worldgoneweb.com/2011/installing-openssh-on-windows-7/)

---

### Post by ian-weisser on 2014-08-21
Yes.

---

### Post by chase7 on 2014-08-21
Ill try this when I get some free time.

Will I be able to automate this process or will it need to be a manual thing each time?

---

### Post by steeldriver on 2014-08-21
I guess if you don't want to run an SSH server on the Windows box, you could run a "scheduled task" (kind of the Windows equivalent of a cronjob) to *pull* the file from your server using PuTTY's pscp (or psftp) utility

---

### Post by chase7 on 2014-08-21
I'm not picky whatever Is easiest to accomplish. I'm all about set it and forget it as well a doing things as easy as possible.

---

### Post by chase7 on 2014-08-21
I am having trouble with the ssh client.

According to this [http://www.worldgoneweb.com/2011/installing-openssh-on-windows-7/](http://www.worldgoneweb.com/2011/installing-openssh-on-windows-7/) i need to do type "mkgroup -l >> ..\etc\group" however when i do i get this "The system cannot find the path specified." 

I am in the correct drive and CD F:\OpenSSH\bin

---

### Post by chase7 on 2014-08-21
Found my issue. I only installed the client version

---

### Post by chase7 on 2014-08-21
Ok so i set the home server up and tried a scp command on the hosted server and it returns a Connection time out.

I thought this might be because of the password so i tried sshpass with the same scp and still get the same issue.

Could it be because my home server is not allowing it to connect? And is their a log i could look at to determine the problem?

---

### Post by ian-weisser on 2014-08-22
Is the ssh server software running?
Is there an account on the server for you to log in to?
If the server firewall open on the appropriate port (usually port 22)?
Don't worry about scp yet. Can you simply login to the server using ssh?

---

### Post by chase7 on 2014-08-22
Yrs I have no issues logging into the ssh server. However I'm loving unity the server using putty on the same machine

---

### Post by steeldriver on 2014-08-22
I really think you should reconsider using a 'pull' technique (i.e. use a scripted scp **client** on your Windows box to grab the file off your linux **server**)  - that way only the linux box needs to run an SSH service, only the  linux box needs an open listening port, you only need a static public IP  (or dynamic DNS updater) for the server side, no need to forward incoming ports on your home router yada yada

---

### Post by chase7 on 2014-08-22
> **chase7 said:**
> Yrs I have no issues logging into the ssh server.  However I'm loving unity the server using putty on the same  machine


Wow, sorry guys that was horrible and what i get for posting from my phone at work.

I am able to log into my SSH server (on my PC) using putty on my PC as well as thru ConnectBot using my phone. 

> **steeldriver said:**
> I really think you should reconsider using a 'pull' technique (i.e. use a scripted scp **client** on your Windows box to grab the file off your linux **server**)  - that way only the linux box needs to run an SSH service, only the  linux box needs an open listening port, you only need a static public IP  (or dynamic DNS updater) for the server side, no need to forward incoming ports on your home router yada yada

This is why I came here because I know very little about this sort of thing. Linux in general has been kicking my but the last couple of days. 

Even my cronjob was a pain to get working however its now working but i still need to try and get the removal of old files working correctly.

---

