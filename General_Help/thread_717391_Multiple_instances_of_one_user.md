---
title: "Multiple instances of one user"
date: 2008-03-07
forum: General Help
---

### Post by Front187 on 2008-03-07
My question is this:  Can multiple instances of the same user be logged into Ubuntu at once?

If yes, is it possible with the default settings?

For the curious:

I want to know because currently my campus IST club is doing a series of linux lectures.  However, the campus computers all use Windows.  I want to give a talk about the linux filesystem, and I figure the easiest way would be to create a single virtual machine that everyone has access to, install VMPlayer in the shared directories of the campus computers, and allow everyone to logon to the same virtual machine with the same name with read only privileges.  

Feasible?  Better ideas?

---

### Post by randomnumber on 2008-03-07
It sounds like you want people to see your desktop. If this is the case you could set up VNC with view only permissions.

Honestly if this is your desire, projectors in the class are a more ideal solution. You will probably have troubles convey to everyone how to set up the login otherwise.

If these people need access to the computer for their own purposes it will likely be best to set up each their own account.

Multiple logins can be accomplished through ssh but multiple x sessions(graphical) are more difficult but possible. xdmcp may also be of interest, it allows multiple users to login graphically. 

Please describe what you would like to do, what your goals are.

---

### Post by Front187 on 2008-03-07
My ideal solution would be something that requires a disposable amount of effort to setup.  Quick and dirty, if you will.

I just want a small group of people (20 or so) to be able to use the command line as I interactively guide them through the linux filesystem.

EDIT:

To clarify, it is in a classroom environment.  All computers are shared and networked to a server.

---

### Post by Front187 on 2008-03-07
bump

---

### Post by murataht on 2008-03-07
So, as randomnumber says, if they just use command line, then use ssh to connect to the server.

---

### Post by randomnumber on 2008-03-10
You should be able to set-up ssh and have everyone log in. I do not know if there is a limit to how many can log in but that should be able to be changed if you run into that problem. It would be in some file off options and after you change the file you would need to restart the service ( reboot),

There are all kinds of tutorials. If you are using windows machines to login to the linux machine you will need something like putty. I think it is at <http://www.chiark.greenend.org.uk/~sgtatham/putty/>.



Anyway good luck.

---

