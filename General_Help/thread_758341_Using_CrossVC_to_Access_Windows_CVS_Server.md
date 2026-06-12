---
title: "Using CrossVC to Access Windows CVS Server"
date: 2008-04-17
forum: General Help
---

### Post by jeremy_watkins on 2008-04-17
I am attempting to access a cvs server that resides on a remote windows server (cvsnt).  I am using CrossVC on Ubuntu as my cvs client of choice.  The cvs server has been set up with a server name of "cvs", and a repository named "/cvs".  I have not yet been able to successfully access the server from Ubuntu.  I have entered in the following when attempting to checkout a module:

User:  [windows user that runs the cvs server]
CVS Server:  [domain]:[port]
CVS Repository:  /cvs
CVS Access: SSPI

I click on the "Browse Modules" button, and it prompts me for a password (I assume this means it is able to reach the server).  I enter the password for the windows user, but it says "Login Failed".

I can't seem to be able to figure out the correct information to enter.  Either I have set up CrossVC incorrectly or I have set up the server incorrectly--I'm really not sure which at this point.  I use CrossVC at work, but I haven't ever done the server setup for a CVS server before.

Any help would be greatly appreciated!

---

### Post by jeremy_watkins on 2008-04-19
I solved the problem.  The guide I was using failed to state that some command-line work is necessary after setting up CVSNT.  If anyone else suffers from this problem, run these two commands:

set cvsroot [directory for cvs repository, in my case C:\cvs]
cvs passwd -r [windows user] -a [cvs username you wish to give that user]

You will then be prompted to create a password for that user.

---

