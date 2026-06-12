---
title: "ejabberd server"
date: 2007-07-14
forum: General Help
---

### Post by Cable on 2007-07-14
I'm trying to set up an ejabberd server on my computer for LAN use.  I'm experiencing a lot of confusion with trying to set it up, so I'm creating this thread to hold my questions about my set up saga.

_**Problem 1**_

When I try to do
```

sudo /etc/init.d/ejabberd start

```it says "Starting jabber server: ejabberd."  When I do
```

sudo /etc/init.d/ejabberd restart

```it says "Restarting jabber server: ejabberd is not running. Starting ejabberd."  And when I do
```

sudo /etc/init.d/ejabberd stop

```it says "Stopping jabber server: ejabberd already stopped."

It seems to me that the server is never even running.  What confuses me is that when I run top and show only the "ejabberd" user, I see what is shown in the attached screenshot.  What's going on?  Don't those processes show that the ejabberd server is running?

[U][B]Problem 2

[/B][/U]I'm guessing this might have something to do with problem 1, but when I try to make use of the "ejabberdctl" command, for example
```

ejabberdctl status

```it outputs "RPC failed on the node 'ejabberd@caleb-desktop': nodedown."  I have no idea what this means, but I'm assuming it means that the server is not running.  However, as seen above, I cannot start the server.  How can I fix these problems?

Any help is MUCH appreciated!

---

### Post by Cable on 2007-07-15
*bump*

---

### Post by Cable on 2007-07-17
So nobody can help me with this problem?

---

