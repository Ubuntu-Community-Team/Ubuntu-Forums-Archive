---
title: "Command Line alternatives?"
date: 2007-02-10
forum: General Help
---

### Post by dwest on 2007-02-10
Hi,
I'm a total newbie to Linux. I'm an experienced web developer but I've been all windows for 15 years.  Now I'm moving to PHP/Linux for development hosting of my clients' sites.

I have a VPS with ubuntu edgy installed.  I also have two shared reseller accounts.  I have access to a some BASH scripts which will utilize the VPS to manage replication of all the sites on the primary reseller account to the secondary reseller account and keep them sync'd.

It is the installation and configuration of these BASH scripts which is making me realize my total lack of experience with the command line and Linux in general.

So, my question is this:

I've been made aware of Yum and Nano (don't have a clue what they are) and that I need "use" them.

Is there some sort of software or interface, other than the command line, to control and manage files and folders in ubuntu?  Dare I say, similar to windows?

As you can tell by the question, I'm quite confused :)   Any guidance, aimed toward minimizing the learning curve, would be greatly appreciated.

Thanks!

---

### Post by meng on 2007-02-10
A lot of things in Linux these days can be done in a GUI environment much like Windows. In addition, beneath the surface there are commands such as apt-get for software package management (not yum, that's for another flavor of Linux) and text editors which run in the console (nano, vi, emacs). What I would recommend is that you try out the Live Desktop CD for Ubuntu and see if you like it. If you do, go ahead and install it. Then feel free to ask for any help here, but keep in mind that not every distro of Linux is quite the same, they rely on a different selection of tools. So some of what you've heard may be true for Ubuntu, and some not. Don't assume!

---

### Post by dwest on 2007-02-10
Thanks meng.

Ubuntu is already "liked" as I have no other choice and being a total newbie I don't know where to begin evaluating the differences anyway. :) 

So, where would I learn such elemental things as:

While in putty, how do I start nano?
While in putty, how do I determine if nano is even installed?
Is there an alternative to putty (even if not free) that makes all this a hell of a lot easier to understand and actually do?

Is there a resource for learning the answers to simple questions like these?

All suggestions welcome!

---

### Post by gradedcheese on 2007-02-10
to start nano, type 'nano' and press Enter :)  To see if it's installed, "which nano" (works for any command of course).  PuTTY is an SSH client, basically.  I'm assuming you've ssh'ed into a Linux box from a Windows PC?  ssh is just a standard for a secure shell login.  The shell is the same, no matter how you get to it.  However, bash is very powerful and has features that DOS could never even imagine.  The tab completion, for example, is very nice.  You should probably pick up a general book about the shell (or look online) and learn a bit about it.  If you want to learn a real text editor (vi or vim), run 'vimtutor' and take the lesson.

You can manage just about everything from the GUI.  It's not really the UNIX way, but you can do it.  Managing a server via SSH login is much more efficient, once you know what you're doing.

---

### Post by meng on 2007-02-10
Confessions first: I've never used putty, although I have connected to remote machines over ssh.

Assuming that putty gets you to the command line okay, then you could simply type:
nano --version

to see if nano exists (and which version it is)

you start nano by typing:
nano

or, if you have a filename in mind already
nano [name of file]

if you're connecting to a remote machine FROM an Ubuntu system, I might recommend doing it this way:
ssh user@hostname/IP

Now I might have misunderstood your setup or what you are trying to do. If so, just let me know!!

---

### Post by dwest on 2007-02-10
gradedcheese, thanks and you are correct, I've ssh'd into my vps using putty.

Are there alternative ways of accessing my vps and working, which are not command line oriented?  Is there a graphical putty?

---

### Post by Maestro23 on 2007-02-10
Here's a few links to get you going:

