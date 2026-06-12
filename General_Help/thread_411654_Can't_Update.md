---
title: "Can't Update"
date: 2007-04-17
forum: General Help
---

### Post by kf4tqj on 2007-04-17
My update manager says that I'm up to date! Not likely, last time I worked on getting my updates I had about 50 to go. Also, synaptic says I've got everything that I can get. I thought maybe it dropped some or all of the repositories out but when I try to check on them I can only get the page that says that a change has been made and I need to reload.
This seems to have happened after trying to extract the Opera browser from a tar.
Any ideas? Now I can't get anything from anywhere.
All The Best,
Woody
ps: Running Dapper on a Thinkpad 600x

---

### Post by Jussi Kukkonen on 2007-04-17
Dapper doesn't get upgrades that often... 

Your explanation of the repository checking problem is not clear to me -- can you please explain with detail what you did and what went wrong? Did you try opening Settings->repositories in Synaptic? Or reading /etc/apt/sources.list directly?

> 
This seems to have happened after trying to extract the Opera browser from a tar.
Can't see this affecting your repository list in any way.

---

### Post by kf4tqj on 2007-04-17
I'll try to be more clear. I've only been fooling with Linux a few weeks.
After I boot, I usually get a message on screen that I have updates. I'm on dial up and have been working on them as time permits. When I first installed Dapper, there were about 200 updates. It said that it would take 1 day 18 hours. I kinow that there are at least 50 that I don't have yet including all the Open Office and Python updates. 
    Now I'm not getting that message so I went to System, Administration, Update Manager and it says that my system is up to date. 
    Add Remove programs used to show up under Applications but is gone now. Went to System, Administration, Synaptic Package Manager. and all the boxes are green indicating that I have installed them already. That lead me to reason that it must not be looking at the repositories so I went to settings, repositories. When I click that I get a message that the information has changed and that I have to reload. I do that but nothing happens. It won't install anything because it says that it is already installed.

---

### Post by Jussi Kukkonen on 2007-04-17
> That lead me to reason that it must not be looking at the repositories so I went to settings, repositories. When I click that I get a message that the information has changed and that I have to reload.
It shouldn't do that... can you paste these things here:
a) the contents of */etc/apt/sources.list*?
b) the output of *sudo apt-get update && sudo apt-get upgrade*

---

### Post by Chappy7777 on 2007-04-17
Same problem here. I have no access to hi-speed here in deep woods Canada. I can't afford satellite. I have 6.06 on my PC, and the downloads are about 200, and when I tried installing them a few at a time a month or so ago, it messed up Dapper. So I reinstalled 6.06 and have only updated thru Synaptic the files needed to have a current version of Firefox working. I was successful w/that. As a total Linux NooB, I was quite pleased that I was able to do that. 

I read somewhere, I think in the book I have called "Ubuntu for Non Geeks" (w/o which I'd likely have given up),
that if you are going to start downloading the Software Updates then get them all. I hope that on dialup this means we can download X number of files at a time. I can't have my old clunker P2 running for the 2 days or whatever it said. So I am leaving well enough alone, and waiting for Feisty Fawn to be out of Beta and onto mail out CDs. I am building a better PC to run Ubuntu on. I love the OS, but if I want time to read my bible (Chaplain and all) I'll make it, not read it while waiting 2 mins for Open Office to open.

I just hope the geek world doesn't do away with supporting dialup folks before we finally get wired for speed. 

God bless,

Chappy

---

### Post by zvacet on 2007-04-17
If you are on dial up and have many updates at the time,you can unchek some of them and install just part of updates.Next time you must see wich updates are left and download them.Making story short you don´t need to download all updates at once.Just look if there are updates wich depends on each other.

---

### Post by Jussi Kukkonen on 2007-04-18
> **Chappy7777 said:**
> So I reinstalled 6.06 and have only updated thru Synaptic the files needed to have a current version of Firefox working. 

There's no need to upgrade anything else, but please do the security upgrades, for your safety and the well being of the whole internet. Check your repository settings in Synaptic and unmark all other updates except "security updates"  -- I bet after reloading list the download isn't that big anymore.

---

### Post by kf4tqj on 2007-04-18
Jussi asked "It shouldn't do that... can you paste these things here:
a) the contents of /etc/apt/sources.list?
b) the output of sudo apt-get update && sudo apt-get upgrade
Here's the results:
kf4tqj@kf4tqj-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kf4tqj@kf4tqj-laptop:~$

kf4tqj@kf4tqj-laptop:~$ /etc/apt/sources.list?
bash: /etc/apt/sources.list?: No such file or directory
kf4tqj@kf4tqj-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: No such file or directory
:(

---

### Post by kf4tqj on 2007-04-18
Jussi,
    Reloading does no good. It says there are no updates, my system is up to date and I know that's not the case. Also, I can't go to any repository and install anything because it shows that I already have everything.

---

### Post by Jussi Kukkonen on 2007-04-19
Ok, we've found the problem. sources.list file (which contains the web addresses for the repositories) seems to be missing.

I built you a new one (using [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)):
```

# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages (stuff in restricted may not be free software)
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted 
#deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (stuff in multiverse is not free software)
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse 
#deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```
I've commented out the general updates as you can see, only security is enabled. That should do what you want. If you later want all updates just remove the #s from those two lines. *EDIT: Sorry, I remembered wrong: it was the other guy who didn't want all updates. Just uncomment the lines if you want everything.*

I can't really know if it has the contents you want, but it should get you started...

To get the file in use open an editor:
```
gksudo gedit /etc/apt/sources.list
```
(make sure the file really is empty at this point) copypaste the above list there and save. Then try synaptic (or the commands I gave you) again.

---

### Post by kf4tqj on 2007-04-19
Jussi,
    Thank you, thank you, thank you! Not only did that set things right I've learned a thing or two.
    Also shows how little I know and causes more questions. One is how did I  screw it up in the first pladce, but I may have the answer to that. So far the only way I can get things done is to copy code off of sites like this and paste them to the terminal. I may have done " gksudo gedit /etc/apt/sources.list " before and deleated it. 
    I'd never have thought about gedit giving me the actual source list to play with. I asumed that it was a copy and just deleated it. I think that's what happened anyway.
Still don't understand why I edit in a text editor and not at the terminal. Also, I've heard Terminal and Console. I had asumed that they were the same thing. Guess not.
Thanks for the help. I'll probably  be back again soon.
All the best,
Woody / KF4TQJ

---

### Post by Jussi Kukkonen on 2007-04-19
I just gave the command with *gedit* since I wasn't sure if you were familiar with terminal editors --  personally I use *nano* instead of *gedit* in cases like this (as it's fast and simple) and you can use any editor you like.

It's a bit of a problem that people just give commands for new users to run without explaining what they do. I admit I've been guilty on several occasions... A good advice for a newbie is to really look at the commands and find out what they do before running them (*man commandname* will usually get you started, but asking is also smart).

Good luck.

---

