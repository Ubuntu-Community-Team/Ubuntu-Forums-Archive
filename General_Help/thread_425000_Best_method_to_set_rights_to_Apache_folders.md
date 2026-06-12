---
title: "Best method to set rights to Apache folders?"
date: 2007-04-27
forum: General Help
---

### Post by the_nite_owl on 2007-04-27
Hi All,
I am a semi-newbie to Linux and this might be an easy question.

I installed Ubuntu 7.04 x86 64 server in a LAMP configuration, then added in the Ubuntu (gnome) desktop gui.

I am trying to setup Apache and want to copy the web site files from my Windows Apache setup.
The problem is a common one I know, I am logged into the GUI and my account is not the owner of the folders Apache is installed in so I cannot modify them.

I will have to access these folders often as I work on the pages, create new folders, etc.  What is the best way to gain access to them from the GUI?  I am not experienced enough to do everything from shell and I want to use GUI apps to create and publish files to the folders.  
I also want to be sure any permissions/ownership changes I make will not affect the normal operation of the server.

I know this must be a common issue, is there a prefered method for dealing with it?

BTW, I have installed Webmin to help me configure the server but since I was unable to create the folder I want to migrate my pages into I have not even begun configuring Apache to point to the folder.

Thanks.

---

### Post by rturner on 2007-04-27
I'm not experienced in a gui interface to accomplish that, except for something like a gui ftp app like gftp where you can right click on the remote interface and select chmod or make directory.

The easiest way for me to do this is from the command line in your home directory.

mkdir ~/public_html
sudo ln -s ~/public_html /path/to/apache//htdocs/$USER

That creates a folder on your server that you can ftp into under your username/password from other computers and load up files, make new directories and change permissions.

Use the mkdir command to create a directory called "newsite" in your webspace:
cd ~/public_html
mkdir newsite

Then you can load files into the newsite folder.  I don't have time at the moment to write down the chmod command for easily setting permissions for owner, group and others.  If you use the gui in gftp, it's probably self-explanatory, or I can add more later.

---

### Post by az on 2007-04-27
> **the_nite_owl said:**
> 
I know this must be a common issue, is there a prefered method for dealing with it?


On a production server, you don't really want the folder used for the apache documentroot to be writeable by apache -  that is a security risk, which can allow someone to compromise any host on your system.  You can write to the folder using sudo, or you can chown the folder to another group (not the webserver www-data group), make the folder writeable by group and add your user to that group.

If this is just a test server, make it world-writeable and go crazy.

---

### Post by the_nite_owl on 2007-04-27
Both ideas have merit.  There is much I still do not know about Apache so it is hard to determine the best course.

The server is essentially just a play environment for me to learn on and also for me to do some development work for a local middle school whose site I have helped to re-design.  It will however be accessible from outside so still needs to be secure.

I am trying to learn enough to migrate my server away from a Windows environment completely to Linux.
For now I have to dual boot so that I can still do the things I only know how to do in Windows.
All other devices in the house are Windows based so I would need to access the server locally in order to learn and use all the other tools I will need such as programming tools.   I could still perform those functions under a Windows OS but that would defeat the purpose.  
So I would be developing on the same box as the Apache server and will need to find a solution that supports that need.

I think I will work on reassigning ownership to another group.  Setting up FTP access will be a useful as well as I get more familiar it but is one more learning experience I will have to take on and I have to get past the Apache setup first.

Thanks for the info guys.  I will poke around and see what I can do.

---

### Post by az on 2007-04-27
> **the_nite_owl said:**
> All other devices in the house are Windows based so I would need to access the server locally in order to learn and use all the other tools I will need such as programming tools.   


You can ssh into your linux box from windows using Putty.

Just install ssh on the server and administer it from anywhere you want.

---

