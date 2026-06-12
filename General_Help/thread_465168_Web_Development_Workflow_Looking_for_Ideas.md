---
title: "Web Development Workflow: Looking for Ideas"
date: 2007-06-05
forum: General Help
---

### Post by ebs16 on 2007-06-05
Hey,

I'm developing a complex site with a group and am looking to develop a server environment and workflow system to keep the project moving along efficiently.  I have a good deal of experience with Ubuntu Server and would like to base this environment on Ubuntu Server Fiesty.  I am not sure what other tools or methods are available to me.

We are developing on Windows XP machines both inside and outside the Ubuntu server's LAN.  I want to build a system that works well with Dreamweaver CS3's server functions and can integrate as seamlessly as possible with a version control system. I would also like to setup a wiki tool for collaboration and status tracking.  The server should also host a live preview of the site in its most current state.

I have a simple LAMP/FTP server setup for my solo development projects.  I have Dreamweaver upload automatically on save and can view my changes immediately through a browser.  I am looking to maintain a similar coding environment with a group, with the addition of version control.

While toying with ideas for a group dev environment, I threw together an Ubuntu Server system with subversion+webdav, apache, proftpd, and trac.  I understand how each of these tools work, but I'm not sure how to use them effectively in a development system.  Setting up WedDAV in Dreamweaver leads to ambiguous check in/out dialogs on each save and I can not have Apache host directly out of a svn repository. (I'm also not sure of exactly what happens on the server when Dreamweaver checks a file in or out.)  Furthermore, using FTP would bypass version control.

Additionally, I'm not sure how to properly configure Dreamweaver for this task.  What is the practical difference between a "testing server" and a "remote server" in the Dreamweaver site setup panel? Which should use FTP and which should use WebDAV?  I usually just setup a straight FTP connection for the remote server and nothing for the testing server.

How should I go about doing this? Is there a better way to do this? Am I completely missing something?

Also, can someone explain how subversion works in a group setting? I understand what the program does, I just can't seem to picture how a development group of this type would use it in practice when developing the same files.

This is long, but any help would be appreciated.

Thanks! :D

---

