---
title: "Apache on the network"
date: 2006-07-10
forum: General Help
---

### Post by Ubuntuud on 2006-07-10
Hi,
I have a network.
And I have an apache2 server.

Is it possible to put the apache server on that network? I have absolutely no experience with this. But I just want to try it out.

Thanks in advance!

---

### Post by scxtt on 2006-07-10
yes, it's possible ... probably just as easy as dropping your currently configured apache2 box right in the network (i.e. plugging it in to the router) ... then you can type its IP into a browser on any box in the network to see its hosted files ...

if you want it visible from the outside, just forward port 80 to its IP address ...

---

### Post by Ubuntuud on 2006-07-11
OK. Thank you!

---

### Post by Ubuntuud on 2006-07-11
Uhm, this may sound stupid. But where is the username and password stored? When I enter my IP on my dad's (windows) PC, it asks for it... And is there a way to disable it? Thanks in advance!

---

### Post by mlind on 2006-07-11
> **Ubuntuud said:**
> Uhm, this may sound stupid. But where is the username and password stored? When I enter my IP on my dad's (windows) PC, it asks for it... And is there a way to disable it? Thanks in advance!

Are you trying to nework/samba here or to access Apache webserver, which is listening port 80 by default ([http://your.ip.here](http://your.ip.here)) ?

---

### Post by Ubuntuud on 2006-07-11
I'm trying to access the apache webserver...

I found something with "htpasswd". But the tutorial wants to write to a file that doesn't exist. So I created it, but that didn't help.

This is the howto (scroll down to just above the midle of the page):

[http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

---

### Post by alanphil on 2006-07-11
The htpasswd stuff can be used to secure a directory on your webserver. I don't think you need to do this at this point.

You just want to enter the IP Address of the webserver, in a web browser on another machine. This remote web browser should show the default Apache page served by your Apache server.

---

### Post by Ubuntuud on 2006-07-11
Indeed, but it asks for a password (and username) I don't know. What's the default (if there is any)?

---

### Post by alanphil on 2006-07-11
While sitting on the webserver running Apache, can you view the local HTML pages in a web browser?

---

### Post by Ubuntuud on 2006-07-11
Yes.

---

### Post by alanphil on 2006-07-11
OK. If you are using a web browser on another machine on the network, there should not be any prompt for user name or password. NOTE: You should not be trying to connect to the webserver using **Places menu**; Connect to Server. You want to open Firefox, and type in the IP Address of the Apache webserver. 

If that is what you are doing, and there is a prompt for a password then tell us more information about your network. How many computers, hub, switch -- all of the details about the network.

---

### Post by Ubuntuud on 2006-07-11
OK.

(all PCs other than my run windows)
The router is at my sister's PC.
And there are three laptops connected wireless to that router.
The apache server is on one of those laptops.
I have tried the IP adress thing on both, my dad's laptop and my sister's desktop PC. They both didn't work.
Then I tried it on my own PC. First with the server's name: "http://hapake/". Worked. But the IP thing didn't work.

It says it's a SITECOM WL-108 btw.

But isn't there some config file where I might have messed in that caused this?

---

### Post by scxtt on 2006-07-11
do you have a firewall going on the apache2 box? -- and have you restarted apache [or the laptop] since moving it? -- and are you sure of the IP address after you've moved the laptop to the router?

---

### Post by Ubuntuud on 2006-07-11
I'm sure about my IP ([www.watismijnip.nl)](www.watismijnip.nl)), and I restart all the time.

I also did a port scan:
21 (FTP): secure
23 (TELNET): secure
25 (SMTP): secure
79 (Finger): secure
[COLOR="Red"]80 (HTTP): secure[/COLOR]
110 (POP3): secure
139 (Net BIOS): secure
143 (IMAP): secure
443 (HTTPS): secure

I don't have firestarter installed, but is it possible that my sister is blocking my traffic?

---

### Post by alanphil on 2006-07-11
So, Apache is running on a Windows laptop (connected wirelessly to the router)?

And your computer is running Ubuntu, and you can connect to the Apache server using the server's name?

---

### Post by Ubuntuud on 2006-07-11
No, apache is running on my ubuntu laptop. And I'm trying to connect from my dad's windows machine. I'm sorry for not being clear. And I can connect from my ubuntu laptop to the server running on the same pc by using the server name, IP doesn't work.

---

### Post by alanphil on 2006-07-11
OK, thank you for that clarification. 

1. On your Ubuntu laptop, to reference your local Apache -- don't use the machine's IP but use 127.0.0.1.

2. Open a terminal on Ubuntu and type:

>ifconfig

and make sure you have the correct IP for the Ubuntu laptop.

3. Go to the Windows machine. Open a command prompt (Start > Run... and enter CMD). At the command prompt type:

> ping xxx.xxx.xxx.xx 
where the x variables are the Ubuntu laptop -- does the ping successfully find the Ubuntu laptop?

if so, on the Windows machine open a web browser. Instead of a domain -- enter the IP address in the Address field. What happens?

Hope this is helpful!  :p

---

### Post by Ubuntuud on 2006-07-11
Thanks! It already worked for that part, but I suddenly noticed that I should type another password. I entered the wrong one. Thanks again. I have certainly learnt something. Thanks! (That's three times now)

---

