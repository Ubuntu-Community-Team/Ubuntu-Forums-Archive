---
title: "Is there a Terminal with a &quot;PowerShell&quot; like interface?"
date: 2015-09-20
forum: General Help
---

### Post by eyeonyouproductions on 2015-09-20
Hi all,
Finally committing fully to a Linux Distro. I've just not had good experiences before, but Ubuntu is absolutely perfect. ;)

Since I'm doing a lot of stuff in the Terminal, I'm wondering if there is one that I could store common commands or scripts and launch them. I referenced PowerShell in the description because that has a good example of what I'm looking for, a sidebar where I could save/store/run common commands... I don't need it to function like PowerShell, just have the options on the side, if that makes sense.

Also, now that I think about it, is there anything similar to a debug environment where I could test the potential results of running some commands, or somehow create a restore point to roll back anything I screw up? Also, I have had a couple of times that going through the Terminal, some attempts fail and I end up taking another route. Does it hurt anything to leave these installs partially done? It's why I would be looking for a sandbox, debug environment or system restore.

Thanks, I hope all of these belong together(Didn't want to make a whole bunch of different posts if they were all related enough to be in one), and I hope I'm being clear enough. Thanks in advance for any help.

---

### Post by monkeybrain20122 on 2015-09-20
All your commands are store in the hidden file ~/.bash_history. You can see all your command history and search through them by opening it in a text editor, or you can display them with the history command.

---

### Post by TheFu on 2015-09-20
You have excellent ideas, but bringing "windows methods" just doesn't apply with Unix systems.
a) powershell was modeled after almost any Unix shell - bash, ksh, sh, psh, zsh are all examples. By default, your "shell" is **bash** in  ubuntu. It is built-in.  Most system admins write little utilities in bash scripting.
b) System restore is something from Windows because "backups" are so difficult. On Unix systems, backups are really easy.  All user settings are stored in 1 place - your HOME directory.  System settings are stored in /etc/ - so, if you backup those things, you have the equiv of a restore point - assuming I understand what that means.
c) sandboxes are just a directory or you can use normal software development tools like rcs, sccs, git, svn, cvs or 20 other tools to manage your code changes.

Scripting, which is relatively new to Windows, has a 40+ year history on Unix systems. The people who came before you and I were really smart - geniuses. The entire architecture of Unix systems creates a development platform out of the box without adding anything else.

So ... first you need to start thinking the Unix way and un-learn about 80% of what you've learned from Windows.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) is my best recommendation to accomplish that.  Read the  first 4 links to start thinking the Unix way - should take about 30 minutes, but will hopefully provide a good start.

There are some other really smart people who will read this. Getting some different viewpoints can only help.

And lastly, a beginning scripting guide will be very helpful:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html) - don't start here. Until you get a little more "Unix thinking", it will not be helpful.

After you create a few small scripts, my scripting 101 post will be helpful: [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) It is full of *best practices* that I've learned from experts over the last 25 yrs.

Hopefully, my idea of *powershell interface* isn't too far off.  I've written about 10 powershell scripts - but I did it in the Unix way, so perhaps my ideas about PS aren't correct.

And have fun with this stuff!  Anything you do more than 2 times should probably be scripted.

---

### Post by eyeonyouproductions on 2015-09-20
First off, thanks for the tip on the 'system restore'. That's a great thing to know, it would make it easy. It's always a pain in the butt to spend all of this time figuring it out and then not remembering how you did it when it comes time to set up a new computer... And yeah, the Windows restore point is something you can run before you make any kind of changes, and if something craps the bed, you can just roll it back. It's actually a really nice implementation that came with Win 7.

The PowerShell comparison was really with the idea to have the second window with common commands, but really, I'm just learning Windows scripting, too, so I'm not committed to that format. It's kind of a 'getting tired of saying "I wish someone would make this process easier, I'm sure it's possible." thing', so I've really only been playing with that a short time. Those links are going to be a great help, thanks!!

---

