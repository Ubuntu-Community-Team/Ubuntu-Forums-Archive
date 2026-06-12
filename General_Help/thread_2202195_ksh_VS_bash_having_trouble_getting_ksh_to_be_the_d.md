---
title: "ksh VS bash having trouble getting ksh to be the default shell"
date: 2014-01-27
forum: General Help
---

### Post by keith14 on 2014-01-27
Hi,
 I tried to get ksh be the default shell but failed so far. last attempt tried something I found on line:

entered                     --> responce

$ pwd                       --> /home/keith
$ sudo apt-get install ksh  --> got several lines of responce w/o error but lost
                                            them in the buffer. can not paste them.
$ which ksh                 --> /usr/bin/ksh
$ sudo chsh -s /usr/bin/ksh --> chsh: PAM Authentication failure

I then tried to reload ksh but was informed the the lag version of ksh is in stalled. I was not able to locate this (ksh) as an extension or an installed program in the software center.

So I got 2 questions I quess where did ksh get installed and how do I get it to work?
Thanks,
Keith

---

### Post by steeldriver on 2014-01-27
It appears that ksh installs as both /usr/bin/ksh and /bin/ksh - both  are ultimately symlinks to /bin/ksh93 which you can confirm using  readlink

```

$ readlink -f /usr/bin/ksh
/bin/ksh93
$ 
$ readlink -f /bin/ksh
/bin/ksh93

```

The 'which' command is finding /usr/bin/ksh simply because /usr/bin is ahead of /bin in your PATH, however you should probably use /bin/ksh for the chsh command - I have a feeling that 'relative' symlinks (i.e. within the same parent directory - in this case /bin) are treated slightly differently.
 
Having said that,  **to change your own default (login) shell you shouldn't use sudo** - just

```
chsh -s /bin/ksh
```

Unfortunately by using *sudo chsh* without specifying a user, you have likely set *root's* login shell to /usr/bin/ksh instead of your own - the PAM error may be because /usr/bin/ksh isn't in /etc/shells, which may make it hard to revert root's login shell to /bin/bash via sudo - I suggest you check with

```
getent passwd root
```

If that's the case, post back - I *think* I know a workaround

---

### Post by keith14 on 2014-01-27
Hi, thanks fot answering. below I just repeated what you sent me (mostly). Most makes sense except last entry. I don't know what it should look like. Thanks ahead of time. Keith         Y was I not able to change shell for self?

ok> pwd
/home/keith
ok> readlink -f /usr/bin/ksh
/bin/ksh93
ok> readlink -f /bin/ksh
/bin/ksh93
ok> pwd
/home/keith
ok> chsh -s /bin/ksh
You may not change the shell for 'keith'.
ok> pwd
/home/keith
ok> getent passwd root
root:x:0:0:root:/root:/bin/ksh

---

### Post by keith14 on 2014-01-27
the face on last line was not intentional

---

### Post by keith14 on 2014-01-28
last line should read:
ok> getent passwd root
root:x:0:0:root:/root:/bin/ksh

---

### Post by steeldriver on 2014-01-28
Use ```
 tags and/or check the 'Disable smilies in text' box to prevent :x etc. getting turned into smilies

Hmm well maybe there are some polkit settings I don't know about making sudo a requirement for your users to change their own shells? if you *must* use sudo, then make sure you specify the target user i.e.

[CODE]sudo chsh -s /bin/ksh **keith**
```

else you will be changing root's shell again. BTW I think it's 'whoami' that matters - not 'pwd'

I suggest changing root's shell back to /bin/bash as well

---

### Post by keith14 on 2014-01-28
I think there must have been upc before. Typing--                root:x:0:0:root:/root:/bin/ksh

I think I may have messed-up settings.

 $ sudo chsh -s /bin/ksh keith
Password: 
chsh: PAM: Authentication failure
$ 
I lost my prompt that I set yesterday also. pwd is print_working_dir I was trying to show where I was typing commands. If I ever get things worked out (as once with MKS) ksh will look in current dir first then /bin and any where else. There are many simularities B/W ubuntu and MKS, I quess it's the sudo thing I need to ketch-up on, was always admin using MKS (or owner). Thanks for taking time. Keith

---

### Post by steeldriver on 2014-01-28
... sorry I have no idea what that means or whether you solved the issue