How to Install Anything in Ubuntu: [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Ubuntu Intro/How-To by Psychocats: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

RootSudo-- Why we use it: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There are many more as I'm sure other people will post.

---

### Post by gradedcheese on 2007-02-10
> **dwest said:**
> gradedcheese, thanks and you are correct, I've ssh'd into my vps using putty.

Are there alternative ways of accessing my vps and working, which are not command line oriented?  Is there a graphical putty?

You can use VNC to get a remote graphical login.  Either install vncserver or turn on remote login in Administration->Login Window (remote tab).  You can then use vncviewer (for Windows, there are several, one is at realvnc.com I think) to log in.

---

### Post by dwest on 2007-02-11
meng, thanks!  I've confused you (along with me :-) )

I'm using a Windows desktop.
I'm accessing my vps using putty.
The end desire is to install some bash scripts and configure them.  The I'll be done with my vps...it will just run the scripts forever.

I'm finding the adjustment to a command prompt to be, as Daniel Boone would say, bewildering.

This is because I am totally unfamiliar with what software that lies behind the command prompt. There is no graphical representation of what is on the server software wise. :-)
Nor do I know any of the commands by which to "see" what is there.

Sooooo, where is a resource to learn the commands, or is there a graphical interface version of a "putty like" piece of software I can install in windows?

---

### Post by dwest on 2007-02-11
gradedcheese, thanks!

I'm familar with vnc.  So you are saying I can install it on my linux (ubuntu) vps and then access it from my windows desktop to get a graphical representation of what is on the vps?

---

### Post by dwest on 2007-02-11
Thanks Maestro23!  I'll have a look at those when the thread settles a bit.

---

### Post by meng on 2007-02-11
I think I understand what you are trying to do now.
There are plenty of resources out there, the only question is what would suit you best.
If you have a graphical environment installed on your VPS (i.e. if you did not just install the server edition) then you can use vncviewer or something like it to run a graphical desktop remotely. This may be slow if the upload speed on the VPS is slow, but hopefully this is not a problem for you.

If you don't have a graphical environment installed on the VPS, but you need one, consider running this command on it:
sudo apt-get install ubuntu-desktop

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.karakas-online.de/gnu-linux-tools-summary/](http://www.karakas-online.de/gnu-linux-tools-summary/)

---

### Post by dwest on 2007-02-11
meng,
Well, the install was for "ubuntu standard".  Is there a way to detemine via the command line is I have the graphical interface installed?

The VPS is basically intended to be a website host BTW.  So it may well be that only the server version was installed.

---

### Post by meng on 2007-02-11
*shrug* (I initially wrote a response, but I wasn't sure so I deleted it) :D

---

### Post by dwest on 2007-02-11
I found this and I think it is what I'm looking for...I'll try it and see.
[http://winscp.net/eng/docs/introduction]("http://winscp.net/eng/docs/introduction")

Any other comments are welcomed!
Thanks to all.

---

### Post by koenn on 2007-02-11
> **dwest said:**
>  Is there a way to detemine via the command line is I have the graphical interface installed?
a graphical interface would depend on the "X" window system so you can check if that is installed by running
```
which xinit
``` or ```
which startx
```
If they return a path, like /usr/bin/xinit, X is installed. It does not mean it's running - servers usually don't run a GUI. 

> consider running this command on it:
sudo apt-get install ubuntu-desktop
I wouldn't do that. ubuntu-desktop includes the standard ubuntu desktop apps such as openoffice e.a. - it would be overkill
It's possible to add a GUI to an ubuntu server install by installing xorg, gdm, metacity, gnome-panels, gnome-menu etc, then add any application you like. I've done that before and can look it up, but I believe it's better you try vnc and see how far you get.

---

### Post by reclusivemonkey on 2007-02-13
While you get to grips with things, you can use Midnight Commander for file management and various other things. If its not installed, just

```

sudo apt-get install mc

```

[http://www.ibiblio.org/mc/images/mc-panels.png](http://www.ibiblio.org/mc/images/mc-panels.png)

If you are serious about using GNU/Linux, you will be well served by learning at least the essentials of the command line; particularly if you are into web development. X is not always installed on servers and is indeed a waste of resources on a web server. RUTE is a good place to start;

[http://rute.sourceforge.net](http://rute.sourceforge.net)

If you want a book, there's no better introduction than O'Reilly's "Linux in a Nutshell";

[http://www.oreilly.com/catalog/linuxnut4/](http://www.oreilly.com/catalog/linuxnut4/)

---

