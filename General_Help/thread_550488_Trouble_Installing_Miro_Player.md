---
title: "Trouble Installing Miro Player"
date: 2007-09-13
forum: General Help
---

### Post by shear on 2007-09-13
Hi guys.

I'm trying to install Miro Player into 7,04. I have installed the program from this repository: [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu)

I installed the program, and when trying to run I get these errors:
```
user@host:~$ miro
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 24, in <module>
    import gtcache
  File "/var/lib/python-support/python2.5/miro/gtcache.py", line 22, in <module>
    import config
  File "/var/lib/python-support/python2.5/miro/config.py", line 25, in <module>
    import eventloop
  File "/var/lib/python-support/python2.5/miro/eventloop.py", line 320, in <module>
    _eventLoop = EventLoop()
  File "/var/lib/python-support/python2.5/miro/eventloop.py", line 211, in __init__
    self.wakeSender, self.wakeReceiver = util.makeDummySocketPair()
  File "/var/lib/python-support/python2.5/miro/util.py", line 337, in makeDummySocketPair
    dummy_server.bind( ('127.0.0.1', 0) )
  File "<string>", line 1, in bind
socket.error: (99, 'Cannot assign requested address')

```

I don't really know where to go from here, I can't find any similar situations in search.

Thanks for any help.

PROBLEM SOLVED:

For future reference the problem was the loopback interface lo on my machine was down.

To fix - run "sudo ifconfig lo up"

---

### Post by shear on 2007-09-14
UPDATE:

I completely removed the version installed from the repository, and attempted to install following the instructions here: [https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs)

When running /tv/platform/gtk-x11/run.sh essentially the same error is spun out.

```
Traceback (most recent call last):
  File "dist//usr/bin/miro.real", line 24, in <module>
    import gtcache
  File "/home/contenti/tv/platform/gtk-x11/dist/usr/lib/python2.5/site-packages/miro/gtcache.py", line 22, in <module>
    import config
  File "/home/contenti/tv/platform/gtk-x11/dist/usr/lib/python2.5/site-packages/miro/config.py", line 25, in <module>
    import eventloop
  File "/home/contenti/tv/platform/gtk-x11/dist/usr/lib/python2.5/site-packages/miro/eventloop.py", line 320, in <module>
    _eventLoop = EventLoop()
  File "/home/contenti/tv/platform/gtk-x11/dist/usr/lib/python2.5/site-packages/miro/eventloop.py", line 211, in __init__
    self.wakeSender, self.wakeReceiver = util.makeDummySocketPair()
  File "/home/contenti/tv/platform/gtk-x11/dist/usr/lib/python2.5/site-packages/miro/util.py", line 337, in makeDummySocketPair
    dummy_server.bind( ('127.0.0.1', 0) )
  File "<string>", line 1, in bind
socket.error: (99, 'Cannot assign requested address')

```

I would be very grateful to anyone who could help me with this.

---

### Post by Maestro23 on 2007-09-14
Is this the same thing you are tyring to install? 

[http://www.getmiro.com/](http://www.getmiro.com/)

If so, they have a version for Ubuntu and the install looks a heck of a lot easier.

---

### Post by shear on 2007-09-14
That is the method I used the first time, for my first post. The Ubuntu version redirects to a page directing the user to add a repository and install from there. The repo on that site is the one I used.

---

### Post by Maestro23 on 2007-09-14
> **shear said:**
> That is the method I used the first time, for my first post. The Ubuntu version redirects to a page directing the user to add a repository and install from there. The repo on that site is the one I used.

Hmm... You followed the steps on this page, and it still blew up like that?

[http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)

---

### Post by shear on 2007-09-14
> **Maestro23 said:**
> Hmm... You followed the steps on this page, and it still blew up like that?

[http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)

To the letter.

---

### Post by the.ant on 2007-09-17
had the same problem as you described here: [http://www.getmiro.com/forum/comments.php?DiscussionID=243]("http://www.getmiro.com/forum/comments.php?DiscussionID=243") and the same solution solved it. thanks for the hint!

---

### Post by shear on 2007-09-17
Yeah, I suppose I should have put that info here. Well, now it is.

~shear

---

