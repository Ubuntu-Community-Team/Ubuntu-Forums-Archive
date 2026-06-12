---
title: "hotwayd in breezy ubuntu?"
date: 2005-11-02
forum: General Help
---

### Post by kirmonkey on 2005-11-02
Afternoon all,

Since upgrading to breezy in ubuntu I have had problems configuring hotwayd to collect my hotmail messages. (worked well in Hoary)

Telneting 127.0.0.1 110 gives the error message 

```
rick@trevor:~$ telnet 127.0.0.1 110
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
Connection closed by foreign host.

```

My main question is. Has anybody else had the same problem, if so then it's a config error and if not then it's my neglect and I will compose a proper post to this forum dealing with that.

---

### Post by Kyral on 2005-11-02
Uhh....is it supposed to be connecting to the local loopback address?

---

### Post by kirmonkey on 2005-11-02
Ah.....  following the guidence here:

[http://hotwayd.sourceforge.net/e107_plugins/custompages/Install_inetd.php](http://hotwayd.sourceforge.net/e107_plugins/custompages/Install_inetd.php)

I cannot currently conect to confirm.

 It relates to configuring hotwayd for inetd and one of the stages in that process is to connect to 127.0.0.1 110

This is a part of the configuration instructions but I am, as I say, unable to access the site at the moment.

Someone had the same problem in 5.04

[http://www.ubuntuforums.org/showthread.php?t=28748&highlight=hotwayd](http://www.ubuntuforums.org/showthread.php?t=28748&highlight=hotwayd)

....

---

