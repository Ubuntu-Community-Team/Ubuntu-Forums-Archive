---
title: "using the &quot;mail&quot; program how do I change the reply-to"
date: 2007-04-11
forum: General Help
---

### Post by netstv on 2007-04-11
I have a problem here.  I want to use cvsspam to send email out to everyone but our Linux usernames are different than our M$oft network names.

What I need to do is remap the replyto name:

I use just good old "mail" in the terminal window.

So what I currently do is this:

mail -s "Test" [email]engineergroup@mycompany.com[/email]
< fill in text>
Ctrl-D
cc: <no-one>

And the mail gets received by all the M$ users but the replyto address is [email]steve@mycompany.com[/email] which is wrong, it needs to be something else.

I'm sure there must be a switch to mail that allows for this.  Someone out there MUST know!!  

Thanks.
-steve

---

### Post by Jussi Kukkonen on 2007-04-11
*man mail* tells you this:
>      mail utilizes the HOME, LOGNAME, USER, SHELL, DEAD, PAGER, LISTER,
     EDITOR, VISUAL, REPLYTO MAIL, MAILRC, and MBOX environment variables.

I'd try setting the REPLYTO variable.

---

### Post by netstv on 2007-04-11
My version of mail doesn't have the REPLYTO.  Hmm.. I better check what version I am using.

BTW:  I did read man first... 

-stv

---

### Post by Jussi Kukkonen on 2007-04-11
Strange. I am running Feisty, but the version of mailx is actually pretty ancient (according to apt-cache the package is dated 20050715)...

---

