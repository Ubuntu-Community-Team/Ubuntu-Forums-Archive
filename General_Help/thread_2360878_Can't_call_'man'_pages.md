---
title: "Can't call 'man' pages"
date: 2017-05-09
forum: General Help
---

### Post by mjones1337 on 2017-05-09
Can't figure out why but I can't seem to call up any of the manual pages. When I try I get the following:

```
:/$ man ls
man: can't execute less: Is a directory
man: command exited with status 255: (cd / && LESS=-ix8RmPm Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$PM Manual page ls(1) ?ltline %lt?L/%L.:byte %bB?s/%s..?e (END):?pB %pB\%.. (press h for help or q to quit)$ MAN_PN=ls(1) less)  
```

I've looked around the forum and tried a few things that have worked for others but unfortunately their fixes didn't work for me. I've tried both ```
export MANPAGER=less
``` as well as checking ```
sudo update-alternatives --config pager
``` which was set to run /bin/less in auto mode. I'm attempting to learn Linux and doing so without manuals is proving slightly difficult. Any help you all can offer would be greatly appreciated!

---

### Post by Habitual on 2017-05-09
I'd look in your ~/.bashrc

---

### Post by SeijiSensei on 2017-05-09
What version of Ubuntu are you running?  On my 14.04 system /bin/less is a file about 150K in size.  I'm not sure where the "is a directory" error is coming from.  I am a bit puzzled by the lack of quotes around the long string literal following "LESS=" in the command that was reported back.  I also don't know why it appears the "man" command is running a script.  /usr/bin/man on my machine is a binary.

---

### Post by mjones1337 on 2017-05-09
Thanks for the input! I realised I was trying to run all this through the default cmd prompt and not Ubuntu. When I switched over the 'man' commands started worked correctly. I still have no idea why it wasn't working on the other side of things but whatever.

[Edit] Cancel that early statement about it being fixed. Things are once again not working. As I'm fairly new to Ubuntu and linux in general what did you mean by > [COLOR=#000000]I'd look in your ~/.bashrc[/COLOR] And what would I be looking for?

---

### Post by steeldriver on 2017-05-09
What do you mean exactly by

> trying to run all this through the default cmd prompt

Are you using a WSL?

---

### Post by QIII on 2017-05-09
Hello.

You use the term "default cmd prompt" and have not yet said what version of Ubuntu you are using.  This makes me wonder if you are using Windows 10 with the command line Linux emulator.

Some information would be helpful.

---

### Post by mjones1337 on 2017-05-09
Apologies for the lack of useful information. I'm still trying to wrap my head around all this. My setup is indeed using Ubuntu through Windows 10 (Bash on Ubuntu on Windows). I'm currently using version 14.04. I attempted to upgrade to 16.04 using 'sudo do-release-upgrade' but that yielded 'No new release found'.

To my earlier statement regarding the cmd prompt I was opening a cmd prompt and then running 'bash' to run the shell. I thought maybe that was the problem but it starting happening again even when starting straight from the Ubuntu shell.

---

### Post by steeldriver on 2017-05-09
OK - can you post the output of

```

file -L $(which less)

```

Also, it might be worth trying

```

man -P /usr/bin/less ls

```

(the command line -P option should have higher precedence than any pager specification variables that might be in play).

---

### Post by mjones1337 on 2017-05-09
I'll start by saying I went ahead and uninstalled and then reinstalled Ubuntu in an attempt to get the newer, 16.04, version. Unfortunately that didn't work so I'm still using 14.04 however all the manual pages are once again working. So whatever was causing the error seems to have been fixed/reset. Thanks to everyone who helped! Just for completeness sake the outputs requested are below.

> **steeldriver said:**
> OK - can you post the output of

```

file -L $(which less)

```
/usr/bin/less: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=539cf624699477e3e069b6c4e4b33842f22be2d2, stripped  

> Also, it might be worth trying

```

man -P /usr/bin/less ls

```

(the command line -P option should have higher precedence than any pager specification variables that might be in play).

The above cause the manual to open.

For my own knowledge is there any difference between running Ubuntu via the cmd prompt (cmd -> bash) versus using the 'Ubuntu for windows' icon from the start menu nor desktop?

---

### Post by Habitual on 2017-05-09
```
\man <page>
``` 
should also work.

I've had 
```
export LESS='FiX'
```
in my ~/.bashrc since 2010 and it was for just this purpose, at that time. I haven't changed it. Still works?

---

