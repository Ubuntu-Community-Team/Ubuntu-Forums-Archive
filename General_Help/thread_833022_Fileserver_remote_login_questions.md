---
title: "Fileserver remote login questions"
date: 2008-06-18
forum: General Help
---

### Post by Muntted on 2008-06-18
on another note, i have just setup ubuntu on a new file server.
Now what i want it to do is:
[LIST=1]
[*]Boot up
[*]log in
[*]start torrent program, mythtv backend and samba sharing
[*]lock itself
[/LIST]

from here I want to be able to log into the pc from another ubuntu computer and take control of the desktop remotely.

I have tried XMDP but it logs in under a different user and you have to log out to finish the session.
I have tried vnc but I couldnt get the computer to lock itself after booting and I couldnt get a vnc client to access it.

Ideally it should lock itself and then if I remote log in I should be able to log in onto the locked user, while nothing is being shown on the actual computer itself (unlike vnc).

---

### Post by HermanAB on 2008-06-18
Headless servers are managed through SSH.  If it is not installed already, install 'ssh' and 'ssh-server' packages.

---

### Post by Muntted on 2008-06-18
once they are installed then what?

---

### Post by bodhi.zazen on 2008-06-18
See these links :

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

ssh access will give you a command line interface on the server. You can forward X or forward a VNC connection over ssh :

ssh -X

[uwiki]VNCOverSSH[/uwiki]

You then start your applications, log out when done.

You may also be interested in screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

        [http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

---

### Post by Muntted on 2008-06-18
The problem with that solution is that it still requires me to log out which means the programs will stop working. Also the work i am doing on the computer, I want that to be happening in the background as someone might be using the computer under another account to watch a movie or something.

In otherwords. I want the computer to start log into a user, start programs and then "switch user". That someone else can use a different user. While they are using it I want to be able to log into that initial user space, do some stuff and lock it again, without actually stopping the programs I was running.

---

### Post by bodhi.zazen on 2008-06-18
No, you can ssh into a computer while someone is using it for something else. Linux (Unix), unlike windows, is multi-user.

Second, if you want programs to continue to run in the background, after you log off, well that is what screen is for.

You can ssh, start applications in screen, even forward a VNC session, all without disturbing a user sitting in front of the box (unless you terimate thier applications or use excessive memory / cpu cycles). (Note there are different VNC servers, vino / x11vnc share the same X session, vnc4server or vncserver each start separate X sessions. Well, they are not exactly X sessions ...).

---

### Post by Muntted on 2008-06-18
So let me get this straight:
I install screen on remote computer
Somehow get it to log into my user when my computer starts, start the programs I want and log out, making sure screen doesnt kill my tasks.
Log into it via SSH on local computer
Start a VNC session through the ssh and screen.
This will allow me to log in and out of it without disrupting the processes or anyone on the computer.

Talk about overcomplicated.
It should be a matter of:
Remote computer starts
Remote computer starts processes in the background under a user all while being available to anyone actually at the remote computer.

Then I should be able to do something like XMDCP into the user that has the tasks running and disconnect without actually logging out that user so the remote computer still has those processes running.

---

### Post by bodhi.zazen on 2008-06-18
I think you are making it more complicated then it really is. It is, IMO, very simple and straight forward.

To be honest, sounds like you want something like a VNC connection. You can look at vnc4server or FreeNX.

If you want a bunch of applications to start at boot time or log in -> write a script.

To use ssh, on the server:

```
sudo apt-get install ssh
```

On the client you just:

```
ssh user@server
```

If you want a graphical connection either ssh -x , vnc, or FreeNX.

If you want applications to start on boot -> script

If you want applications to continue to run when you log out either vnc, freenx, or screen.

---

### Post by Muntted on 2008-06-18
sorry about all this, your probably right that Im making this hard for myself.

Create a script to start the programs as soon as it starts up.
Set up a ssh server + vnc server on remote computer
Set up vnc client on local computer
I ssh into the remote computer and then start the vnc client

How do I make sure the vnc connection goes through the ssh tunnel?

Now VNC actually takes control of the computer so that a user sitting at the remote computer is seeing the same thing I am. I dont want that to happen, I want all this to be happening in the "background". im assuming doing all this through a ssh tunnel solves this problem?\

Thanks for all the help by the way.

---

### Post by bodhi.zazen on 2008-06-19
> **Muntted said:**
> sorry about all this, your probably right that Im making this hard for myself.

Create a script to start the programs as soon as it starts up.
Set up a ssh server + vnc server on remote computer
Set up vnc client on local computer
I ssh into the remote computer and then start the vnc client[/code]

You can skip the ssh part if you are on a LAN (and run VNC directly), otherwise IMO best tunnel your VNC over ssh.

You can either :

[uwiki]VNCOverSSH[/uwiki]

or take a look at FreeNX

[uwiki]FreeNX[/uwiki]

> How do I make sure the vnc connection goes through the ssh tunnel?See the wiki page.

[quote]Now VNC actually takes control of the computer so that a user sitting at the remote computer is seeing the same thing I am. I dont want that to happen, I want all this to be happening in the "background". im assuming doing all this through a ssh tunnel solves this problem?no, no, no, this is what you are missing. :lolflag:

There is no single VNC server, think of VNC as a type of connection or protocol, one way to forward a graphical connection.

The way it works depends on the server. The Windows server behaves the way you describe as windows is not a multiuser OS.

In Ubuntu *some* VNC servers work that way (the default , vino, and x11vnc), others do NOT.

So if you use vncserver or vnc4server you will get a *NEW* session, *independent of the user sitting in front of the box*. The two users will not interact. FreeNX will act the same way.

So, if you want a shared desktop use the default VNC server, vino, or x11vnc.

If you want independent sessions use vnxserver, vnc4server, or FreeNX.

With what you are describing => FreeNX

> Thanks for all the help by the way.np

---

### Post by Muntted on 2008-06-19
Perfect. Ill post back on how I go. Ill even write a simple guide on it.

---

