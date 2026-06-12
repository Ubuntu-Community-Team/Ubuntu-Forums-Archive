---
title: "ssh remote control"
date: 2013-01-30
forum: General Help
---

### Post by Quarkrad on 2013-01-30
Two remote machines - both running 12.04.  Most of the documentation goes through configuration etc but I'm struggling on what you use/launch to actually use remote control.  I've installed openssh on the remote host and installed Putty on my client machine.  (I believe I have openssh client already installed by default but what/where is it?).  Anyway, I have a long way to go but I'm trying to set up a basic connection.  I have created on my client machine a passphrase and got a key finger print but I do not know what to do now.  I launched Putty on my client (installed Putty becuase I do not know what the default ssh client is) and entered the ip of the remote host - all I got was a black screen and nothing else.  I was expecting to see the remote desktop and be able to control the cursor or even something asking me for a password/the passphrase.  I haven't got it set up properly but what do I launch on my desktop to use this ssh remote connection?  (Up to now I have been using a product called Teamviewer which has set my expectation level.  It would be nice to see in all the documentation around some screens afterwards so you can see what you have to do and what it looks like).  Apologies if this a stupid question.

---

### Post by omeomi on 2013-01-30
To use ssh in Ubuntu you can just run 'ssh' in the terminal, as so:
```
$ ssh user@remote-address
```

When you login over ssh you will just get the command line, not a desktop (although it is possible). 

For actual remote desktop you can use VNC.

---

### Post by Quarkrad on 2013-01-30
Ah - I've got this completely wrong.  My goal is to set up hostname on the remote becuase they have a dynamic ip, so am I right in thinking that ssh sets up the baisc secure connection and then I use something like, as you say, vnc to see the desktop?  So would I launch/use Putty to establish the connection and then something like VNC to actually see and use the remote control?

---

### Post by omeomi on 2013-01-30
You don't need Putty in Ubuntu because you can just use the terminal. (unless you are using a windows client but I didn't get that from your story)

Have a look at this: [https://help.ubuntu.com/community/SSH]("https://help.ubuntu.com/community/SSH") and this [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by prodigy_ on 2013-01-30
> **Quarkrad said:**
> I launched Putty on my client (installed Putty becuase I do not know what the default ssh client is) and entered the ip of the remote host - all I got was a black screen and nothing else.  I was expecting to see the remote desktop and be able to control the cursor or even something asking me for a password/the passphrase.
You seem to be a bit confused here.

First, like **omeomi** said, you don't need putty in Ubuntu, it comes with a native ssh client - just open terminal and type **man ssh** to learn more.

Second, SSH will not allow you to see GUI desktop on the remote machine. For that you'd need RDP or VNC. SSH is strictly command line.

Third, to troubleshoot your SSH connection, you can use the ```
netstat -atun|grep ':22 '
``` command on the server (if it outputs nothing, the SSH server isn't running) and **telnet** command on the client. Assuming port 22 (the default) and SSH server IP 192.168.0.1 the command would be: ```
telnet 192.168.0.1 22
```

---

### Post by steeldriver on 2013-01-30
If the server and client are both using Ubuntu 12.04 Desktop edition, you can simply enable 'Desktop Sharing' on the server via the settings GUI and then use any VNC client e.g. remmina on the client

IIRC it gives you the option to tunnel the actual VNC connection via SSH if you want extra security (IMO you *should* do that if you are connecting the machines via a public network, but it's not necessary if you are connecting on a private LAN behind a suitable router / NAT firewall). 

Or you *could* manually set up the VNC tunnel via ssh - you are not wrong about that (I'm running a VNC desktop session on a remote machine for my work that way right now)

---

