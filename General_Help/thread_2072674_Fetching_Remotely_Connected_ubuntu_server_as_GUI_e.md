---
title: "Fetching Remotely Connected ubuntu server as GUI enabled"
date: 2012-10-18
forum: General Help
---

### Post by NagaLakshmi on 2012-10-18
Hi,

I am trying to connect to a remote server using remote desktop client  application.Actually,the remote server is a server edition.I need to  fetch it as gui enabled like a ubuntu desktop edition.So i have installed ubuntu-desktop using sudo  apt-get install ubuntu-desktop.
I'm able to connect to the server via putty SSH client.In putty we can  run in command line mode only.I want to run the server in GUI mode.I  cant access the server as GUI enabled in remote desktop client.

What shall I do now???

---

### Post by Lars Noodén on 2012-10-18
To fetch files from the remote computer using a grahpical interface you do not need to install Ubuntu-desktop on it.  That's just extra and unrelated.  What you do need is a file transfer tool with graphics.  Then you can connect with SFTP.   Three that work with Ubuntu are Dolphin, Nautilus and FileZilla.  

Your system probably has Nautilus installed, it will if it is plain Ubuntu.  To connect to the other machine using either Nautilus or Dolphin, press ctrl-L and then enter the URI for the remote host.  The URI will be something like this, sftp://nagalakshmi@xx.yy.zz.aa/ where you substitute the actual username and host address.

---

### Post by 2F4U on 2012-10-18
This article describes how to enable remote desktop from a SSH session:

[http://www.ehow.com/how_7301198_enable-remote-desktop-ssh-ubuntu.html](http://www.ehow.com/how_7301198_enable-remote-desktop-ssh-ubuntu.html)

---

### Post by NagaLakshmi on 2012-10-18
Thank you for the reply Lars Noodén..

But the thing is i don't want to fetch or transfer only files.I need all the things that can be done in a ubuntu-desktop(using GUI interface) on the remotely connected server also.Since the server is in console mode,I can execute process in command line only.I want it to convert to GUI mode.

---

### Post by Lars Noodén on 2012-10-18
Then you'll want either krdc/krfb or VNC.  If you use VNC, it is very important to only tunnel it over SSH and not leave it exposed.   If it is exposed to the public, the public will get in eventually.  Here is one document to get you started, but there are many other tutorials available on the net:
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by 1clue on 2012-10-18
What is your goal here?  Is there just some gui tool that you want to use, or are you unfamiliar with the command line, or do you want to have something like Windows where you have a single server and several people log into it to do their work for the day, and it needs everything the user might want that day?

If, for example, you just want to use synaptic instead of aptitude, then install synaptic and use
**ssh -X your.host.name**
**synaptic**

Note that you need an X server on your workstation, and it needs to be running.  Also note that the -X option is for a Linux ssh client, I don't know what putty needs to forward X.

---

### Post by NagaLakshmi on 2012-10-18
Ya thanks 1clue,
 
I need just as the same as you told for windows.I need a single server where multiple users can log in using remote desktop connection.But if it is command line means it will not be user friendly.So only i need a GUI for that server.

---

### Post by 1clue on 2012-10-18
OK so you want a single server which has all the software you need on it, and people log in remotely.

I've done this sort of thing but years ago, and it's a bit easier now I understand.

Here's the deal:
Linux is a multi-user operating system by design.  X is a networked UI by design.

I just googled **remote ubuntu xorg from windows 2012** and got several promising links.

Take out the 'ubuntu' and you get more good info.

The biggest thing here is going to be finding a good X server for Windows.  Windows has its own window manager, and X is not it.

There are 2 possibilities for this, you either get an Ubuntu desktop in a window (or full screen) which has your remote session in it, or you get individual windows from Ubuntu (like Synaptic, Firefox, etc) and have those windows sort-of mingle with your MS windows.

I don't know how much you know about Xorg, but the whole client-server thing is opposite of what you might think.  Your Ubuntu Server will have the Xorg clients on it.  Firefox is an Xorg client.  Your workstation has the server.

All the embellishment comes from the server side.  Firefox can't really tell what window manager you're using, what sort of colors you use, any of the theme information.  That all happens on the server.  And generally speaking, X11 servers for Windows are pretty minimal by default.

So you won't get your normal Ubuntu desktop unless you really get involved.

Good luck and have fun.

---

### Post by Lars Noodén on 2012-10-18
As 1clue mentions, you'll need an X-server for your old machine.  Xming is a commonly used one in those circumstances.  

Here is one set of instructions for using Xming with PuTTY:
[http://taggi.cse.unsw.edu.au/FAQ/Accessing_CSE_login_servers/#Logging_in_from_Windows](http://taggi.cse.unsw.edu.au/FAQ/Accessing_CSE_login_servers/#Logging_in_from_Windows)

xming must be installed and running before starting PuTTY

---

### Post by NagaLakshmi on 2012-10-19
Thank yo very much 1clue,

I can connect to the remote ubuntu server with a ppk key file using putty ssh client.Mine is Ubuntu 12.04 LTS.The remote server is also ubuntu 12.04.In this case,how can i connect to the remote server as GUI enabled.Is it possible to connect to the server without ppk file.

Which software is to be used for establishing remote connection in this manner(from ubuntu desktop to ubuntu server as GUI enabled)???

---

### Post by 1clue on 2012-10-19
So your client system (your workstation) is also Ubuntu?  Then it's easy:

ssh -X [email]remoteUser@remote.host.name[/email]
<login>
sudo synaptic

The key here is ssh -X (capital X) which tells ssh to forward X sessions.  The synaptic line is just an x app to run, you can make it anything.

If you want to have a window containing a desktop like Windows Terminal Server you need to go through a bit more work, and last time I did it it was using XFree86 rather than Xorg, so everything is going to be different.  Look up Ubuntu remote Xorg or similar, you're sure to find a page about it.

---

