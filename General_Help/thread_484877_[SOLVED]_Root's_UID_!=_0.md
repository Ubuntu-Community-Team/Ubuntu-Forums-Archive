---
title: "[SOLVED] Root's UID != 0"
date: 2007-06-26
forum: General Help
---

### Post by briealeida on 2007-06-26
I'm using Kubuntu 7.04, so feisty! For security purposes, I gave the user 'root' the UID 1000 and created a user account (punisher) and gave it the UID 0, effectively making it root (what we normally consider to be root, anyway). All was fine and well until I decided to update my machine. When I try to open Adept Notifier, I'm asked to authenticate with the su password. 

I've determined that 'su' without options is tied to the username root, not the UID 0 so it's asking me to enter the password of a regular user account that doesn't have the permissions to update. I would like to continue using punisher as the account with the UID 0 but want to avoid this issue. Any thoughts on this? Anyone tried this? 

Thanks a bunch.

---

### Post by kidders on 2007-06-27
Hi there,

My recommendation would be to restore the original user configuration. :-(

To be honest, I can't think of a reason to change the root account's username, especially since there may be other (perhaps more security-critical) places where the usual association between "root" and UID 0 is assumed, that you haven't discovered yet. Ideally, of course, no application should ever make that assumption, but it *does* seem to happen.

"UID 0 = root" is a long-standing convention shared by virtually all operating systems (Microsoft ones being the notable exception) ... I'd be **very** slow to deviate from it. Out of curiosity, what was your reason for making the change in the first place?

---

### Post by briealeida on 2007-06-27
I have an acquaintance whose web servers were hacked (low security) and after looking at the bash history, it was obviously a script kiddie. Most people who can get a chance to login know to try root but if root has the power of the 'nobody' account and some other name has the permissions associated with a UID of 0 I'm that much more ahead. They don't know the username they want OR the password.

I understand why you would recommend that and while it seems obvious, I'd kind of like to avoid going that route. I know that I may have to but this is a relatively expendable machine so I'm willing to test out other solutions I receive.

---

### Post by bodhi.zazen on 2007-06-27
> **briealeida said:**
> I have an acquaintance whose web servers were hacked (low security) and after looking at the bash history, it was obviously a script kiddie. Most people who can get a chance to login know to try root but if root has the power of the 'nobody' account and some other name has the permissions associated with a UID of 0 I'm that much more ahead. They don't know the username they want OR the password.

I understand why you would recommend that and while it seems obvious, I'd kind of like to avoid going that route. I know that I may have to but this is a relatively expendable machine so I'm willing to test out other solutions I receive.

This is why Ubuntu uses sudo and inactivates (locks) root.

You do not need to go through all this effort, it is all taken care of already.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **By default, the root account is locked in Ubuntu.** This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

---

### Post by kidders on 2007-06-27
Hey again,

The usual approach is not to set a root password at all and/or to explicitly disallow the use of the root account with remotely accessible apps. Taking SSH as a specific example, just for the sake of it, disabling authentication by password, explicitly disabling the use of the root account, and removing root's password gives you three layers of protection against brute force hacks. The only way to perform any action as root then becomes hacking an account with access to sudo, which puts malicious users in exactly the same position you're looking for (ie needing to guess both a username *and* a password to get anywhere). I don't want to seem cruel, but frankly, anyone who makes it possible to log in normally to a machine as root at all deserves what they get!

> **briealeida said:**
> this is a relatively expendable machine so I'm willing to test out other solutions I receive.By all means, go for it! :-) To be honest, I can't help feeling as though the username of the "root" account _should_ be irrelevant. I'd like to think that the maintainers of any apps that fail your test would appreciate a bug report on the issue.

[SIZE=1]As an aside, regarding your friend who got hacked, it's often helpful to watch for brute force attacks & have your system act pre-emptively to head them off. Even a basic script that keeps an eye on authentication logs, and blocks sources of repeated failures with iptables can be quite effective. I often get very obviously scripted attempts to log into common accounts over various protocols ... some of them last for hours! ... but my box blocks them automatically after three failures, in addition to more normal security precautions.[/SIZE]

This post is full of mixed messages (sorry about that), so just to restate, the problems you've run into feel wrong to me, but even if you *could* change root's username without adverse effects, I'd still prefer to stick to standard solutions when it comes to security. Hopefully some other posters' points of view will appear here before long though. :-)

**Edit:** Oops... bodhi.zazen beat me to a response! I know neither of our posts is really what you want to hear (ie they avoid the issue rather than solving it, in a way), but standard solutions really are best.

---

### Post by briealeida on 2007-07-02
> **kidders said:**
> 
By all means, go for it! :-) To be honest, I can't help feeling as though the username of the "root" account _should_ be irrelevant. I'd like to think that the maintainers of any apps that fail your test would appreciate a bug report on the issue.


I've found a few more instances on non-Ubuntu machines where this tactic is failing me. Suppose this is something best left unchanged until I have the 48 hours in a day to get some serious work done on it.

Thanks everyone.

---

