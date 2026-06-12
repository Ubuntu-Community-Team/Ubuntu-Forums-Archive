---
title: "Root security"
date: 2007-05-26
forum: General Help
---

### Post by 5ER on 2007-05-26
I wonder if it's secure and safe to set all files of my computer to be viewable and editable by everyone. I'm the only user of my computer.

---

### Post by Bachstelze on 2007-05-26
Of course it's not ! That's the whole reason there's a root user in the first place...

---

### Post by aysiu on 2007-05-26
The files in your home folder are *not* editable by anyone

And there are some system files (like /etc/shadow) that are not viewable by anyone.

Of course, if someone has physical access to your computer, she has root access too, for all practical purposes.

---

### Post by rillip on 2007-05-26
With a default setup, a hacker cannot use your root account, since it isn't enabled with a usable password, access is controlled only through sudo.  They have to guess your username and password.

If you set it so that everyone has access to read and write, they still have to guess that information to login, but once they login, they can do whatever they want with any of the files.

Of course, if they get loged in, they can just set up a root password and do whatever they want anyway.

I don't see any increased risk if you're just using it as a desktop, because you still have to get past the gatekeeper.  If you're running any kind of webservice like http, I definitely would not do this, as this makes it trivial to put a file there that can overwrite whatever it wants if they all have write by everyone.

Everyone I've seen who makes a post like this is often concerened about local security.  Unless you've got your case locked, your bios password protected, and your case attached to an imobile fixture, local security is pointless.  They can just boot into single user mode, or slave the drive and pull everything off, or just take the drive take their time hacking it, etc.  The password/read/write system is only for a very rudimentary, casual sort of protection that really isn't worth thinking about unless you have serious trust issues with people in your house.

---

### Post by TheWizzard on 2007-05-26
> **5ER said:**
> I wonder if it's secure and safe to set all files of my computer to be viewable and editable by everyone. I'm the only user of my computer.

are you serious? it is both insecure and a guarantee for you to break your system. 

why would you want this? please explain.

---

### Post by 5ER on 2007-05-26
> **TheWizzard said:**
> are you serious? it is both insecure and a guarantee for you to break your system. 

why would you want this? please explain.

Less sudo, less kdesu, less having to run a new window to go fix something instead using tabs.

I'm not concerned about local security, I just to be safe from hackers, but I don't know why that would be easier to hack, although I heard it is.

---

### Post by aysiu on 2007-05-26
Wow! I totally missed that.

When I read the original post, I assumed 5ER was criticizing the way Ubuntu is currently set up.

Reading it again, though, with TheWizzard's response, I see 5ER wants to change the setup to make it so that every file is viewable and editable by everyone.

I agree with TheWizzard, then: hell, no! Don't do it. It will break your system. Permissions are there for a reason.

---

### Post by aysiu on 2007-05-26
> **5ER said:**
> Less sudo, less kdesu, less having to run a new window to go fix something instead using tabs.

I'm not concerned about local security, I just to be safe from hackers, but I don't know why that would be easier to hack, although I heard it is.
Konqueror has an *edit as root* context menu. If not, you can use Adept to install the Konqueror plugins so that you have that context menu.

You can also [change the *sudo* timeout](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo). There is an option to make it infinite (in other words, to never ask for your password again after the first time).

Alternatively, since you appear to have no regard for security, you could enable the root account by setting a password and changing the KDM settings to allow a root login.

But changing permissions on every file and folder in Kubuntu *will* break your system and render it unusable.

---

### Post by rillip on 2007-05-27
I'm not trying to argue the point, but as long as the permissions are being escalated, how will it break?  As you might guess, I'm not really willing to try it out myself, I'll take your word for it... :p

---

### Post by TheWizzard on 2007-05-27
> **rillip said:**
> I'm not trying to argue the point, but as long as the permissions are being escalated, how will it break?  

1) the user (you) 
2) a software bug

---