### Post by CantankRus on 2015-09-20
Try [**_[COLOR="#B22222"]clicompanion[/COLOR]_**]("https://help.ubuntu.com/community/clicompanion").
Hasn't been updated for a while but works here on 14.04.
The above link will point you to deb file. 
No use adding the ppa as clicompanion hasn't been updated for a while but deb works here on 14.04.

---

### Post by eyeonyouproductions on 2015-09-21
Hey, this looks like it will work. Something that will help me transition to learning these commands.

I appreciate all of the quick replies so far. This has been far the easiest time I've tried the Linux route so far, so I'm getting into far more technical areas than I managed before. Like I said, thanks for the help!

---

### Post by VMC on 2015-09-21
Also "aliases" work wonders also. You combine multiple commands to do more. Example:
```
[COLOR=#000000][FONT=Consolas]alias x[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][FONT=Consolas]'command1;command2;command3;'[/FONT]
[COLOR=#000000][FONT=Consolas]alias y[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][FONT=Consolas]'command1 && command2 && command3'[/FONT] 
```
Then "&&" will continue if the previous command is successful.

You can make aliases very complex and then run with a single command.

---

### Post by Lars Noodén on 2015-09-21
And in bash and some other shells you can scroll back through your history by pressing the up arrow.  You can also search your history by pressing ctrl-r and then typing what to search for.

---

### Post by TheFu on 2015-09-21
> **Lars Noodén said:**
> And in bash and some other shells you can scroll back through your history by pressing the up arrow.  You can also search your history by pressing ctrl-r and then typing what to search for.

Being efficient in a shell is a 10 yr learning thing.  If you are typing more than 3 characters at a time, you are doing it the hard way.  Shells have thousands of features to make life easier, but being new, makes it hard to deal with just a few of those.  Start by learning about "tab completion" - it will save you from lots of typing.  There are lots of youtube videos and for some of these "efficiency" things, seeing really is the only way to learn about each.

For example, I haven't used ctrl-r in 15 yrs, but I use the history all the time with !{number} or !{2-letters} to run a command I ran previously.  I always have at least 4 terminals open when I'm scripting.
a) to run the program
b) to edit the program
c) to review manpages about each command
d) ... something else might come up ... plus I script in perl whenever a bash script becomes longer than 1 page.

BTW, there are literally thousands of example bash scripts on your Linux install right now. The OS is lousy with them to get things done. Some are really easy to understand and other seem to be written in a completely different language.  When you login to the system, a bash script run to setup your environment - just for your userid.  Windows has this too, but most Windows people never touch it, since it is buried in a sub-sub-sub-sub menu.  Windows software developers know where it is, because they've been forced to find it. On Unix systems, it is easy to keep environment variables either in 1 place or have them placed into the startup script for the specific program.  JAVA_HOME is required for all java programs, as an example. Pretty much **every** other program can have environment variables to override default behavior. This is part of the Unix design philosophy.  That philosophy can be seen in 80% of the programs on the system.  IMHO, if you just point-n-click on a Unix system, you are only using 10% of the power at your fingers.  Scripting and automation is the other 90%.  The OS has well-proven tools for this stuff. It isn't part of each program - rather it is an OS service provided to all users of the system.

Anyway - don't feel bad about thinking "they made it hard" ... we've all been there. Just remember that the people who came before truly were geniuses and that learning "why" they did something a certain way will come.  People like me get that same frustration when we use Windows - why did they make is so hard?  Seems like microsoft went out of their way to handicap users. Why?  Learning Linux is like learning a new language. That is hard. Your brain will hurt as it is overwhelmed by all the "new" ideas.   A computer is not a computer. ;)

---

### Post by eyeonyouproductions on 2015-10-02
> **TheFu said:**
>  Seems like microsoft went out of their way to handicap users. Why?

