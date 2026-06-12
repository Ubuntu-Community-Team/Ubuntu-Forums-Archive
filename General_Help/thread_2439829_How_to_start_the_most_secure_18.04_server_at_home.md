---
title: "How to start the most secure 18.04 server at home"
date: 2020-04-02
forum: General Help
---

### Post by marina92 on 2020-04-02
Hello everyone,

I’m planning to start a home 18.04 Ubuntu server at home. Considering that I don’t need remote access to it, I want to get the maximum level of security on it to avoid any hacker taking control. So, investigating, seems like to get that I should:

 1. Ensure that my router has disabled inbound connections
 2. Disable totally SSH service for all users 

Is that right? 

Doing that it would be almost impossible for something on the internet to access my server?

Some people said me to not disable SSH, but if I’m sure I don’t need remote access because I always have physical access to the server, why take the risk? I prefer to close that potential door to gain more security.

Not sure neither about how I interact with the server locally. I mean. I have already setup DigitalOcean servers and I know that to securely login in them I can use SSH keys. But in case of my local server with SAH disabled, I still have to enable a password for root user right? And I guess the only option is to use simple passwords and there is no other way or hardware to secure the access?

Thanks a lot

---

### Post by mastablasta on 2020-04-02
there is plenty of lists regarding hardening out there like this one for example: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)

how will you access the server form other computers? if physical access means that server has keyboard and it's own monitor, then yes you do not need SSH. why would you even install it if you do nto need it? otherwise you can also install it and just keep the doors closed (e.g. using UFW), so that only LAN user can access it.

however i use sFTP to access server from other PCs for file transfer. it uses keys+passwords to connect to server and fail2ban is setup to discourage hackers. 



most important from the usage point and how to secure it is to first define what the server will be used for. if this is only for testing then using something like virtualbox is easier and faster. is it a website server? is it some data server? is it a backup server? is it a media server?  what kind of services will run on server?

---

### Post by TheFu on 2020-04-02
I&#8217;m confused.
What is the point of having a server if nobody can access it from anywhere?

it is one thing to block internet access, but is a completely different thing to block access from the LAN.  SSH using keys is probably the most secure network protocol.  Don't allow passwords and it is virtually impossible for anyone to connect.  Don't have the "server" on the same subnet as high-risk devices.  So if you have any iot stuff, put that somewhere else on a different subnet.  Especially any listening devices or always connect things like a thermostat. Those things belong on a guest network.

i prefer to access my LAN servers from a more comfortable workstation running X11 with lots of terminal windows, access to a browser, access to my notes about setting things up, etc.  A server just has a few consoles, which makes select/paste impossible.

No, root should not be enabled.  You can setup 2FA for your logins using something like a yubikey, but why bother if you don't allow any remote access?

if you want a secure system, get automatic, daily, versioned, backups working ASAP.  Have them "pulled" by another system over the network, not local storage, and encrypt the backup storage.  May want to encrypt the server storage too, if you don't plan to leave it powered all the time.

imho.

---

### Post by QIII on 2020-04-02
Perhaps you should describe to us what you think a server is.

---

### Post by HermanAB on 2020-04-03
Well, what do you want to serve:
Anonymous FTP, CIFS, NFS, Streaming Music, Streaming Video, Mail, Spam?

Serving up Spam is the easiest, just put the machine online and wait a while.

---

