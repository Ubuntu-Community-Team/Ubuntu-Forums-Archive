---
title: "shell commands"
date: 2013-04-03
forum: General Help
---

### Post by john abbott on 2013-04-03
I am a long-time user of Widows (since Window 3.1). I just recently looked into Ubuntu. I have installed Ubuntu 12.04 LTS server on a newer laptop. I would like to turn this laptop into a web server for my own websites. I am looking for a list of commands for the Terminal(shell). I have been reading quite a few of these forum posts and realize I have a lot to learn before I take on creating a webserver and getting my websites uploaded. Does anyone know where I could find this list of commands?

---

### Post by Cheesemill on 2013-04-03
Getting the basic LAMP stack is actually easy with Ubuntu, you can install with just one command...
```
sudo apt-get install lamp-server^
```

This will install Apache along with MySQL and PHP and give you a basic configuration that will serve web pages from your /var/www directory.

Just google for 'ubuntu 12.04 lamp' and you will find plenty of more detailed guides out there.

For commands in general, I suggest you start with the CLI resources page on the Ubuntu wiki...
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by john abbott on 2013-04-03
Thanks I have already installed these programs and I found some command line functions on Wiki but I will check out your suggestion. I now have to find out how to access my router settings via a wireless network. I read somewhere on the web that a web server should be wired to a router. If so, what OS would you suggest for a computer with 256K RAM

---

### Post by d0006 on 2013-04-04
> **john abbott said:**
> Thanks I have already installed these programs and I found some command line functions on Wiki but I will check out your suggestion. I now have to find out how to access my router settings via a wireless network. I read somewhere on the web that a web server should be wired to a router. If so, what OS would you suggest for a computer with** [COLOR=#ff0000]256K RAM[/COLOR]**

I would suggest buying more RAM! Is it even possible to run Linux on a 256K system?  Even SliTaz needs 48MB for a CLI environment!

If you meant 256MB, take a look at #! (crunch bang Linux, and you should still buy more RAM or a newer computer).

---

