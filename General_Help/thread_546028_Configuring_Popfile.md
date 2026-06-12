---
title: "Configuring Popfile"
date: 2007-09-08
forum: General Help
---

### Post by gavinjb on 2007-09-08
Hi,

I have just installed popfile through package manager and can access the web interface [http://localhost:7070](http://localhost:7070), but my problem is that my email account requires SSL, so after looking at the details on the popfile account I have entered the following in the security tab on the popfile web interface

Remote Pop3 Server: pop.mail.yahoo.co.uk
Remote Pop3 Port: 995

and entered the following in Evolution

Server address: 127.0.0.1:7071 (as 127.0.0.1 doesnt work, even with non secure servers)
Logon mail.yahoo.co.uk : ubuntu.forums

But when I do this can click on the check for mail all I get is the message saying Waiting.


Has anyone got any ideas.

Thanks,


Gavin,

---

### Post by dndrich on 2007-09-09
Yes.  What you need to do is to configure POPFile to use SSL.  Go to the POPFile homepage, and you'll find it.  Basically, you have to download a few Perl libraries by hand, and install them by hand.  To see how to do this, look at the instructions on the how to install in Mac OS X.  But in any event, what you will then do is configure your email to have the server as localhost, and then to configure the username as outlined in POPFile instructions, with an SSL at the end.  If you read on their site, you will see how to do this.  It does work.

---

