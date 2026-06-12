---
title: "SSH tunnel, SOCKS 5"
date: 2015-01-21
forum: General Help
---

### Post by dan138 on 2015-01-21
I have an Ubuntu server and sometimes I create a SSH tunnel from my local computer and then set the SOCKS 5 settings in my browser so that I can surf the net securely (like when I connect using a WiFi hotspot that I don't own.

Anyhow, I'd like to give a few of my (non technical) friends the ability to do it with my server. What would be the best way?

---

### Post by Holger_Gehrke on 2015-01-21
Are you asking how to set this up client side so they can do it without to much trouble for them ? That's different depending on their OS's and client software.
Or do you want to know how to secure your server against their mistakes / wannabe hacking attempts ? For this a search for "ssh user only tunnel" leads -- among other stuff -- to two highly relevant thread at stackexchange :
 [http://unix.stackexchange.com/questions/14312/how-to-restrict-an-ssh-user-to-only-allow-ssh-tunneling](http://unix.stackexchange.com/questions/14312/how-to-restrict-an-ssh-user-to-only-allow-ssh-tunneling)
[http://stackoverflow.com/questions/8021/allow-user-to-set-up-an-ssh-tunnel-but-nothing-else](http://stackoverflow.com/questions/8021/allow-user-to-set-up-an-ssh-tunnel-but-nothing-else)

---

### Post by dan138 on 2015-01-21
> **Holger_Gehrke said:**
> Are you asking how to set this up client side so they can do it without to much trouble for them ? That's different depending on their OS's and client software. 

Yes. I only need www not all network connections. Lets just assume they (my friends) have Firefox and I can can tell them how to get to the "Configure Proxies to Connect to the Internet" settings page. I'd like to give them an IP and port number like I use for SOCKS 5.  It would probably be a good idea to also give them a PW as well?   They will not be able to use a shell or make a SSH connection to my server.

---

### Post by Holger_Gehrke on 2015-01-21
I wouldn't use a password, I'd use a keypair and set up login through public keys. They'd also need to run ssh in the background before starting firefox to set up the tunnel. If I was you, I'd write a short script to start ssh with the key and open the tunnel and then start firefox with a separate profile (see the manual page for firefox on how to do this, especially the option -P *profilename* and -ProfileManager ) , in which the socks setting is set up right. This way, they get a clean firefox and don't need to change their configuration all the time. They'd have two configurations one with the tunnel and one without. If they are on window, the same can be done with a bat or cmd file and using Putty.

---

### Post by dan138 on 2015-01-21
> **Holger_Gehrke said:**
> I wouldn't use a password, I'd use a keypair and set up login through public keys. They'd also need to run ssh in the background before starting firefox to set up the tunnel. If I was you, I'd write a short script to start ssh with the key and open the tunnel and then start firefox with a separate profile (see the manual page for firefox on how to do this, especially the option -P *profilename* and -ProfileManager ) , in which the socks setting is set up right. This way, they get a clean firefox and don't need to change their configuration all the time. They'd have two configurations one with the tunnel and one without. If they are on window, the same can be done with a bat or cmd file and using Putty.

That would work with friend A. Friend B is at work and wants to use Facebook which is blocked. It's not really a good option for her to run a script or have Putty installed. I'm not that concerned with the server it's just a VM at DigitalOcean. I have several.  My motivation is just to learn more. 

If I did something like this on the server[PHP]SSH -f -D 1080 localhost[/PHP] that would open up a port on the server than anyone could use? How can I use a PW? (this would also be a good time to try out Fail2Ban.)

---

### Post by QIII on 2015-01-21
Friend A is covered.

If Friend B is blocked at work, we won't help you figure out how to circumvent his/her employer's block on getting to Facebook even as an academic exercise.

Don't go there, or the thread will be closed.

---

### Post by dan138 on 2015-01-22
Wow. Sorry. Am I allowed to talk about Tor if I want to help a friend in China?

---

### Post by Holger_Gehrke on 2015-01-22
You **need** to run ssh on the client to tunnel. The browser doesn't know a think about ssh. It sends it's request to a local port (which the ssh client listens on). The ssh client 'talks' to the server, the server does it's thing and delivers a response to the ssh-client that passes it back to the browser. So if  friend B can't run a ssh client, she is up the creek without a paddle  and will have to wait until she gets home to get her facebook fix. Plus  circumventing a block at work would be a violation of the contract she  signed when she took the job and could get her fired.

---

### Post by dan138 on 2015-01-22
Dude, she would like to get fired, they need her way more than she needs them, and she can't seem to say "no" . . She sits in her office and surfs FB on her iPad's cell connection. Nobody give a sh** and she didn't sign a contract. Anyhow, I don't want to get banned so I'll figure this out some other way.

---

