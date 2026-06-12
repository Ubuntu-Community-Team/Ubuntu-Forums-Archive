---
title: "SSH on Box startup"
date: 2008-02-12
forum: General Help
---

### Post by CrazyEyesITGuy on 2008-02-12
Hello,

I have limited space for my Windows Sever, Linux 7.0.4 server especially when your talking about 2 monitors/keyboard/mice/desks, ETC.  

i would like to be able to set up my Linux box so that when i turn it on i can go to one of my other workstations and VNC into the Linux box with having to wait and put usrname and password in so the box loads the OS.  

is there any easy way to start SSH prior to the log in of a user?

any help on this or a link to something a Linux Noob would understand would be awesome.

peace.

---

### Post by zozobra on 2008-02-12
If the latest version of OpenSSH is installed, you'll be able to ssh into it without anyone actually having to go to the PC and log in.

---

### Post by dmizer on 2008-02-12
if you have openssh-server installed, you don't have to be logged in locally in order to log in via ssh.  it's been like that for many years in order to provide access to headless servers.

you should also be able to log in to vnc without having to be logged in locally, but i can't confirm that for sure.

note: the box doesn't "load the os" after you log in.  the os is already loaded.

---

### Post by Origin415 on 2008-02-12
VNC needs a user to be logged in, if you are committed to a GUI (for a server, its only going to create overhead), you should look into FreeNX or X forwarding over SSH.

As was mentioned before, if SSH is all you want, it is loaded automatically during boot if it is installed.

PS - Look into a KVM switch to avoid the two monitor/keyboard/mouse issue. I have one that switches using the same set to control my desktop, server if necessary, and laptop if docked.

---

### Post by CrazyEyesITGuy on 2008-02-13
Do I need to load a specific program on my XP machine to allow the SSH connection to the Box take place?  Can i use the Remote Desktop Connection?

Should i dump the GUI interface and just run from Command Line  the GUI seems to be the root of the problem.

---

### Post by nemilar on 2008-02-13
If you want to run graphical applications over the network on your windows machine, using the Linux machine as a server, you need to install an X11 server on the windows machine.

[See this page]("http://www.techthrob.com/tech/ssh101.php") for more info; there is a link to a free X11 server for windows at the bottom.

---

### Post by dmizer on 2008-02-13
> **CrazyEyesITGuy said:**
> Do I need to load a specific program on my XP machine to allow the SSH connection to the Box take place?  Can i use the Remote Desktop Connection?
no, you cannot use the remote desktop connection.  you must use a separate program to ssh to your ubuntu machine.  one of the most popular windows ssh programs is putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

> **CrazyEyesITGuy said:**
> Should i dump the GUI interface and just run from Command Line  the GUI seems to be the root of the problem.
i think the answer to this question will largely depend on what you intend to do with your server.  if you intend to serve web pages, it is preferable to have as minimal setup as possible so as to avoid providing hackers in-routes to your machine.  i had to learn this the hard way after my own web server was hacked.

---

### Post by CrazyEyesITGuy on 2008-02-13
This server is really intended as a learning experience.  i would like to set up a DNS and LAMP on the same box... is this even possible?  after that i want to use the DNS as part of the Win 2k3 domain controller running active directory.  

i'd like to use the LAMP as learning tool for the MySQL and PHP to write code, build databases and maybe even collect some data from a website...

i may not have mentioned this before but this is my first experience with linux.  i've had this ubuntu 7.0.4 server up and running for a total of about 3 hours maybe..

i've got putty working fine,  i can get right in to a command prompt but i can't display the desktop to log in?

---

### Post by dmizer on 2008-02-15
> **CrazyEyesITGuy said:**
> This server is really intended as a learning experience.  i would like to set up a DNS and LAMP on the same box... is this even possible?
possible, yes.  but:

if you are planning to allow your LAMP server to be visible to the internet, it's hyper-critical that you only have the bare minimum resources available on the web server.  (no gui, no DNS, no active directory, no shares ... nothing except bare bones linux, apache2, mysql, and php4 or 5 as needed).  otherwise, you run the extreme risk of your entire network being compromized by a simple mistake in your php/html code, or in your mysql scripts, or by an unpatched security hole in php, apache, or mysql.

here's what happened to me because i had too much going on my own web server: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

putty will not allow you to display the desktop login.  ssh and putty are text only interfaces.  this may seem daunting at first, but since most servers do not have a gui anyway, you'll find that most server howtos only have directions for the command line.

i strongly suggest that you make the effort to work with the command line as much as possible while learning to configure a server.  especially since you are just learning and everything is fresh, i suggest learning it correctly the first time instead of having to re-learn it later.  especially since you are planning on having this server be headless.

if you insist on using the gui, you will also have to configure it for vnc ... and i am not familiar with how to do so.  however, there are lots of tutorials on this forum as well as in the community documentation pages.

---