LOL, I get that feeling with OSX. Jesus, stuff that I can a do a million ways on a Windows machine, I either can't do on a Mac at all, or I suddenly have to add a billion different steps. An example is skinning a media player. When I was working with graphic design, I'd have whatever Adobe product I was working in, my Adobe palettes, email, Filemaker, and maybe even a Finder window or two. I wanted to skin the mini player for iTunes so I could find the damn thing in all that traffic. It's pretty much impossible to find any kind if skinnable media player, and the ones you do find stopped working around Tiger. For your overall theme, you can have everything be any color you want as long as that color is either blue or silver. Themes are about more than just making your desktop look like a Hello Kitty factory just threw up on your monitor, they really can help with workflow. Apple doesn't want you to do that. If you want to change what they have set in stone for you, it's you that has the problem, not them. I see this in everything that rolls out from them.

With Linux, I see it with installing software mostly. It's kind of silly as the standard user to have to go thru all of the extras steps of making and compiling and building just to install something. I think the Software Center is a lifesaver. OTOH, I see a lot of benefits to doing stuff in the Terminal, I just have trouble remembering all of the commands. That's why that recommendation of the CLICompanion is perfect. I get a searchable window for common commands, and a Terminal at the bottom. I can even choose a command to restart my panel or get updates that I just have to select and click 'Execute'. I still find Windows easier, but with this Terminal, the Software Center, and the ease of installing and using Ubuntu, I am most definitely having my most positive Linux experience yet. I'm almost ready to switch my wife over so we don't have to play the Windows snooping in my private data game anymore.

The help in just this thread has been awesome, it's great to know there is a community like this, online help is getting to be more of a forum for making fun of the person asking the questions nowadays, it's good to see that that isn't the case everywhere!! :D

---

### Post by TheFu on 2015-10-02
I tried OSX for 2-3 weeks, full-time.  Extremely frustrating. Gave it back. Apple seemed to want to call normal things by some other name - don't know why.  OTOH, I wanted a Unix machine and expected it to work in the way I know AIX, Solaris, HP-UX, OSF, Digital Unix, Irix and some Linuxen to work. OSX is NOT that sort of system. BTW, I didn't understand most of your OSX paragraph - all those Mac-specific terms.

"Software Center" - never used it.  If you need a GUI, try out the not-dumbed-down **synaptic**.  
It shows all the packages available.  
```
sudo apt-get install synaptic
``` 
Not so hard to get it installed and much easier than trying to explain point-n-click methods.  That is why I much prefer the shell methods.  *Generally*, they work on desktops AND servers, so I don't have to learn 20 different ways to accomplish a task for 19 different GUIs.  The shell is the shell on Ubuntu. Very few surprises.  Most of the commands I learned in 1993 are still working the same.  Saves on all that relearning when a new GUI is provided to users.

I've built up hundreds of scripts for different tasks.  Most still work even though they were written for a Unix OS, not Linux.

Anyway - glad you are enjoying this.

**History**
BTW - there is a 'history' command in most shells with an entire set of options.  man bash will show what is built-into the bash shell interpreter. I suspect that is what you use, but there are 20 other shells in use today.  I use an alias for history (h), to get access to it quicker.
**h|grep foo** - will show me all saved cmds in my history that have 'foo' inside them. Sometimes we don't know the first letter of the command, but know something inside it. I think the default setup is NOT to save and command that doesn't begin with a non-whitespace character, so there are times when I specifically add a space to the beginning for security reasons.  There is a solution for having only cmds over 4 characters or 10 or whatever number you like saved, but nothing shorter too. I'd have to check the manpage for the exact setting. There  are multiple sub-cmds in the bash manpage about history use and techniques. Very few people make full use of it, including me.

---

### Post by coldraven on 2015-10-03
On every install that I've done in the last few years I always do the trivial changes mentioned in the link below. It is incredibly useful! For example, last week I wanted to clone a git repository and could not remember the exact command. In the terminal I just type "git" and press the up arrow, this finds the last instance of the command and I can copy/paste a new URL to it. Pressing the up arrow again will scroll through all uses of the git command that I have ever used.
If I had only typed "g" I would find all commands starting with that letter. (for example, get_iplayer, gs, grep)
In the terminal Copy is Ctrl+Shift+C, paste is Ctrl+Shift+V

[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

---

