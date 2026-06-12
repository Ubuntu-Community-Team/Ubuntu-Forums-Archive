---
title: "What is &quot;Set-Root-UID&quot;?"
date: 2007-01-09
forum: General Help
---

### Post by mistypotato on 2007-01-09
What is the purpose of set-root-UID and how is it used?

I can't get mondoarchive to burn DVD's because it says growisofs will not run under root yet MondoArchve won't run unless I run it under root (Sudo).
A real Catch-22 situation.

This is bizarre and confusing.

The Growisofs Man Pages says to Install GrowIsOfs "set-root-UID" but as a newbie, I don't know how to do that or what it means.

Thanks for your help.

---

### Post by mistypotato on 2007-01-09
Anyone know what this is and how to use it?

---

### Post by simonn on 2007-01-09
> **mistypotato said:**
> Anyone know what this is and how to use it?

See [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid).

Use:

```

$ sudo chmod ug+s [path to]/growisofs

```

---

### Post by mistypotato on 2007-01-20
MondoArchive Problem with DVD (CD backup works fine)

Still can't get her done :confused: 
 
[SIZE="3"]Fatal error... Can't write DVDs as sudo because growisofs doesn't support this - see the growisofs manpage for details.[/SIZE]

Even after setting growisofs Set-Root-UID
[SIZE="3"]
**[COLOR="Navy"]-rwsr-sr-x 1 root root 71740 2005-11-11 10:14 growisofs[/COLOR]**
[/SIZE]

Still getting the same error!


[COLOR="Sienna"]Taken Directly From Growisofs Manpage.....
[http://www.linuxcommand.org/man_pages/growisofs1.html]("http://www.linuxcommand.org/man_pages/growisofs1.html")

       If executed under sudo growisofs refuses to start. This is done  for
       the following reason. Naturally growisofs has to access the data set to
       be recorded to DVD media, either indirectly by letting mkisofs generate
       ISO9660  layout on-the-fly or directly if a pre-mastered image is to be
       recorded. Being executed under sudo,  growisofs  effectively  grants
       sudoers  read  access  to any file in the file system. The situation is
       intensified by the fact that growisofs parses MKISOFS environment vari-
       able  in  order  to  determine  alternative  path to mkisofs executable
       image. This means that being executed under sudo,  growisofs  effec-
       tively  grants  sudoers  right  to execute program of their choice with
       elevated privileges. If you for any reason still find the above accept-
       able  and  are  willing to take the consequences, then consider running
       following wrapper script under sudo  in  place  for  real  growisofs
       binary.

       But  note that the recommended alternative to the above "workaround" is
       actually to install growisofs set-root-uid, in which case it will  drop
       privileges  prior  accessing data or executing mkisofs in order to pre-
       clude unauthorized access to the data.


[/COLOR]


The Mondo Log offers help inthe way of sending the logs to a "Mail List"...
but when I tried I got this....

[COLOR="Red"]Error while performing operation.

RCPT TO <mondo-devel_at_lists.sourceforge.net> failed: Requested action not taken: mailbox unavailable[/COLOR]

At a dead end here

---

### Post by iceman504 on 2007-02-11
Im having the same problem with mondoarchive also and i did what simonn said but im still getting the same error....anybody figured this out yet or have any other alternatives?

---

### Post by 3rdalbum on 2007-02-11
What about if you do:

```
gksudo nautilus
```

Find the growisofs binary (it's in /usr/bin), right-click on it and go "Properties". In the Permissions tab, change the file owner to your *own user account*, and change the group owner to something applicable (the group with the same name as your username) and click the "SetUID" checkbutton.

Now run the mondoarchive program with sudo. I'm guessing it should work now.

---

