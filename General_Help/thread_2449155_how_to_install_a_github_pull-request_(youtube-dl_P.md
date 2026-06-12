---
title: "how to install a github pull-request? (youtube-dl PR)"
date: 2020-08-21
forum: General Help
---

### Post by fluffy20470-50233 on 2020-08-21
Solved. I was able to install it by using pip3 (python3-pip) instead of pipx.  pip3 worked with the github URL as-is (no need to download the zip file  manually).

//////////////////////////////////////

I want to install this pull request for youtube-dl
[https://github.com/ytdl-org/youtube-dl/pull/25895](https://github.com/ytdl-org/youtube-dl/pull/25895)

Apparently I can install it by using:
```
pipx install [https://github.com/runraid/youtube-dl/archive/tiktokwatermarkless.zip](https://github.com/runraid/youtube-dl/archive/tiktokwatermarkless.zip) --force
```
(source: Github user notpushkin [https://github.com/ytdl-org/youtube-dl/issues/23264](https://github.com/ytdl-org/youtube-dl/issues/23264))
but this gives me the error 
```
Package cannot be a url
```

I also tried to download the .zip file manually and install it with:
```
pipx install youtube-dl-tiktokwatermarkless.zip --force
```
and got the error:
```
Could not find package youtube-dl-tiktokwatermarkless.zip. Is the name correct?
```

What am I doing wrong? Is there another way to install this pull request?

---

### Post by CelticWarrior on 2020-08-21
I know nothing of this but the error messages are self-explanatory.
"[COLOR=#000000][FONT=&quot]Package cannot be a url" means exactly that, the command doesn't accept an URL to download the package, only the package itself. And if you didn't download it then logically when you try the command to non-existent package it will complain that "c[/FONT][/COLOR][COLOR=#000000][FONT=&quot]ould not find package..."
Maybe you need to download it and then run the command in the some folder where you downloaded it?[/FONT][/COLOR]

---

### Post by fluffy20470-50233 on 2020-08-21
> **CelticWarrior said:**
> I know nothing of this but the error messages are self-explanatory.
"[COLOR=#000000][FONT=&amp]Package cannot be a url" means exactly that, the command doesn't accept an URL to download the package, only the package itself[/FONT][/COLOR] 

I just assumed it would work since that was the exact command written by notpushkin on github


> **CelticWarrior said:**
> [COLOR=#000000][FONT=&amp] And if you didn't  download it then logically when you try the command to non-existent  package it will complain that "c[/FONT][/COLOR][COLOR=#000000][FONT=&amp]ould not find package..."
Maybe you need to download it and then run the command in the some folder where you downloaded it?[/FONT][/COLOR]
That's exactly what I did. I downloaded the .zip file, went to the folder it was in and opened terminal with (right click > open terminal here), and typed:
```
pipx install youtube-dl-tiktokwatermarkless.zip --force
```

---

### Post by CelticWarrior on 2020-08-21
Then you need to contact the devs.

---

### Post by fluffy20470-50233 on 2020-08-21
> **CelticWarrior said:**
> Then you need to contact the devs.

Wouldn't this be something to do if there was something wrong with  the pull request? I haven't even gotten past the installation stage,  which I assume is due to my lack of knowledge with pipx & linux in  general, not because the pull request is broken.

---

### Post by ActionParsnip on 2020-08-21
Isn't youtube-dl in the Ubuntu repos? I thought it was......

---

### Post by ActionParsnip on 2020-08-21
Where did you download youtube-dl-tiktokwatermarkless.zip to? If it's in your ~/Downloads folder then you need to run
```

cd ~/Downloads

```
FIRST and then the command to install it (I guess). The OS won't go hunting for the file you named. It doesn;t work like that. Windows doesn't work like that either. If you file is not in the folder that the terminal is currently sat in then it won't find the file.

For completeness:
```

cd /tmp
wget https://github.com/runraid/youtube-dl/archive/tiktokwatermarkless.zip
sudo pipx install ./youtube-dl-tiktokwatermarkless.zip --force

```

I don't know if this works as I've never used the application. Hopefully this flys. Not even sure if sudo is needed to install using the pipx command. Have a play

---

### Post by fluffy20470-50233 on 2020-08-22
> **ActionParsnip said:**
> Where did you download youtube-dl-tiktokwatermarkless.zip to? If it's in your ~/Downloads folder then you need to run
```

cd ~/Downloads

```
FIRST and then the command to install it (I guess). The OS won't go hunting for the file you named. It doesn;t work like that. Windows doesn't work like that either. If you file is not in the folder that the terminal is currently sat in then it won't find the file.

For completeness:
```

cd /tmp
wget https://github.com/runraid/youtube-dl/archive/tiktokwatermarkless.zip
sudo pipx install ./youtube-dl-tiktokwatermarkless.zip --force

```

I don't know if this works as I've never used the application. Hopefully this flys. Not even sure if sudo is needed to install using the pipx command. Have a play

This still gave me the package not found error unfortunately. I know I was in the correct folder because I could use other commands to interact with the zip file (like "md5sum youtube-dl-tiktokwatermarkless.zip").

I was able to install the pull request by using pip3 (python3-pip) instead of pipx. pip3 worked with the github URL as-is (no need to download the zip file manually).

---

### Post by TheFu on 2020-08-22
I would just clone the repo first, then look through the different branches and checkout the branch I wanted, then install that.

The repo version of this software is always out of date. Has been for years.  It changes fast due to website changes, so having the git version really is the only solution for this type of software.

Less pip. More git is needed.  Learn to use git. There are only about 5 commands to know.

IMHO.

---

### Post by fluffy20470-50233 on 2020-08-22
> **TheFu said:**
> I would just clone the repo first, then look through the different branches and checkout the branch I wanted, then install that.

The repo version of this software is always out of date. Has been for years.  It changes fast due to website changes, so having the git version really is the only solution for this type of software.

Less pip. More git is needed.  Learn to use git. There are only about 5 commands to know.

IMHO.

so with pip3 I just needed to type 1 line
```
pip3 install https://github.com/runraid/youtube-dl/archive/tiktokwatermarkless.zip --force
```

what would I need to do with git? (I just started using linux and this terminal stuff is really over my head)

---

### Post by TheFu on 2020-08-22
github is a git repo service.  git is a DVCS.

From the manpage:
```
DESCRIPTION
       Git is a fast, scalable, **distributed revision control system** with an unusually
       rich command set that provides both high-level operations and full access to
       internals.
```

The git manpage points out that there is a command - gittutorial 
```
       See gittutorial(7) to get started, then see giteveryday(7) for a useful
       minimum set of commands. The Git User’s Manual[1] has a more in-depth
       introduction.
```

git is used by developers to keep track of changes, reasons for changes, and branch software versions. It is how most F/LOSS software teams work together.  There are other DVCS, but none are as popular.  There are other VCS (not distributed) which have been used over the decades too.  cvs, svn, rcs, sccs are examples of the F/LOSS versions. There have been and still are many commercial VCS - I've used StarTeam and MS-SourceSafe in a few companies.  Oddly, MS-SourceSafe had corruption problems, which defeats the reason to use a VCS.  At home, I've used rcs and git over the decades - even on software that only I work.  VCS are great for teams, but just as important for individual programmers.  rcs has saved me from huge mistakes at least once a year before I switched to git.  

But this isn't a class on any specific VCS. There are lots of those already on youtube.  When I first needed to learn git, I watched a video presentation by Randall Schwartz that he gave at Google. That 50 minutes or so explained stuff that isn't intuitively clear to outsiders.

All git repos are the same.  It is simply a social agreement between developers on the team which repo will be "the repo" for their project. By cloning the youtube-dl repo, you've got all the code, all the changes, since the beginning, on your local machine. 

You can modify that code and use it for your nefarious purposes and as long as you don't share it, nobody would know.  Some code has specific license requirements (AGPL) that mandate you share changes with the community.  That's called a "pull" request where you make your repo available to the upstream and send the maintainer of that repo a link so she can "pull" your code.  Not all licenses require this mandatory sharing and sometimes the requirement to share only happens when you start sharing the code elsewhere (GPL and LGPL).  Some licenses don't require any sharing at all - MIT, Perl, BSD, Apache, and a few others. They just require that credit for any coder before you is given. That's why iOS from Apple and Roku devices isn't Open Source. They use BSD code in those devices.  TiVo uses Linux, so they have to share their code. Same for most Linux-based routers. Cisco, Linksys, TP-link, D-Link, Ubiquiti, Microtek, all have to share their code for the products based on GPL and LGPL libraries.  A few of them were sued in court so they would comply.

Probably more than you cared to know. Software licenses matter to all of us who use Ubuntu. It is because of the GPL that we get it and most Linux software for minimal/$0 cost.  There are some fine lines that only Oracle's lawyers seem to have found which allow charges for GPL software.

---

### Post by ajgreeny on 2020-08-22
Thread Closed.

See [https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

---

