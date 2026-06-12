---
title: "After replacing motherboard and drive, svn+ssh:// no longer works"
date: 2015-03-06
forum: General Help
---

### Post by steward2 on 2015-03-06
Forum newbie alert. If this is not the right way or place to post please do not shoot me ;)


Ubuntu 14.04.1 LTS

I had my PC and disk drive replaced. The tech copied the old drive, everything booted and worked great.

Except that I can no longer use svn+shh://my.server.com/home/svn/repos/blah to access my source code. 

ssh "-p 2332 " [EMAIL="me@myserver.com"]me@myserver.com[/EMAIL] still works.  So it seems SSH is okay (?).

Local checkout (file protocol on server) checks out okay. SVN is working.

So if ssh and svn are working, I don't know where to start. I am terrified of breaking ssh login.

It makes sense to me that I might need to regenerate a key, if it used the hardware somehow to seed itself. But I cannot work out what I need to change, or how to debug to confirm what I need to change....  not a great deal of ubuntu expertise here.

Have opened port 3690 on firewall. Unsure how to test I succeeded.


Thank you

---

### Post by ian-weisser on 2015-03-06
Does it fail silently?
Do you get any kind of error message? If so, what does it say?

---

### Post by steeldriver on 2015-03-06
Hello and welcome to the forums

Do you get any error messages?

Did the tech remember to copy the hidden files and directrories in your home directory? it sounds like you no longer have an appropriate svn+ssh definition (including the non-standard port - and login name if different) in the [tunnels] section of your ~/.subversion/config file

---

### Post by steward2 on 2015-03-07
Thank you for your responses.

Opening up port 22 solved the problem.

The tech had never set the port number in the subversion config tunnels section, and the original firewall had 22 open.

So I only thought I was using port 2332 for ssh :(

Now I can correct the config.

---

