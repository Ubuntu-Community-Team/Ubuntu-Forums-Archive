---
title: "How to manage applications without a GUI? Ubuntu Server"
date: 2016-04-02
forum: General Help
---

### Post by lakeshore2985 on 2016-04-02
So I've been fascinated about the idea of having Ubuntu Server as my main file server and P2P machine (and perhaps even functioning as a home router). But then the question is, how can I control or access for example P2P programs without a GUI? Is that even possible? e.g. Transmission, Deluge, aMule, etc and the list goes on and on.

Such a lightweight operating system could serve P2P needs quite well too! Get spare hardware and underclock the hell out of it!

---

### Post by QIII on 2016-04-02
Hello!

Just by way of example for transmission, you could take a look at [this]("https://help.ubuntu.com/community/TransmissionHowTo#Transmission_Command_Line").

There are many, many of us who use our server machines solely from the command line.  Some applications may have a bit of a learning curve since you don't have a GUI where the "START NOW" button jumps out at you.  But you learn over time.

---

### Post by lakeshore2985 on 2016-04-02
Hi donkey!

So this turns out to be a little confusing at first;  when one says "CLI", does it mean the same as WebUI access? Now I know  CLI stands for command line interface, so it's different than Web  interface. But it also says that CLI has to activate daemon, which in  turn also provides WebUI access? How does that work?

I'm finding  Ubuntu Server to be a pretty interesting solution even for home use,  pretty solid. Once you get familiar with the terminal things get really  fast and fun. Heck, the fact that it's so lightweight makes it even more  appealing! Gotta check whether samba server runs smooth even  on a crappy old single-core Sempron 2400+ and 256MB DDR333. For home use it  should be okay.

---

