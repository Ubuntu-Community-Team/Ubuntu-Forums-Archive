---
title: "Strange bash shell tab completion behaviour"
date: 2007-04-30
forum: General Help
---

### Post by donut on 2007-04-30
I've got what may seem like a very trivial issue on Ubuntu 7.04 which is annoying me cos I use the feature all the time...

I have a symbolic link in my home directory which is actually a link called 'share' to a locally mounted windows partition so that I can get to my shared docs easily on my dual boot system. On Fedora and other distros, when I am in a shell in ~ and type 'cd sha' followed by the tab key, this completes to 'cd share/'. On Ubuntu this only completes to 'cd share' and I then have to hit tab a second time to have the '/' added at the end before I can then start typing the first few letters of the next folder down and then tab completing again. For folders that are 'real' and not symbolic links, the shell in Ubuntu behaves as it should and always includes the '/' at the end of the folder, first time, when using tab completion.

This can be easily demonstrated by doing the following:

> cd ~
> mkdir realdir
> touch realdir/realfile
> cd rea    [then hit tab to see this completed to 'cd realdir/']
> cd ~
> ln -s realdir/ fakedir
> cd fak    [then hit tab to see this completed to 'cd fakedir' and not include trailing '/']

Does anyone have any idea how I can correct this behaviour in Ubuntu? Do I have to change something in the Ubuntu generated ~/.bashrc script or something else?

Thanks

Paul

---

### Post by aiwarrior on 2007-05-01
Hi i don't know if i understood your problem.
When the shell dosnt put the "/" it means theres also a file that matches the name of the directory. For example

>mkdir name
>touch name
>cd na[ hit tab will show only "cd name" not "cd name/", there's an ambiguation point ]

---

### Post by donut on 2007-05-09
I don't have any other file of similar name. Could it be that bash is detecting the dir symbolic link as a file and thus not include trailing / . However because it is a symbolic link to a directory I want it to behave as it would for a directory - as it does on all other Linux distris I've used

---

### Post by stylishpants on 2007-05-09
The readline library handles completion in bash.  Readline has an option specifically for this behaviour, it is called "mark-symlinked-directories".   To change this behaviour, you need to explicitly set the option in your ~/.inputrc file, which is where you can define readline settings that you want to override.

Run this command to put the option you need into your .inputrc:
```
echo "set mark-symlinked-directories on" >> ~/.inputrc
```

Then restart your shell (exec bash) to get the new behaviour.    All new shells will behave the way you want.

For more info, see the man page:
```
man readline | less -p mark-symlinked
```

---

### Post by donut on 2007-05-14
excellent - this worked a treat - I was sceptical that I get to a solution so thank you very much

---

### Post by bryceharrington on 2008-01-11
Awesome, this has been annoying me for quite some time!  Thanks for the solution!

---

### Post by &amp;wP*!) on 2008-01-26
I have two problems in this issue.

- Filename completion works if and only if I type ESC three times, but not 2 times.
- Filename completion sometimes doesn't work if there is only one file or directory in a file. In this case shell cannot complete the only file/dir name.

I have looked at manpage of readline but I could not find any answer for these.
I am using Microsoft keyboard, don't know whether it has to do with it.

---

### Post by elcasey on 2008-01-26
If you're a big fan of tab-completion, as I am, you might want to look into running zsh. I switched about four months ago and I couldn't be happier. You can find .zshrc files on dotfiles.org (including mine) so you don't have to get involved in the arduous task of writing your own from scratch.

My pal jdong wrote an excellent piece about zsh [on our old Wordpress blog, FriedCPU](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/), and you can check out the [official zsh intro page](http://zsh.sourceforge.net/Intro/) as well.

I can't think of any reason not to like zsh...it's amazing.

---

### Post by &amp;wP*!) on 2008-01-26
Hello elcasey, thank you for the precious answer. At the moment I do not intend to replace my current shell. I have not seen this behaviour before. If someone shares a solution, would be great.

---

### Post by &amp;wP*!) on 2008-02-02
> **pencuse said:**
> Hello elcasey, thank you for the precious answer. At the moment I do not intend to replace my current shell. I have not seen this behaviour before. If someone shares a solution, would be great.

Hello all, I have found the reason. That the filename completion occurs in BASH only with 3 times ESC key press, has to do only with BASH.

I have just installed TCSH from [http://packages.ubuntu.com](http://packages.ubuntu.com) to my Gusty Gibbon, changed login shell using **chsh** utility, I have logged off and on, it turned to TCSH.

TCSH does not have this strange behaviour.

I don't to be *very* certain; but I think I will not use BASH unless I need it.

Long live TCSH!!!

---

