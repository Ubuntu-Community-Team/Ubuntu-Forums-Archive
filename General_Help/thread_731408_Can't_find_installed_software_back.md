---
title: "Can't find installed software back"
date: 2008-03-21
forum: General Help
---

### Post by slinky89 on 2008-03-21
Hello,

I had this problem several times but I will specify to the latest one now. I downloaded RealVNC in a RPM package, I converted it to a .dem package and installed it. It seemed to go very well and it says that the application is installed successfully. But when I'm looking in the Applications menu (above left) I can't find it anywhere. Also when I use search on VNC, I only find the .dem package.
But.. when I'm looking in synaptic I can see the application and it's also marked as installed.

So the question is, where can I find my software and how can I open/start it?


Thanks in advance,
  - Slinky

---

### Post by dcstar on 2008-03-21
> **slinky89 said:**
> Hello,

I had this problem several times but I will specify to the latest one now. I downloaded RealVNC in a RPM package, I converted it to a .dem package and installed it. It seemed to go very well and it says that the application is installed successfully. But when I'm looking in the Applications menu (above left) I can't find it anywhere. Also when I use search on VNC, I only find the .dem package.
But.. when I'm looking in synaptic I can see the application and it's also marked as installed.

So the question is, where can I find my software and how can I open/start it?


Thanks in advance,
  - Slinky

Look in the properties of the package in Synaptic for the installed files.

---

### Post by slinky89 on 2008-03-22
Hi,

I already did that but I still can't find a way to open the program. Here's a overview of the installed files:

/.
/usr
/usr/share
/usr/share/vnc
/usr/share/vnc/classes
/usr/share/vnc/classes/index.vnc
/usr/share/vnc/classes/logo150x150.gif
/usr/share/vnc/classes/vncviewer.jar
/usr/share/doc
/usr/share/doc/vnc
/usr/share/doc/vnc/changelog.Debian.gz
/usr/share/doc/vnc/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/vncviewer.1.gz
/usr/share/man/man1/vncpasswd.1.gz
/usr/share/man/man1/vncserver.1.gz
/usr/share/man/man1/vncconfig.1.gz
/usr/share/man/man1/Xvnc.1.gz
/usr/share/man/man1/x0vncserver.1.gz
/usr/bin
/usr/bin/Xvnc
/usr/bin/vncpasswd
/usr/bin/vncconfig
/usr/bin/x0vncserver
/usr/bin/vncserver
/usr/bin/vncviewer
/usr/X11R6
/usr/X11R6/lib
/usr/X11R6/lib/modules
/usr/X11R6/lib/modules/extensions
/usr/X11R6/lib/modules/extensions/vnc.so

I tried to open /usr/bin/vncviewer but nothing happens.

---

### Post by banewman on 2008-03-22
Since it is in /usr/bin and that folder is one that the terminal searches for apps try typing Realvnc in a terminal.

---

### Post by slinky89 on 2008-03-22
I already tried that, and also vnc and vncviewer but it says "command not found"

---

### Post by banewman on 2008-03-22
The terminal is case sensitive - did you try with a capital and small R.
Try vnc4viewer at the prompt.

---

### Post by spupy on 2008-03-22
Try:
```
gnome-application-browser
``` (not very sure if that's the correct name)

---

### Post by slinky89 on 2008-03-22
> **banewman said:**
> The terminal is case sensitive - did you try with a capital and small R.
Try vnc4viewer at the prompt.

"Command not found" but when I type vncviewer it says something different: vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


[QUOTE=spupy]Try:
Code:

gnome-application-browser

(not very sure if that's the correct name)[/QUOTE]

"Command not found"

---

### Post by banewman on 2008-03-22
OK - you need to install the client on one comp and the server on the comp you want to connect to.
Did you install a vnc server?

---

### Post by slinky89 on 2008-03-22
Yes I did, but that´s not the point. Even when I didn't installed a server the viewer should start up. Only thing is I wouldn't be able to connect with another PC.

---

### Post by banewman on 2008-03-22
I'm a long way from you're comp and can't see what's been done. :)
Why did you decide to use an rpm for this?
Have you tried the packages in synaptic?
I think the rpm install might be the issue.

---

### Post by slinky89 on 2008-03-22
> **banewman said:**
> I'm a long way from you're comp and can't see what's been done. :)
Why did you decide to use an rpm for this?
Have you tried the packages in synaptic?
I think the rpm install might be the issue.

Well, I'm in the Netherlands so why don't you just come by? lol :p
Ehm.. what should I use else? I could download a rpm and a tar.gz both I would just convert to deb because that's the way I know.
And what do you mean with if I tried the package in synaptic?

---

### Post by Tomatz on 2008-03-22
If i remember right the command is:

vncserver

---

### Post by slinky89 on 2008-03-22
No, that would start the server. What I want is the viewer, anyway it gives the same error:

vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

only "vncviewer" is replaced for "vncserver"

---

### Post by ryanhaigh on 2008-03-22
There is a vnc viewer available in the default install, go to Applications>Internet>Terminal Sever Client and you can change the protocol to VNC.

---

### Post by slinky89 on 2008-03-22
> **ryanhaigh said:**
> There is a vnc viewer available in the default install, go to Applications>Internet>Terminal Sever Client and you can change the protocol to VNC.

The thing is, I want to take over a Windows computer. I installed a server on that and configured a password so when I connect to that computer I only have to type the password and then I have control.

And when I try to connect with Terminal server I get the same error as typing vncviewer in my terminal.

---

### Post by ryanhaigh on 2008-03-22
Im pretty sure that you can use the terminal server client program in that way, it is only a frontend and actually lauches a vncviewer. You may have overwritten the installed application with your converted package so you may need to remove the package you have installed from the converted rpm and install the default which I believe is xvncviewer. There is also xtightvncviewer which I have found better for low bandwidth connections, of course you need to be using tightvnc on the windows machine to take advantage.

---

### Post by slinky89 on 2008-03-22
I think your right, I removed Realvnc and now I don't get that error anymore. But I'm still not able to connect.. when I'm trying to connect with Terminal server the windows just disappears and nothing happens.

Edit: Oh... it gives a error unable to connect, but after a long time.

---

### Post by ryanhaigh on 2008-03-22
Is the windows computer on the same network as you are?
Do you know the IP address of the windows computer?
Are you able to ping that IP address?
Does it work if you try to connect to the windows computer using the IP address rather than hostname in VNC?

---

### Post by slinky89 on 2008-03-22
Uh well... I don't know if I'm in the same network.. I'm on the same router but I don't know how it works exactly, in Windows it was with workgroups right?

When I type the host name I get the message unable to connect immediately and when I type the IP address it takes a while.

---

### Post by ryanhaigh on 2008-03-22
Are you able to ping the windows machine from your ubuntu machine using the ip address. 
Have you connected to the vnc server before, is it possible that a software firewall on the windows machine is blocking the connections?

---

### Post by slinky89 on 2008-03-22
Oh sorry forget to answer that question, yes I'm able to ping. Well there is a software firewall yes but it always worked but I will turn it off and try again. I'll let you know.

---

### Post by slinky89 on 2008-03-22
Thanks a million! It works now!

It's a bit strange because it always worked.. and I configured the firewall to allow RealVNC but I can only connect when turning the firewall off.

So for now this problem is solved and now I'm gonna figure out how to configure the firewall right.

---

