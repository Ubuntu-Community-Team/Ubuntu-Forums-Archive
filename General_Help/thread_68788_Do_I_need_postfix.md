---
title: "Do I need postfix?"
date: 2005-09-24
forum: General Help
---

### Post by blackant on 2005-09-24
I am using ubuntu as a personal desktop.
And recently I notice there is postfix installed in my box.
Since i am not running a mail server.. do I need it?

I try to uninstall, and there is quite a list of other packages which linked together with it.
Is it safe for me to remove postfix?

Thanks.

---

### Post by drogoh on 2005-09-24
[QUOTE=blackant]I am using ubuntu as a personal desktop.
And recently I notice there is postfix installed in my box.
Since i am not running a mail server.. do I need it?

I try to uninstall, and there is quite a list of other packages which linked together with it.
Is it safe for me to remove postfix?

Thanks.[/QUOTE]


1.  Yes, the underlying system will send mail regardless of how you use it and interrupting that can cause Bad Mojo Things(tm) if you don't disable each and everything that will send e-mails around the system.  It's best to leave it alone.

2.  No, see above.

---

### Post by mlomker on 2005-09-24
> 
Since i am not running a mail server.. do I need it?


Probably not.  I've heard some arguments for using it on a desktop but I don't see the value.

It's better to just disable the scripts and leave the files on your machine.  The following commands disable postfix and the software RAID components, since these are mostly server services.

```

sudo update-rc.d -f postfix remove
sudo update-rc.d -f mdadm-raid remove
sudo update-rc.d -f mdadm remove
sudo update-rc.d -f lvm remove

```

---

### Post by blackant on 2005-09-24
hmm.. since there is no confirm answer then i shall just leave it.

---

### Post by John.Michael.Kane on 2005-09-24
[http://www.postfix.org/features.html](http://www.postfix.org/features.html)

[http://en.wikipedia.org/wiki/Postfix_(software](http://en.wikipedia.org/wiki/Postfix_(software))
[http://postfixwiki.org/index.php?title=Main_Page](http://postfixwiki.org/index.php?title=Main_Page)
[http://software.newsforge.com/article.pl?sid=04/10/14/1648251&tid=74](http://software.newsforge.com/article.pl?sid=04/10/14/1648251&tid=74)

hope this helps

---

