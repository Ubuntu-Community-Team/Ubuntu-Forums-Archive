---
title: "sudo timeout"
date: 2008-02-02
forum: General Help
---

### Post by SpiderGorilla on 2008-02-02
There are several older posts about extending the time-out of sudo (and I would think any time you have to put in the password via the GUI) that involve gediting or using visudo.  I was hoping there was a new way to do this by now that didn't require editing a rather tetchy file. The five or so minutes between things gets annoying, although I can now type my rather convoluted password pretty quickly.

So is there a gui-based way or at least a less-meddlesome way to change this, or should I just go ahead and dig in for the duration?

And if I *DO* edit this file, which is proper:
[Method #1](http://ubuntuforums.org/showpost.php?p=1031679&postcount=3) or
[Method #2](http://ubuntuforums.org/showpost.php?p=1337839&postcount=2) or
[Method #3](http://ubuntuforums.org/showpost.php?p=1198301&postcount=6) (which is Method #1 without defining the username) or
[Method #4](http://ubuntuforums.org/showpost.php?p=113137&postcount=6)

I mean, I'll do it. I really will. But I don't really feel like trying to rescue my system if I bork this. Any help is greatly appreciated.

---

### Post by kidders on 2008-02-03
Hi there,

It's worth bearing in mind that sudo's timeout exists to avoid forcing users to type their passwords more than once in the same 10 seconds (ie for sequential commands, all of which start with "sudo..."), because in principle, asking for passwords *too* often is insecure. Its purpose is _not_ one of convenience.

If you really want to extend the grace period, I suggest...
[LIST]
[*]Only using methods that involve visudo.
[*]Not setting the timeout to -1.[/LIST]The reason for peoples' warnings & cautions when they talk about editing /etc/sudoers is that ill-advised changes have the potential to allow malicious scripts/users unrestricted access to your box, and mistakes can mess sudo up completely. If you are confident about a change you want to make, there is no reason not to modify the file. :-)

If you get bored typing & re-typing your password, there are other ways of avoiding having to do so, that you may not be aware of...

**- I -**
You can run **sudo su** in a shell, to become root & stay root, until you hit CTRL+D. The last character in the prompt should change from '$' to '#' to remind you anything you execute will run with root privileges.

**- II -**
If you find yourself constantly using sudo to run something reasonably harmless that just happens to require root privileges, you could permit less restrictive use of sudo on a "per-user-per-command" basis.

Anyhow, if you find yourself wanting to make your sudo grace period very long, one of these might be worth a look.

---

### Post by SpiderGorilla on 2008-02-04
Thanks for that info. I'll bear that in mind. Mostly I don't find myself doing sudo unless I'm adding or removing programs a lot, which tends to happen as I'm testing out new things.

---

