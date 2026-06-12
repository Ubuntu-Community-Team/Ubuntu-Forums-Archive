---
title: "ssh stealing password?"
date: 2007-02-09
forum: General Help
---

### Post by jscottm on 2007-02-09
When I try to ssh I get

ubuntu > ssh -l user domain.com
Password:
Password:
Password:
[email]user@domain.com[/email]'s password:

On the first three requests for the password, it does not matter what I put in. When I finally get the [email]user@domain.com[/email] prompt, then I'll get in if I use the valid password. Did one of the packages I installed put in a password-stealing version of ssh?

Any help would be appreciated, Some details are below.
- John :)

ubuntu > uname -a
Linux ubuntu1 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux
ubuntu > which ssh
/usr/bin/ssh
ubuntu > ls -l /usr/bin/ssh
-rwxr-xr-x 1 root root 238028 2006-10-02 07:26 /usr/bin/ssh

---

### Post by rich.bradshaw on 2007-02-09
You realise that when you type the password won't show on the screen don't you? Not sure if that is what is the problem, but it confused me at first...

---

### Post by jscottm on 2007-02-09
I'm only  showing what is shown on my screen (not what I type in, which is not shown). When I get prompted for the first three password attempts (prompt is "Password:") then no matter what password I put in, it does not log me in, it just prompts me again. Only when I get the "user@domain.com's password:" prompt, do I get logged into the system with the valid password.

Hope this clears up my situation.

John :)

---

### Post by taurus on 2007-02-09
What if you just do 

```
ssh domain.com
```
It will then prompt you for your username and your password.

---

### Post by christhemonkey on 2007-02-09
That is wierd!
Are you running breezy? (cos that kernel is getting on a little bit now)

Maybe you should file a bug?

Are you running ssh as your default user?

The only thing that seems vaguely relevant is this but then again it was asking for the ssh pass not your pass....
> I get a dialog box titled 'OpenSSH', text 'Enter passphrase for key [...]'
I hit cancel.

Instead of cancelling, I get a second dialog: title 'OpenSSH', text '[me@gnome]'s password'.
I hit cancel again.
I get the second dialog two more times before I can get back to what I was doing.

My guess is that you are asked once for every auth mechanism the host supports, and when hitting cancel it tries the next auth mechanism. I.e hitting cancel is not canceling the whole operation but canceling authentication with the current mechanism.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/34283](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/34283)

---

### Post by wiremoons on 2007-02-09
You could also try the following:

```
ssh user@domain.com
```

---

### Post by jscottm on 2007-02-09
ubuntu > ssh domain.com
Password:
Password:
Password:
[email]my_ubuntu_user_id@domain.com[/email]'s password:

Since my_ubuntu_use_id is not the same as the login I need to use for the ssh, this doesn't work. Should it be prompting me for a user id if I leave it off?

John :)

---

