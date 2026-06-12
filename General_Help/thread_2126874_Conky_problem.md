---
title: "Conky problem"
date: 2013-03-18
forum: General Help
---

### Post by rob62158 on 2013-03-18
I installed conky on Ubuntu Syudio 12.10 it worked fine then as I start it I get this message.
I've removed and reinstalled with both the Ubuntu Software Center, Synaptic Package Manager, and in a terminal.
Here is the error.
charlie@charlie-K53TA:~$ conky &
[1] 6131
charlie@charlie-K53TA:~$ WARNING: gnome-keyring:: couldn't connect to: /run/user/charlie/keyring-ch1TMh/pkcs11: No such file or directory
Conky: invalid configuration file '/home/charlie/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

Any help wiyh fixing this would be appreciated.
Thanks

---

### Post by stinkeye on 2013-03-18
Have you had conky running and now doesn't or
is this your first time running?

See this recent post by Sector11.
[http://ubuntuforums.org/showthread.php?t=1998123&p=12562387&viewfull=1#post12562387]("http://ubuntuforums.org/showthread.php?t=1998123&p=12562387&viewfull=1#post12562387")

---

### Post by rob62158 on 2013-03-18
I ran it once after install, but now this is all hat happens when i try to start it.
I'll try the info in the link and see if any of it helps.
Thanks

---

### Post by rob62158 on 2013-03-18
I got it fixed.Re: Conky problem
I installed ImLib2Dev. and re did the conky files and folders in my home directory.
It fixed the problem.
Thanks for the help, it got me thinking in the right direction.

---

