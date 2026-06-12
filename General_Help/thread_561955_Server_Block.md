---
title: "Server Block"
date: 2007-09-28
forum: General Help
---

### Post by mattc908 on 2007-09-28
Basiacally this is what happens, I have a server running ubunutu 7.04 and It is in my house. I can SSH into it. But I canno't FTP from within my network and also I cannot PHPmyAdmin into it. My friends can from other house's but I cannot. Would it be a router setting or a server setting anyone know that can help get rid of this?

---

### Post by SeanTater on 2007-09-28
Have you checked if the server is on?

```
sudo netstat -pl4
```

It should tell you what your server is listening for, and what servers are running

Most likely, you need to edit a server configuration file to listen on all addresses (which would be *) rather than localhost or the like. Although, I don't know what server you are using, so I cannot help much there.


Also, as for the "friends from other houses", you will need to change a router setting, called port forwarding. For HTTP (which is WWW) that port to forward is 80. 21 for FTP. You don't want to forward SSH unless you really know what you are doing, but that would be 22.
This guide should help you in finding out how to forward your ports: [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by mattc908 on 2007-09-28
............yeah I know what I'm doing thanks for the help, but I have a DMZ set up so it unlocked all the ports, Yes the server is on its physically sitting in my house, I SSH into it all the time and make edits........ Im not exactly sure why all my friends can FTP into it via there house's but from my own house via the server is in my house I cannot? I'm not exactly sure why it does this......

---

### Post by mattc908 on 2007-09-30
Bump

---

### Post by mattc908 on 2007-10-02
Bump Please help me!

---

### Post by SeanTater on 2007-10-02
"Within my network" Does this mean when you access the public or private IP of the server? Either way, can you ping it?

Then try this:
```
sudo apt-get install httping
httping -g http://YOURIP/
```

Then this: (Only if you mean the private IP)

```
sudo apt-get install nmap
nmap YOURIP
```

And possibly this:
```
sudo apt-get install traceroute
traceroute YOURIP
```

Then also try this on the server, while you try the httping one on the client:
```
sudo apt-get install tcpdump
sudo tcpdump -i  YOURNETINTERFACE port 80
```
where YOURNETINTERFACE is something like eth0 or eth1 or ath1 or wifi0 or whatever you see when you type in ifconfig

---

### Post by mattc908 on 2007-10-03
I can go to the public website I have stored on there and I can SSH into. But I cannot FTP into.......Directly. I can view the files FTP in my browser but I cannot use a client (tried many) and FTP into it to add and remove files. My friends can all but I cannot.

---

### Post by SeanTater on 2007-10-03
So you are saying you can use your web browser to access your FTP server, but a client like GFTP won't do it? Web browsers almost always log in as anonymous. Have you tried logging in as anonymous, as guest, or without a username?
If you are looking to have all the read/write  rights of your user account over the Internet (effectively root), then you are in for serious security issues, as the password is not encrypted.

---

### Post by mattc908 on 2007-10-03
No when I access it via Browser I can obviously only read, and it asks for a username and password thats the way I set it up. I cant access it via Clients?

---

### Post by mattc908 on 2007-10-04
Any assistance?

---

