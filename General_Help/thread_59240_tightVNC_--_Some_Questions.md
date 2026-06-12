---
title: "tightVNC -- Some Questions"
date: 2005-08-23
forum: General Help
---

### Post by Freddie on 2005-08-23
Hi, I want to be able to access my server (which is running ubuntu, ppc) remotely. I have been told that tightVNC is the best way to go. However, often when I work away from home I am unable to install applications, however I am able to run Java applets (in the form of ones of webpages). Someone told me that there is a Java applet for tightVNC which can be used if you are unable to install the tightVNC client software. Is this correct?
As for the tightVNC server, is it available for Ubuntu (Mac PPC) and is it hard to set up and get working?
Thanks for all of your help.

---

### Post by hagen00 on 2005-08-23
Hi there,

> As for the tightVNC server, is it available for Ubuntu (Mac PPC) and is it hard to set up and get working?
i'm also very new to Ubuntu, but one thing i've learnt is that nothing is hard to install and get working on ubuntu. Coming from Red Hat, the package management on Ubuntu is a dream!!

```
sudo apt-get install tightvncserver tightvncviewer
```

before you do that though, do a```
 apt-cache show tightvncserver
``` to make sure it's what you want.

---

### Post by Freddie on 2005-08-24
This is going to sound dumb, but here goes. Okay, I have installed the server as well as the Java-applet thingy which the server can distribute to the server. But, what do I do now, is there a config file I need to edit and what software do I need to install on computers what I want to use vnc on (a viewer) and I also need to know what port I need to use.

---

### Post by Freddie on 2005-08-30
I typed in:
```
root@macserv:/home/freddie # tightvncserver

You will require a password to access your desktops.

Password:
Verify:
Found /usr/share/tightvnc-java for http connections.

New 'X' desktop is macserv:1

Creating default startup script /root/.vnc/xstartup
Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/macserv:1.log

```
Then I installed tightVNC on my Windows computer and tried to connect (using the viewer) to 192.168.0.5 which is the port of my Linux computer but I got the error 'Failed to connect to host'
Can someone please help me.

---

### Post by hashimoto on 2005-08-30
[QUOTE=Freddie]I typed in:
```
root@macserv:/home/freddie # tightvncserver

You will require a password to access your desktops.

Password:
Verify:
Found /usr/share/tightvnc-java for http connections.

New 'X' desktop is macserv:1

Creating default startup script /root/.vnc/xstartup
Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/macserv:1.log

```
Then I installed tightVNC on my Windows computer and tried to connect (using the viewer) to 192.168.0.5 which is the port of my Linux computer but I got the error 'Failed to connect to host'
Can someone please help me.[/QUOTE]
 Just a thought: did you specify the correct screen to connect to? 
I've not used the java based viewer, but when I connect using CLI I must specify the screen using something like "vncviewer 192.168.0.5:1"

---

### Post by Freddie on 2005-08-30
Ok, thanks! It seems to connect but when I connect all I see is a terminal (using the default gnome theme). I want it to work like it does on Windows (like the Gnome/Ubuntu remote desktop system) works, when I can see my computer screen as if I was actally working on it (so my real desktop). Can anyone tell me how to do this. Also, I normally connect locally use 192.168.0.5:1 how should I set up port-forwarding on my router to allow remote access?

---

### Post by hashimoto on 2005-08-30
[QUOTE=Freddie]Ok, thanks! It seems to connect but when I connect all I see is a terminal (using the default gnome theme). I want it to work like it does on Windows (like the Gnome/Ubuntu remote desktop system) works, when I can see my computer screen as if I was actally working on it (so my real desktop). Can anyone tell me how to do this. Also, I normally connect locally use 192.168.0.5:1 how should I set up port-forwarding on my router to allow remote access?[/QUOTE]
 Did you try to define the screen to be xxx.xxx.x.x:0? I think this is is the normal session screen you use (could be wrong, though). You could also try startx in the remote command line...maybe?

I think the vnc server is listening to port 5900 though, so somehow it should be forwarded in the router. And I would like to know this too, as I need to do the same to my fathers router so I can support him from home. And if someone knows/has detailed instructions on how to set up and use ssh together with vnc.

---

### Post by Maier on 2005-09-01
Try Looking into FreeNX instead og VNC.. 

FreeNX's speed is amazing compared to VNC and other remote programs.. (and integrates really well with ubuntu)


(on the sidenote, VNC has some development going on, wich will improve the speed a lot)

Good Luck though :)

---

### Post by seethru on 2005-09-06
[QUOTE=Maier]Try Looking into FreeNX instead og VNC.. 

FreeNX's speed is amazing compared to VNC and other remote programs.. (and integrates really well with ubuntu)


(on the sidenote, VNC has some development going on, wich will improve the speed a lot)

Good Luck though :)[/QUOTE]

does FreeNX allow a java-applet client connection?

---

### Post by seethru on 2005-09-07
[QUOTE=seethru]does FreeNX allow a java-applet client connection?[/QUOTE]
 when specifying the :0 display I get this error.

```
Warning: echelon:0 is taken because of /tmp/.X0-lock
Remove this file if there is no X server echelon:0
A VNC server is already running as :0
```

thing is, I want control of this session remotely....

---

### Post by seethru on 2005-09-07
[QUOTE=seethru]when specifying the :0 display I get this error.

```
Warning: echelon:0 is taken because of /tmp/.X0-lock
Remove this file if there is no X server echelon:0
A VNC server is already running as :0
```

thing is, I want control of this session remotely....[/QUOTE]
 found an alternate solution, use x11vnc w/ the tightvnc java-applet, like so.

x11vnc -httpdir /usr/share/tightvnc-java -scale <if you want> -httpport <port> -display :0

---