### Post by dragonfly41 on 2016-04-03
[webmin]("http://www.webmin.com/") is installable from Ubuntu Software Centre and typically runs on [https://localhost:10000](https://localhost:10000)

But it might be more powerful than you need.

---

### Post by ian-weisser on 2016-04-03
> **lakeshore2985 said:**
> when one says "CLI", does it mean the same as WebUI access? Now I know  CLI stands for command line interface, so it's different than Web  interface. But it also says that CLI has to activate daemon, which in  turn also provides WebUI access? 

When I SSH to my server, I can do *anything*. It's a normal shell prompt.
When I check my application web page, I can change settings on that application only.

Try both to see the difference. Transmission, for example, does both very well.

Yes, you must start the application using SSH. After the application starts, it launches it's own webserver and makes it's WebUI available.
It's trivial to automatically start the application at boot or on a schedule, or to manually signal the system to launch the application. Many ways ot do it.

Tip: Experiment in a VM first.
Tip: If you use SSH, *always* use keys. Never passwords. Get in the key habit.
Tip: Never keep sensitive or personal data on an internet-facing server.

---

### Post by lakeshore2985 on 2016-04-03
> **ian-weisser said:**
> Yes, you must start the application using SSH. After the application starts, it launches it's own webserver and makes it's WebUI available.

Yes, but what I don't get is how does one start an application's WebUI interface (say Transmission for example) if Ubuntu Server doesn't have a graphical interface in the first place?

Let's say I SSH into my Ubuntu Server from a different computer, okay. I launch Transmission application in Ubuntu Server, all fine. But then Transmission doesn't come with its WebUI interface enabled by default, which means I won't be able to access it. So I figure the only way to do this is fiddling with the configuration files of these applications? Apparently it's the only way.

---

### Post by nerdtron on 2016-04-03
> **lakeshore2985 said:**
> Yes, but what I don't get is how does one start an application's WebUI interface (say Transmission for example) if Ubuntu Server doesn't have a graphical interface in the first place?

The GUI of the server is different from the WebUI interface of transmission. Think of the GUI of the server like a desktop PC and you're using a file manager to navigate onto the filesystem. The WebUI on the other hand is rendered by your own web browser (from your own PC, not the server).
> **lakeshore2985 said:**
> 
Let's say I SSH into my Ubuntu Server from a different computer, okay. I  launch Transmission application in Ubuntu Server, all fine. But then  Transmission doesn't come with its WebUI interface enabled by default,  which means I won't be able to access it. So I figure the only way to do  this is fiddling with the configuration files of these applications?  Apparently it's the only way.

Yes, you need to edit the Transmission configuration files to "activate" the web interface. Once the webGUI is activated, you can access the WebGUI by opening a web browser and typing the IP address of the server on the URL bar. Now, you'll be able to add your torrents.

---

### Post by ian-weisser on 2016-04-03
> **lakeshore2985 said:**
>  I figure the only way to do this is fiddling with the configuration files of these applications? Apparently it's the only way.

Well, that is the purpose of a configuration file. To change (and save) your settings...

You seem uncomfortable with the idea of controlling your server using the shell.
You're not the first. We have all been there.

Once you try it, you will discover that it's not difficult at all.
After a few experiments, you will realize just how limiting the GUI is.
There is great satisfaction in understanding how your system works.

---

### Post by SeijiSensei on 2016-04-03
It is possible to run graphical applications on the server and have them display on a client workstation.  This is called "X forwarding" since it uses the X Windows protocols that lie at the heart of the graphical Linux desktop.  Since the server does not come with a GUI installed, you need to install support for X.  According to [this thread](http://ubuntuforums.org/showthread.php?t=879877), all that's required is to log into the server via SSH and run
```
sudo apt-get install xauth
```

Once xauth is installed, you should be able to log into the machine using "ssh -X" instead of just "ssh".  Now if you run an application like Transmission from the terminal prompt on the server, its GUI will pop up on your client workstation.  I usually put apps that I run in this manner into the background so I regain access to the terminal prompt.  To do that just run:
```
transmission &
```
The ampersand puts the application into the background.  It can take a few seconds for the application to appear on your desktop so be patient.

---

### Post by The Cog on 2016-04-03
It varies from application to application. 

The most basic way to control server services is to provide them with command-line arguments to tell them what to do. If you want to change it, kill the process and start another one with different arguments. Next, you can leave a file with configuration details for the service to read. In both cases, the only interaction you have with the process is to kill it - there are commands you can run to kill a process. So there is no application GUI here. Apache falls into this category, I think.

Or can have a service that listens for connections and accepts control instructions over that connection. It's obvious with transmission - it has an inbuilt webserver and you talk to it with a browser. Some services come with simple command-line utilities that connect to the running process and send commands. With many services, they don't have a GUI at all other than the client part of the application. If the client connects to a server locally, you can't really tell that it's a two-part client-server pair. You just see a GUI running on the server controlling the application. 

If the service (file application, database server or whatever) is running on a headless machine like an Ubuntu server, then it is obvious when it's a two-part client-server system. And even local command-line control such as killing and restarting it is done remotely using an SSH connection. 

And yes, you may have to edit transmission's configuration file to enable the remote web GUI and then restart it. This is quite normal. Configuration like that doesn't change much and is left in configuration files. Operational running control is then effected over a network connection (like starting/stopping torrents in transmission). This is the way things have to be with headless servers. There is no windows-like assumption that the service must always have a local GUI because quite often there isn't even a video card in the server, let alone an attached keyboard mouse and screen.

---

### Post by lakeshore2985 on 2016-04-03
First off, thank you all for the replies!
> **ian-weisser said:**
> You seem uncomfortable with the idea of controlling your server using the shell.
You're not the first. We have all been there.

No, it's not that I'm uncomfortable with using the shell instead of GUI. Well it's more difficult yes, but much more fun and exciting indeed. Especially because the OS is so lightweight without a GUI... it drives me insane!

What kinda worries me is the fact that each application may have different sets of configuration files, and some may even not be possible to change settings manually at all (via config files). For example, Transmission is not the only P2P application I'll be running, so there is a chance I come across some software that completely unables me to have a CLI or WebGUI option. Then it defeats the purpose of having such lightweight operating system.

[QUOTE=SeijiSensei]It is possible to run graphical applications on the server and have them  display on a client workstation.  This is called "X forwarding" since  it uses the X Windows protocols that lie at the heart of the graphical  Linux desktop.  Since the server does not come with a GUI installed, you  need to install support for X.[/QUOTE]

That's some great piece of suggestion right here. Thank you very much!

My only concern though is whether that'll put a heavy load on the server, since the machine I'm planning to run this thing on is not really big on graphics; it has only an onboard SiS something from 15 years ago. But if it'll only run one instance of X for each individual application, then it may not be a problem.

---

### Post by HermanAB on 2016-04-03
The X heavy lifting will  be done by your local machine, the one you are logging in from.

$ ssh -X user@server "gedit filename"

Provided that the target program has all its dependencies installed, it will work perfectly fine.

---

