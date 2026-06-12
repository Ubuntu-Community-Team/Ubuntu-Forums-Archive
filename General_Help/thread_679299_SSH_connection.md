---
title: "SSH connection"
date: 2008-01-26
forum: General Help
---

### Post by Driagan on 2008-01-26
Hello, I have searched and have not found a solution to what I am looking for. So I thought I would post a new topic.

I would like a way to connect to my server computer via SSH (or some other encrypted connection) where I can relay web requests. I mean, use it as a proxy server. I would like to have an encrypted connection to it that I would be able to use anywhere (like when I am connected to a public wireless network) so that I do not send any unencrypted information over an unsecured network (e.g. usernames, passwords, forum posts, etc.) This information would be sent over an encrypted connection to my server which will then send out the normal (unencrypted) requests to the web, then send the results back to me, encrypted. This would allow me to surf the web almost as secure as if I were just sitting at home, at my server computer.

I would also like to be able to do this from a Windows computer (I can already do this from a Linux one with the "ssh" command (using what is described on [LifeHacker](http://lifehacker.com/software/ssh/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy-237227.php),) and without installing any software (I would like to have whatever program is required to be able to be ran from my USB flash drive, as I would most likely be using this while I am away from my home computer, where I would have had software installed.)

My server already has the ability to be connected to with SSH (I use PuTTY all the time to access it over SSH.) 

If anyone knows any programs that would allow me to do this, I would really appreciate it :)

---

### Post by heypete on 2008-01-26
Putty should be able to do precisely what you want; no need for extra software. Though if you're using a USB flash drive, you might want to get [Putty Portable]("http://portableapps.com/apps/internet/putty_portable").

According to [http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-port-forwarding](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-port-forwarding), this might be helpful:

> An alternative way to forward local connections to remote hosts is to use dynamic SOCKS proxying. For this, you will need to select the ‘Dynamic’ radio button instead of ‘Local’, and then you should not enter anything into the ‘Destination’ box (it will be ignored). This will cause PuTTY to listen on the port you have specified, and provide a SOCKS proxy service to any programs which connect to that port. So, in particular, you can forward other PuTTY connections through it by setting up the Proxy control panel (see [section 4.15]("http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter4.html#config-proxy") for details).

Once you have Putty set to forward the dyanmic port, then just configure your browser to use a SOCKS proxy on "localhost" on whatever port you chose in Putty.

Hopefully this is helpful.

Cheers!
-Pete

---

### Post by fyo on 2008-01-26
If I understand you correctly, what you want is an SSH tunnel from an remote system to a web proxy on your home server. That would allow you to just point the web browser on the remote system to the remote end of the SSH tunnel, e.g. 127.0.0.1:8080.

I think pretty much any SSH software, including Putty, will accomplish this. All you need to do is set up a web proxy on your home server and then establish the SSH tunnel.

---

### Post by Driagan on 2008-01-26
Yes, thank you. That link had exactly the information I was looking for on it. I did not know that PuTTY had the ability to forward ports.

---

### Post by heypete on 2008-01-26
My pleasure. Glad to be of assistance. Surf safely.

---

