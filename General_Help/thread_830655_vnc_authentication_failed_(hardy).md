---
title: "vnc authentication failed (hardy)"
date: 2008-06-16
forum: General Help
---

### Post by sonicb00m on 2008-06-16
I tried to change the port and enable authentication via the remote desktop gui. It didn't work so I turned off authentication and put the port back to default.

Somehow though, my configuration has become trashed because, typically, I cannot access my desktop now with the settings I had before. I suspect it is still expecting authentication because I get an authentication to host failed message.

How can I undo the mess created by a simple gui and get it working again?

---

### Post by sonicb00m on 2008-06-20
someone?

---

### Post by lightstream on 2008-06-20
Not quite sure what you're saying - you mean you have a VNC connection to a remote machine, and using VNC you tried to change the port and authentication settings in the VNC client on the remote machine?

Now you've tried to set the remote machine's VNC settings to what they were originally (ie no authentication and default port), and you can no longer access that machine by VNC?

Can you not access the remote machine directly any way and sort it out locally?

---

### Post by sonicb00m on 2008-06-21
No, I mean I have a machine with a vnc server installed and enabled encrpytion and a port changed. Then I couldnt connect any longer using a remote viewer on a different machine. After putting the settings back to default on the vnc server, i still cannot connect with my remote viewer. I get this authentication error message by the remote viewer, despite putting the port back to 5900 on both the host and the remote viewr.

---

### Post by law826 on 2008-08-09
It seems that I am having the same problem.  Did anyone happen to find out how to fix it?  Thanks!

---

### Post by Gohalien on 2008-08-09
Same problem here, trying to access from my notebook to my desktop computer, I configure the password correctly and it says authentification failed.

---

### Post by hydrogennz on 2008-09-02
In the password field for Remote Server, try holding down the backspace key for a while, even after the * characters have been deleted.

It seems like there is a bug when changing passwords in that the old one doesn't get overwritten correctly.

---

### Post by tregora on 2008-10-20
That is a strange bug, I couldn't beleive it actually worked.  Thanks hydrogennz.

---

### Post by LarryJ2 on 2008-12-06
Thanks also from me,  hydrogennz.   As of December 6, 2008 in  2.6.24-22-generic  and Hardy Heron 8.04,  this bug still exists.  

So if you get the failed to authenicate from your remote machine, log into your local desktop, then System->Preferences->Remote Desktop,  position your cursor in the password edit window and lay down on the back space key until it squeals.

LJ

---

### Post by Browner87 on 2009-02-13
Wow. I can't believe it worked either :P

Thanks man!!!!!

:guitar::lolflag::popcorn:

---

### Post by prymus on 2012-10-09
It's worth noting that using vino-passwd on the command line will make it work every time!

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

