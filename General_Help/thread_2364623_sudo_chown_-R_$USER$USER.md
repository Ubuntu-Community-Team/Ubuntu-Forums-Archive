---
title: "sudo chown -R $USER:$USER /"
date: 2017-06-25
forum: General Help
---

### Post by rudger2 on 2017-06-25
Accidently I used the command: sudo chown -R $USER:$USER /, now I dont have any permissions anymore and when trying to run the sudo command I get: sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set.
Anything I can do?

---

### Post by CatKiller on 2017-06-25
You could probably boot from a live cd and restore the ownership by hand. Everything that's not in /home should probably be owned by root. At least it was ownership that you did, rather than permissions.

You might even be able to get away with doing it from single-user mode.

---

### Post by SeijiSensei on 2017-06-25
This is the kind of damage that is very difficult, indeed nearly impossible, to fix.  You would have to correct the permissions on thousands of files making sure, for instance, that /var/lib/mysql is owned by the mysql user, /var/www/html is owned by the www-data user, etc.  So really the only safe solution is to backup any files you want to save and reinstall Ubuntu.  

And be careful about using sudo.

> **CatKiller said:**
> You could probably boot from a live cd and restore the ownership by hand. Everything that's not in /home should probably be owned by root.
Sadly, no.  As I said above, some files are owned by specific users like mysql or www-data, not by root.  Changing everything to root ownership would break these applications.

---

### Post by CatKiller on 2017-06-25
Getting everything owned by root will mean that the system works, at least. Some tweaking may be necessary later for specific applications, for sure, but at least the whole thing will actually be working.

If he's running a webserver on there then he'll already know which permissions he needs for that.

---

### Post by rudger2 on 2017-06-25
How can I get access via live cd? Right now I also get kicked from my login screen, if i type my password right.

---

### Post by QIII on 2017-06-25
Having everything owned by root is not such a swell idea, either.  Especially on a web server where certain owners/permissions are required for proper functioning.

It is well nigh impossible to fix this without a week or two of concerted effort and detailed knowledge of which ownership/permissions belong where.  Even then, there would be no guarantee of success.

There are only about three circumstances where I will say this:  Attempt to save what important files can be saved and then blast to nuke they system from orbit.  That is the most efficient course of action.

---

### Post by CatKiller on 2017-06-25
@QIII There's been no indication that it is a webserver; that was just an assumption that Seiji made. AFAIK, on a standard Desktop install, everything that isn't in /home is owned by root. As I said. There may be one or two applications whose files need different ownership. As I said.

@rudger2: you need to boot from the live cd and then mount your hard drive from there to change the ownership back since, as you've found, using the installed programs has become problematic. A search for something like "mount files from live cd" should give you all the information you need. I'd find a guide for you, but I'm typing on my phone.

---

### Post by QIII on 2017-06-25
While it is true that *most* files outside of /home are owned by root, it is not true that *all* files outside of /home are owned by root.

---

### Post by CatKiller on 2017-06-25
If you know which files should be owned by a user other than root in a standard Desktop install, I'm sure that would be very useful information for the OP.

---

### Post by Habitual on 2017-06-26
Sorry about your luck. Easiest to re-install. As hard as that is, it is the best way.

---

### Post by SeijiSensei on 2017-06-26
Just looking in /var/lib/ alone, I see directories owned by same-name "users" including libuuid, avahi-autoipd, lightdm and colord.  I have other such directories there as well, but these are from packages not commonly installed on desktops like postgresql.

Some files and directories have root ownership but belong to other groups like /var/metrics and /var/cache which belong to the whoopsie group.

---

### Post by sisco311 on 2017-06-26
> **CatKiller said:**
> If you know which files should be owned by a user other than root in a standard Desktop install, I'm sure that would be very useful information for the OP.

Unfortunately on a debian based system there is no easy (automated) way to restore the proper file ownership and permissions.   

For security and usability reasons cache files, log files and some config files like shadow and gshadow, the mail directory and so on... are owned by a non-root user or group. And don't forget that the chown command wipes out the setuid and setgid bits. So you will have to restore the permissions of the setuid and setgid commands like su, sudo, ping, pkexec, chsh, passwd, chage and a dozen more. Setting the wrong owner/group on a setuid/setgid application is a huge security risk. 

Tracking down the files owned by a non-root user or group will take more time than a reinstall even for an experienced user. 

As QIII said there are very few cases when a reinstall is needed. This is one of them.

---

### Post by CatKiller on 2017-06-26
> **sisco311 said:**
> And don't forget that the chown command wipes out the setuid and setgid bits. So you will have to restore the permissions of the setuid and setgid commands like su, sudo, ping, pkexec, chsh, passwd, chage and a dozen more.

I had forgotten that. I had thought, as you can see from my first post, that it would only be ownership & not permissions; a major pain, but still doable.

I also concede that rescue is a lost cause, then.

---

### Post by rudger2 on 2017-06-26
Is there a possibility for me to recover some files on my desktop? I also get kicked back to login screen when trying to login.

---

### Post by CatKiller on 2017-06-26
> **rudger2 said:**
> Is there a possibility for me to recover some files on my desktop? I also get kicked back to login screen when trying to login.

Yes, booting from a live cd or live USB will let you copy files elsewhere. The only problem with your existing install is that the programs no longer work. The data is essentially intact.

If you have your /home on a separate partition (which is generally useful) you could simply reinstall over your /, create the same users, and all your settings and data will magically be the same. Backing up would still be advisable, even in that happy state.

---

### Post by deadflowr on 2017-06-26
^That
[s]As well as you will need to reset your permissions settings (owner/group).
As those would have also been changed to root.
But that's easier than doing so to the whole system, since most everything in home should be owned by you.[/s]

Edit: Nevermind.
I now see you would have already have the permissions set correctly for your own files.
Based on the original actions done (better known as the reason for this thread).
I was thinking you already changed the rights to root for all.

---

### Post by rudger2 on 2017-06-26
Do I have to select try ubuntu?

Like this: https://m.youtube.com/watch?v=y9GU5TUz_f0  ?

---

### Post by CatKiller on 2017-06-26
You'll want to do all your backing up from a live environment. It will be called something like "try Ubuntu without installing" when you've booted from a live cd or live USB.

---

### Post by rudger2 on 2017-06-27
Thanks a lot guys, without you I may not have succeeded.

I selected try ubuntu on startup and managed to save my files from my "corrupted" server.

---

### Post by Habitual on 2017-06-28
Nicely done. Good job.

---

