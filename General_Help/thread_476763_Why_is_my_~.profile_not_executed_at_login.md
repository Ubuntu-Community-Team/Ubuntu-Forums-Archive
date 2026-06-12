---
title: "Why is my ~/.profile not executed at login?"
date: 2007-06-17
forum: General Help
---

### Post by therealbrewer on 2007-06-17
Sorry for the repost, but I think my old title didn't attract enough attention...

Please help me figure out why this is happening.

I have two machines. One had Dapper upgraded to Edgy upgraded to Feisty, the other has fresh install of Feisty.

My understanding of login initialization is:

1) /etc/profile  is for system-wide environment variables -> thus available to all users
2) ~/.profile is for user environment variables -> for current user only, but available to all processes whether launched from x-term, menu, whatever.
3) ~/.bashrc is for (bash) terminal environment variables -> current user, applies only to processes launched from terminal

So, I wanted to set my $PATH for all processes, thus I added the following to ~/.profile:

```
source /opt/intel/fc/10.0.023/bin/ifortvars.sh
source /opt/intel/idb/10.0.023/bin/idbvars.sh
```

These are just scripts that set various environment variables for the Intel Fortran compiler.

Now, on the fresh install machine, this works fine. I can launch a program from the menu in Gnome and that program will see the path set by ~/.profile. Also, I can launch an x-term, and get 

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/intel/fc/10.0.023/bin:/opt/intel/idb/10.0.023/bin
```

so the PATH is as it should be.

On the other machine, it doesn't work!! Programs launched from the menu can't see the modified path, nor can x-terms see it. (They can only see the PATH as found in /etc/environment.) Interestingly, if I then do this

```
. .profile
```

from an x-term, the PATH is OK. So since I can execute the file manually and get the needed results, it is clear that there is nothing wrong with the syntax, etc. Therefore I believe that ~/.profile is never being executed on that machine at login.

So, I have many questions:

What could cause ~/.profile to not be executed or to not be called?
Is there any way to trace the login sequence and see if ~/.profile is or is not called?
Would there be an error log somewhere?
How else can I figure out what is going on?
Suggestions?

I know that ~/.profile is not executed if ~/.bash_profile or ~/.bash_login exist, but neither of these files exist. Also, on the machine where this does not work, when I went to add the two lines above, I discovered that ~/.profile did not already exist. Thus I copied it from /etc/skel/ and then added the two lines. I don't really understand why that file would exist on one machine but not on the other, but nevertheless I can't see why ~/.profile shouldn't be executed just because I created it (permissions seem to be OK as far as I can tell).

Anyway I'm really stumped on this, and I suppose there are other ways of achieving the end result, but I would like to get to the root cause if possible.

Finally, if I add the two lines to /etc/profile, it still doesn't work! What is going on????

Thanks!

---

### Post by s.deleeuw on 2007-06-17
> **therealbrewer said:**
> 
What could cause ~/.profile to not be executed or to not be called?


$HOME/.profile is read only when a login-shell is started.
Are you using gnome-terminal? Gnome-terminal doesn't start BASH as login-shell by default. You may want to change this under Edit > Current Profile > Title and Command.
I am using $HOME/.bashrc to customize my PATH. This file is read anytime.

---

### Post by therealbrewer on 2007-06-17
> **s.deleeuw said:**
> $HOME/.profile is read only when a login-shell is started.
Are you using gnome-terminal? Gnome-terminal doesn't start BASH as login-shell by default. You may want to change this under Edit > Current Profile > Title and Command.
I am using $HOME/.bashrc to customize my PATH. This file is read anytime.

Well, I don't know how to be more clear about what I am doing. I modified $HOME/.profile on two machines. On one machine, a program launched from Gnome's top menu bar (Applications) can see the modified $PATH. The same program on the other machine cannot. Note these are not launched from Gnome-terminal. Nevertheless, if I open a Gnome-terminal, and echo the $PATH, I can see that the PATH is not the same on the two machines. But I want to emphasize that I am not talking about Gnome-terminal. I am talking about the system-wide path for one user.

According to this

[http://www.phptr.com/articles/article.asp?p=441605&seqNum=2&rl=1](http://www.phptr.com/articles/article.asp?p=441605&seqNum=2&rl=1)

and countless other sources, $HOME/.profile should be read only by login shells just as you stated. I'm not an expert, but I have read in several places that when Gnome (the window manager, not Gnome-terminal) starts up, it is not run as a login shell. I don't know if that is true or even if it makes sense, BUT even if it is, why would my approach work on one machine and not the other? I know that for one machine $HOME/.profile IS called. That is what I don't understand. Is there any way to trace exactly the sequence of events that occur at startup? Is there any way to echo all the startup commands/scripts/etc to a file so I can check to see if $HOME/.profile is ever called?

Anybody?

---

### Post by therealbrewer on 2007-06-18
OK, don't ask me why this worked, but I fixed it.

I did this

```
sudo cat /etc/passwd | grep ^myusername
myusername:x:1000:1000:myactualname,,,:/home/myusername:/bin/bash
```

which showed that my default shell was /bin/bash. Just for the heck of it I edited /etc/passwd so that my shell would be /bin/sh. Restart Gnome with ctrl-alt-backspace. Path is fixed but gnome-terminal is now crappy. Re-edit /etc/passwd back to /bin/bash, restart Gnome, and voila! PATH is fixed!!! just to be sure though I rebooted and it is indeed fixed.

Don't know why, can't explain it, but it works!!!

---

