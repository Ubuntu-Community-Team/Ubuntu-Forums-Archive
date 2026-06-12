---
title: "PHP GD2 imagerotate function"
date: 2006-12-01
forum: General Help
---

### Post by phfeenikz on 2006-12-01
Having tried both PHP4 and PHP5, neither have the imagerotate function.  When trying to use the function, I always receive an error saying imagerotate() is an undefined function.  I've searched the threads for this and none of them have been resolved.

To stave off the usual replies, yes I have uncommented extension=gd.so in the php.ini file.  Yes, I can in fact see that GD is showing up on the phpinfo() function, and the version states that it is "2.0 or higher".  In fact, every other function from the GD module that I use works great, with exception to imagerotate().

My question is can anything be done to resolve this?  If so, how, and if not, why?

---

### Post by bdk6m2007 on 2008-03-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/39719](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/39719) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Doesn't look like ubuntu will ever support this b/c of upstream security issues.  See the Launchpad bug.  :(

---

