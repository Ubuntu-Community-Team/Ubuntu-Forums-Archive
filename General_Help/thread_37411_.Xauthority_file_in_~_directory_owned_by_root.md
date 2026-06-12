---
title: ".Xauthority file in ~/ directory owned by root?"
date: 2005-05-27
forum: General Help
---

### Post by emmet on 2005-05-27
Hi All,

I'm having a little problem with the vncserver application under Hoary, and I'm not sure what's incorrect here.

When I start up the vncserver by typing

```
vncserver :1
```

I get the error:

```
xauth: /home/user/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/user/.Xauthority
```

The rest of the application works, and I can access an Ubuntu desktop from my vncviewer (on an XP machine).

While I was trying to debug the problem, I saw that the .Xauthority file in my home directory belongs to root. 

So, my question is: is this normal in Ubuntu? Should I change the ownership to the user?

Thanks in advance,

Emmet

---

### Post by Takis on 2005-05-27
```
~$ ls -l .Xauthority
-rw-r-----  1 taki taki 152 2005-05-22 18:07 .Xauthority
~$ 
```
Looks like you're supposed to be the owner. I guess a chown is in order.

---

### Post by emmet on 2005-05-27
Ah, the Red Dwarf crew swing into action.  \\:D/ 

Many thanks Takis. I've made the change. 

Just wanted to make sure that I was the only one with a 'rooted' .Xauthority file...

Thanks again,

Emmet

---

### Post by jonrkc on 2005-05-29
The same thing happened to me, and in fact a whole bunch of permissions got messed up when I transferred my Ubuntu system to a larger hard drive.  I just take them one by one and make myself the owner.  This has been such a frequent problem that when something fails to work the first thing I check now is the file ownership and permissions.  Sometimes they seem to get mysteriously set wrong again, and I just change them back again...

---

### Post by word_virus on 2005-05-29
[QUOTE=emmet]

Just wanted to make sure that I was the only one with a 'rooted' .Xauthority file...

Thanks again,

Emmet[/QUOTE]

I had the same permission change after installing Ruby on Rails on hoary.  A quick 'sudo chown' fixed it so no big deal, but the only reason I even noticed it was because the first time I rebooted I was locked out of Gnome :) Makes me worry there are other permission 'suprises' that may have escaped my attention :)

---

### Post by Takis on 2005-05-29
I guess the problem on Linux boxes isn't so much from spy/malware maliciously attacking machines, but from programs that accidentally do something that isn't too good (e.g. include an 'rm -fr *' at the root level  :) ).
Looks like the lesson here is to look at a program's feedback before installing it.

---

### Post by jonrkc on 2005-05-29
[QUOTE=Takis]I guess the problem on Linux boxes isn't so much from spy/malware maliciously attacking machines, but from programs that accidentally do something that isn't too good (e.g. include an 'rm -fr *' at the root level  :) ).
Looks like the lesson here is to look at a program's feedback before installing it.[/QUOTE]
 My impression after 2 1/2 years of exclusive Linux usage is that you're absolutely right!  I have found program after program that has not been tested enough before making it available.  The same thing was true under Windows, of course, but I ran into fewer such there.

By the way, I hope nobody TRIES out the command you quoted in your post unless they want to lose possibly a whole lot of their files--or even the entire system.  It might be just as well to warn: If you don't know what that does, don't try it.

---

### Post by Takis on 2005-05-29
[QUOTE=jonrkc]By the way, I hope nobody TRIES out the command you quoted in your post unless they want to lose possibly a whole lot of their files--or even the entire system.  It might be just as well to warn: If you don't know what that does, don't try it.[/QUOTE]
It's alright. You can always try to recover your harddrive by [PROGRAMMING IN HEX](http://www.ee.ryerson.ca:8080/~elf/hack/recovery.html)!  ](*,)

---

