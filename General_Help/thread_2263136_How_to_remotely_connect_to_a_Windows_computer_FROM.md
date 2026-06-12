---
title: "How to remotely connect to a Windows computer FROM Ubuntu"
date: 2015-01-29
forum: General Help
---

### Post by sam64 on 2015-01-29
There are many tutorials that show you how to connect to Ubuntu FROM Windows (by using putty as the client, as in this video [https://www.youtube.com/watch?v=5BsShkcweIs](https://www.youtube.com/watch?v=5BsShkcweIs) ), but what about the other way around? What I want to do is remotely connect to another computer (that is, to use my home desktop as the server) from my Ubuntu VM on my laptop. But what client am I supposed to provide a bridge-connection FROM Ubuntu TO Windows? Is putty only one way (that is, can putty only connect a windows to a linux)?

---

### Post by Mike_Walsh on 2015-01-29
Hallo, Sam.

If I read this correctly, you have a desktop, running Windows, yes?

And you have a laptop with Ubuntu ( only on a VM)...yes?

You want to use the Windows machine as the server, and you want to access it, using your Ubuntu as the client, yes?

Normally, I would say straight away that you want to have a look at SAMBA. It CAN be used to connect two Linux machines, but was primarily developed to address the exact situation you have stated, i.e., cross-platform...Linux to Microsoft.

However, I wouldn't like to say whether it will work with one of the machines running as a VM. I have NO experience of VMs, and can't ever see me doing so, as I have no need of one.

Might be better to wait for someone with experience of VMs; in the meantime, however, it won't hurt to Google 'SAMBA in Linux', and see what you come up with.


Regards,

Mike.

---

### Post by SeijiSensei on 2015-01-29
Samba is just a file server.  I think the OP wants to be able to access his or her desktop remotely.  Here's one solution: [http://www.7tutorials.com/connecting-windows-remote-desktop-ubuntu](http://www.7tutorials.com/connecting-windows-remote-desktop-ubuntu)

---

### Post by Holger_Gehrke on 2015-01-29
> **sam64 said:**
>  But what client am I supposed to provide a bridge-connection FROM Ubuntu TO Windows? Is putty only one way (that is, can putty only connect a windows to a linux)?

In theory ssh can be used from Linux to Windows; all you'd need would be a ssh server on Windows. In practice this is not all that useful, since most windows application are graphical in nature and ssh is mostly meant for the command line (although it can do X11-forwarding if you connect between two systems running the X Window System). You'd be better off with a graphical desktop sharing program, something like rdesktop or remmina.

---

### Post by sam64 on 2015-01-30
@SeijiSensei, I tried that tutorial link that you gave me. My laptop and home computer (home computer is my connection target) are both connected to the same Ethernet adapter. I used my home computer's the ip address under the Ethernet adapter Local Area Connection in the Server text field of *Remmina Remote Desktop Client*, but I'm still unable to connect. Do I still need to configure putty on my home computer (which is a Windows 7) to bridge the connection?

---

### Post by HermanAB on 2015-01-30
rdesktop is what you are looking for.

---

### Post by sam64 on 2015-01-31
> **HermanAB said:**
> rdesktop is what you are looking for.

OK, I just got the SSH Server set up on my desktop computer at home by configuring putty and cygwin on it. I've also got both my laptop (with my Ubuntu VM on it) and my desktop connected to the same Ethernet Adapter, so I've got a local network connection set up. I just tried to connect to my desktop from my laptop, but the connection failed (as shown in the following screenshot):
 
[ATTACH=CONFIG]259627[/ATTACH]

Am I missing something?

---

