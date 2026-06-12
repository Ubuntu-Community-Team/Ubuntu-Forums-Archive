---
title: "SSH &amp; Running GUI programs off Server?"
date: 2006-11-18
forum: General Help
---

### Post by olieviya on 2006-11-18
I'm not sure if this is possible but I'd like to give this a go:

I want to connect to my CS Department web server (Linux web server - that I can and do connect to via ssh2 using putty) and be able to use programs like Thunderbird, Firefox, kate, openoffice etc etc. Is this generally possible?

What exactly do I need to do? :???: 

I've been looking around and trying stuff but none of them seem to work and if i try and run a program that has a gui from putty it'll not allow it to open.


All help extremely appreciated.:KS

---

### Post by CatKiller on 2006-11-18
ssh -X user@hostaddress

---

### Post by karlbowden on 2006-11-18
Try connecting with a '-X' ssh option. This enables X11 forwarding on the client side. If this does not work then X11 forwarding may also be disabled on the server side.

eg:
ssh -X user@host

then just:
firefox

---

### Post by Joe_CoT on 2006-11-18
Firstly, make sure that your sshd is set up for X forwarding. make sure this is in your /etc/ssh/sshd_config
```
X11Forwarding yes
```

and then restart sshd
```
/etc/init.d/ssh restart
```

Then connect to ssh with X forwarding
```

ssh user@remotebox -Y
```

Keep in mind, your server will basically need the kde or gnome desktop installed, which it's probably not currently. As well, your system needs to have xwindow -- ie if it's a windows machine, you'll need to find and install one for it to work.

---

### Post by bukwirm on 2006-11-18
In putty, there is an option to enable X11 forwarding - make sure it's enabled. Also, as previously stated, you'll need X windows in some form.

---

### Post by olieviya on 2006-11-18
> **bukwirm said:**
> In putty, there is an option to enable X11 forwarding - make sure it's enabled. Also, as previously stated, you'll need X windows in some form.

I tried that before also... nothing seems to happen... It just gets "stuck".


ssh -X [email]og500@milan.cs.york.ac.uk[/email]
password: 

firefox

and then nothing...

---

### Post by karlbowden on 2006-11-18
What speed is the connection to the server?
X11 forwarding is a **very** bandwidth intensive way of running programs remotely.
Is you client machine a windows or linux box? If it is a windows box that your using putty to connect to the uni server with, are you also running a X11 server on the windows box?

---

### Post by olieviya on 2006-11-19
> **karlbowden said:**
> What speed is the connection to the server?
X11 forwarding is a **very** bandwidth intensive way of running programs remotely.
Is you client machine a windows or linux box? If it is a windows box that your using putty to connect to the uni server with, are you also running a X11 server on the windows box?

Both systems are running linux and it's a WAN so it's speedy. I tried both putty and the ssh command.

---

### Post by olieviya on 2006-11-20
I have this connection after my normal campus connection with is called eth0, named: lo, and i think it's for tunneling? :confused: :confused:  Sorry: n00b.


> **karlbowden said:**
> What speed is the connection to the server?
X11 forwarding is a **very** bandwidth intensive way of running programs remotely.
Is you client machine a windows or linux box? If it is a windows box that your using putty to connect to the uni server with, are you also running a X11 server on the windows box?

The lo one 100mbs if I'm not very much mistaken.

---