---

### Post by keith14 on 2014-01-28
I merely meant thanks for taking time to look at problem.

Well this is a re-start.
>edited /etc/shells to add ksh as an entry
 this removed the aplication athentification error above when using chsh
>re-edited /etc/shells to remove ksh that was added above
>removed ksh install: sudo apt-get remove ksh
<[sudo] password for keith:
<Reading package lists... Done
<Building dependency tree
<Reading state information... Done
<The following packages will be REMOVED:
<  ksh
<0 upgraded, 0 newly installed, 1 to remove and 260 not upgraded.
<After this operation, 3,229 kB disk space will be freed.
<Do you want to continue [Y/n]? y
<(Reading database ... 162645 files and directories currently installed.)
<Removing ksh ...
<Processing triggers for man-db ...
<re-booted>
>re-added ksh:
>ok> sudo apt-get install ksh
<[sudo] password for keith:
<Reading package lists... Done
<Building dependency tree
<Reading state information... Done
<The following NEW packages will be installed:
<  ksh
<0 upgraded, 1 newly installed, 0 to remove and 260 not upgraded.
<Need to get 0 B/1,583 kB of archives.
<After this operation, 3,229 kB of additional disk space will be used.
<Selecting previously unselected package ksh.
<(Reading database ... 162625 files and directories currently installed.)
<Unpacking ksh (from .../ksh_93u+20120801-1_amd64.deb) ...
<Processing triggers for man-db ...
<Setting up ksh (93u+20120801-1) ...
<update-alternatives: using /bin/ksh93 to provide /bin/ksh (ksh) in auto mode

PROBLEM STILL:

Should just be able to enter 'ksh' at this point but doesn't work
left the non working ksh
then tried: chsh -s /bin/ksh  (and /bin/ksh93) but still no ksh.
 I'm not sure what to try at this point, and really like ksh.
Thanks,Keith

---

### Post by steeldriver on 2014-01-28
- what exactly happens when you type 'ksh'? is there an error message?

 - does your chsh get reflected in the passwd file i.e. if you do
```
getent passwd keith
```

Don't forget the chsh won't take effect until next time you log in (or start a new login shell e.g. 'su - keith')

---

### Post by keith14 on 2014-01-28
Yes,
ok> getent passwd keith
keith:x:1000:1000:Keith,,,:/home/keith:/bin/ksh93

ksh does nothing really, <esc>k       acts just as if it is escaping the k nothing shows on screen.

---

### Post by keith14 on 2014-01-28
hmm, I must have quit before the last post I sent made it. firefox is a very slow broswer compared to others
Yes,
$ echo $SHELL
/bin/ksh93
$ getent passwd keith
keith:x:1000:1000:Keith,,,:/home/keith:/bin/ksh93
$ echo $SHELL
/bin/ksh93
$ getent passwd keith
keith:x:1000:1000:Keith,,,:/home/keith:/bin/ksh93

note bash is nolonger used the prompt is changed to "ok> " in .bashrc

---

### Post by steeldriver on 2014-01-28
What is Esc-k supposed to do? I used to use Korn all the time - but not since the early 90s :) Does

```
echo $0
```

indicate you are in ksh? (the $SHELL variable can be misleading)

What feature(s) are you looking for that you can't get in bash btw?

---

### Post by keith14 on 2014-01-28
<esc>k will act like bashes up arrow with vi like search of previous commands as well as edit what ever entry you select in a vi like setting. that's y I like it. vi still my editor not gmacs

---

### Post by steeldriver on 2014-01-28
You know that bash supports vi editing mode, right?

```
set -o vi
```

[http://www.catonmat.net/blog/bash-vi-editing-mode-cheat-sheet/](http://www.catonmat.net/blog/bash-vi-editing-mode-cheat-sheet/)

---

### Post by keith14 on 2014-01-28
I think there may still be some residue from my first attemts to make ksh happen. MKS is also unix much of the same stuff B/W them but differences as well. My use of it was always in compatable mode where you had both systems available to you, it ran beside DOS...WIN. I will lookt around on the web for a bit.

---

### Post by keith14 on 2014-01-28
no but will look into it.

---

### Post by keith14 on 2014-01-28
hmm, very close to ksh only thing I notice is leave extra char in begining.
I will close this. Thanks for your help. Keith

---

