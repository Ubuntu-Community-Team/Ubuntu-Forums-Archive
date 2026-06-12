---
title: "Problems using Subclipse with Eclipse in Dapper Drake"
date: 2006-10-06
forum: General Help
---

### Post by tdn on 2006-10-06
Hi

I am not sure I am posting this in the right forum.  If not, please tell me where to post it.

I have a problem with using Eclipse and Subclipse in Dapper Drake.

I have installed Eclipse via apt-get install eclipse. I have installed Subclipse from the update-manager.

When I am trying to set up a repository location ([https://svn.adora.dk/svn/tdn-diku-distsys](https://svn.adora.dk/svn/tdn-diku-distsys), which *is* the URL to a repository)I get this error: 
``Error validating location: "org.tigris.subversion.javahl.ClientException: svn: PROPFIND request failed in '/svn/tdn-diku-distsys'
svn: SSLv3"
Keep location anyway?''

I only have this problem in Ubuntu. Actually only in Ubuntu Dapper Drake.
I have tried this on two different installations of Ubuntu Dapper Drake. And it does not work. 
I have tried this in Windows and it works.

I also tried this in an earlier version of Ubuntu and it worked. In Debian it works too.

Can you help me fix this?

---

### Post by antspants on 2007-10-04
have you installed libsvn-java libsvn-javahl?

Probably a bit late for you :(

---

### Post by tdn on 2007-10-04
Antspants: Thanks for your reply.
Yeah. It is a bit late. I do no longer use Eclipse :(
And I don't remember if I had that package installed.

---

