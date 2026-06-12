---
title: "Apache files read only"
date: 2007-06-01
forum: General Help
---

### Post by mac173 on 2007-06-01
I am trying to configure my apache server to only listen to my own network. I am using the command 

$ gksudo "gedit /etc/apache2/ports.conf" and getting the ports.comf file. 

Unfortunatly, it is flagged as "Read Only" and I cannot edit it. 

Also, I made my user name the administrator, but don't think I have a root account. 

I think I need root access to make the changes, so how do I do that?

The apache server is on a machine duel booting WinXP and Ubuntu, and the server IS running.

---

### Post by pbw on 2007-06-01
sudo chmod +w  /etc/apache2/ports.conf

sudo nano /etc/apache2/ports.conf

sudo /etc/init.d/apache2 restart

edit: btw, if you want to do a few tasks as root. just type sudo -s then enter your password. No real need for fully enabling root.

---

### Post by mac173 on 2007-06-02
> **pbw said:**
> sudo chmod +w  /etc/apache2/ports.conf

sudo nano /etc/apache2/ports.conf

sudo /etc/init.d/apache2 restart

edit: btw, if you want to do a few tasks as root. just type sudo -s then enter your password. No real need for fully enabling root.

OK, I used that to get into the file, and was able to change the "Listen 80" to "Listen 127.0.0.1:80" like I want it. 

The problem is, just how do I SAVE the file once I change it? The File and Edit buttons neither one have a SAVE on the drop down menu, and if I just close the file, it does not save it. I know, this is elementary, but I don't know how.

---

### Post by taurus on 2007-06-02
If you are using nano text editor, <Ctrl>o to save and <Ctrl>x to exit.

---

### Post by mac173 on 2007-06-02
> **taurus said:**
> If you are using nano text editor, <Ctrl>o to save and <Ctrl>x to exit.

Ohhhhhh...........<light bulb appears over my head>

the nano part of that command is designating the text editor to be used? In that case I could use "nano emacs" to use the emacs text editor, yes? Very cool. Nice to understand the commands, it helps. 

Thank you very much, the file is edited the way I wanted. Looks like I need to study up on the text editors a bit.

---

### Post by taurus on 2007-06-02
> **mac173 said:**
> Ohhhhhh...........<light bulb appears over my head>

the nano part of that command is designating the text editor to be used? In that case I could use "nano emacs" to use the emacs text editor, yes? Very cool. Nice to understand the commands, it helps. 

Thank you very much, the file is edited the way I wanted. Looks like I need to study up on the text editors a bit.

Nano is a text edit and so is emacs.  So if you want to use emacs, then you would run

```
sudo emacs filename
-or-
sudo nano filename
-or-
sudo vim filename
```

---

### Post by mac173 on 2007-06-02
I have  been playing with that, and I see how that works now, thanks. 

I tried to access the apache default site from the same computer, and that works, but when using the 127.0.0.1 on my other comp I got the cannot find server message. So do I have to configure my local network before I can access the web  page from other computers? 

That is the ultimate goal right now, to run a server on one machine on my network, and to be able to access it from the other computers, but NOT the internet.

---

