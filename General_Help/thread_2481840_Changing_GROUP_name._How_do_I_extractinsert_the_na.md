---
title: "Changing GROUP name. How do I extract/insert the name?"
date: 2022-12-10
forum: General Help
---

### Post by ne29914 on 2022-12-10
I'm trying to correct a UID:GID problem by writng a small script (more like a batch file, really).
The username and groupname should be the same in the end.

I can extract the username from the systam by running "users", but how do I get the output into the two following commands?
I've searched high and low on the web, but all I get is paraphrases of the "man" pages:

sudo groupmod -g 1000 **output from "users" command**
sudo chgrp -R **output from "users" command** $HOME/*

TIA.

---

### Post by TheFu on 2022-12-10
For getting uid and gid information, I always use the
```
 $ getent group
```
and
```
 $ getent passwd
```
commands.  These will hit LDAP if it is configured or just read the text files in /etc/ otherwise.

the getent will filter on a single "name", if provided as the 3rd parameter on the line.
```
$ getent group adm
adm:x:4:syslog,thefu
```

For just a few users or groups, it is much easier to just directly edit the passwd and group files directly and make them consistent with whatever you desire.  The "names" aren't really important. It is the uid/gid that matter, so just be consistent. It ain't hard and this is how admins in small situations handle local accounts.  If it takes over 60 seconds, I'd be surprised.  Don't forget to check the shadow and gshadow files too.  I remember that one of those also needs changing sometimes.
Also, if you are messing with any sudo users, don't dally.  Git-er-done in a few seconds before the elevated privileges expire and you have to boot from a "Try Ubuntu" setup to put things back.

If the uid/gid don't change, then there's no need to chown anything.

If the uid/gid (the numbers) are changing, then you'll need to use chown and tell the users impacted to check the group settings on their files, if you don't feel like fixing those too.  I never do.  Makes users think you're too busy and gives them something to do.

BTW, you might want to use the 'id' command. Be certain to check the options to get exactly what you want, when you want it.
And I'd only look at users with a uid GT 999 and LT 9999. Some containers, daemons and snaps like to use 10,000+ for their non-root mappings from the host system.

If this is for fewer than 5 users, I'd manually do it.  For more, I'd look for an existing script.  A tiny mistake could easily lead to a system that won't run.

---

### Post by Impavidus on 2022-12-11
TheFu gave you an explanation for your current problem. Read it.

Putting the output of one command on the command line of another is common in shell scripting. It's known as command substitution. Every bash scripting guide should have a chapter on that. Basically,```
command1 $(command2)
```Alternatively (but a bit old-style):```
command1 `command2`
```If you wish, you could use the xargs tool instead:```
command2 | xargs command1
```There are some differences in how these methods handle things like whitespace, linebreaks or escape characters.

---

### Post by TheFu on 2022-12-11
> **ne29914 said:**
> 
sudo groupmod -g 1000 **output from "users" command**
sudo chgrp -R **output from "users" command** $HOME/*


```
$ sudo groupmod -g 1000 $(users)
$ sudo chgrp -R $USER  $HOME 
```
I didn't check that the 'groupmod' command is correct.  I've never used it.

But there is very likely an existing environment variable $USER with the current username, so no need to run any command, just use the existing environment.  

I cleaned up the chgrp a bit. Using pattern matching will miss .dot files.  BTW, you can force the group using the name or the gid (number) can also be used, if that is easier.

---

### Post by ne29914 on 2022-12-11
Thank You All for your help.
The trick with $(users) was extremely helpful!
I managed to cobble this together, and it works :)
```
sudo groupmod -g 990 sambashare
sudo groupmod -g 1000 $(users)
sudo chgrp -R $(users) $HOME/* $HOME/.[!.]* /home/$(users)
```

This fixes the Calamares bug setting Sambashare GID to 1000; but only if executed directly after a clean install. Another annoyance dealt with.

---

### Post by TheFu on 2022-12-11
```
chgrp -R $USER $HOME 
```
should be all you need.  We post that as a fix here lots. 

Also
```
sudo chown -R  $USER:$USER $HOME
```
for when people abuse sudo and end up with the wrong owners.

---

### Post by ne29914 on 2022-12-11
@TheFu:
Yes, it should be enough, but isn't. The problem is, that a default Lubuntu install (using Calamares) assigns GID 1000 to sambashare, so that has to be taken care of first.
That still leaves the main user with UID:GID as 1000:1001 which I found out is at total pain when exchanging files between computers. Originally I'd decided to ignore the issue, but the side-effects were too annoying.
My problem is not the user:group names, but the wrong GID. Thus the somewhat more involved commands I constructed.
I'm not sure if your commands solve the basic problem of the GID.

I apologise that I didn't state the issue precisely in my OP.

---

### Post by TheFu on 2022-12-11
The changing of the gid is a completely separate thing and I'd assumed that would be handled before the last command I posted here. I was ignoring the groupmod completely.  Re-reading my last post, I can see that I was unclear and chose poor words "should be all you need", which is incorrect for the total needs, but definitely covers the chmod stuff completely for all files inside the user's HOME.

---

### Post by ne29914 on 2022-12-12
Yes, "inside the user's $HOME. Unfortunately it doesn't cover changing the /home/username directory, which explains that addition to my command.
But I'm very satisfier with my result, also because when I look at it a year from now I'll understand what it's doing.
 
Thanks

---

