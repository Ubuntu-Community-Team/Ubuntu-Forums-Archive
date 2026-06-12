---
title: "How do I look under the hood?"
date: 2007-04-14
forum: General Help
---

### Post by motin on 2007-04-14
Summary:
Multiple applications are crashing randomly and/or acting strange and/or hogging the CPU. I want to learn how to track down the reasons to this as well as create useful bugreports!

Long version:
One of my main reasons to leave Windows was that when all those programs including Explorer would go for a 3hour 100% CPU session, a crash or show randomly strange behaviour there was nothing one could do about it. Maybe you could track some error in the Application Log or find some other user having the same problem on the web (rarely with a solution however). 

Nowadays with a free OS I know that I am allowed to check, track and spot the reasons to this errenous behaviour. Great - but that is far from being easy imho. I am a web developer - not a os programmer. Despite this - I'd like to be able to - when the computer is acting erreneously - open the hood and see what is causing problems etc. 

I know about syslog and check it out to track error messages of NetworkManager. Good. I know about apport and it's vast improvements with Feisty (WOW how easy it is filing bugreports with apport when it finds a crash). 

But most times I have a problem it is a Thunderbird or Firefox window either just closing unexpentantly (without apport being activated), or a Window that is frozen - being able to spraypaint draggable windows on top of it and having to close with the X and then "Yes" on the "Application not responding" dialogue. No apport, no syslog messages, no nothing. 

How do I track down what is causing trouble?

---

### Post by x1a4 on 2007-04-14
Hi,

/var/log/ contains helpful log files.  Some of the more important ones include: 

/var/log/auth.log
/var/log/bootstrap.log
/var/log/daemon.log
/var/log/debug
/var/log/dmesg
**/var/log/kern.log**
/var/log/mail.log
**/var/log/messages**
**/var/log/syslog**
/var/log/user.log
**/var/log/Xorg.0.log**

Also look in: 

/var/log/fsck/checkfs
/var/log/fsck/checkroot

and: 

/var/log/gdm/:0.log

To check what daemons are running, execute

ps -A

run *man ps* for details.

To check memory/cpu usage: 

*free*, *slabtop*, *top*, *vmstat*

See the man page for each of these for details.

---

### Post by 23meg on 2007-04-14
It's also a good idea to run the problematic app from a terminal, and track its output for error messages, or other useful output that may hint to where the problem is.

---

### Post by az on 2007-04-14
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

[https://wiki.ubuntu.com/Strace](https://wiki.ubuntu.com/Strace)

[https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

---

### Post by motin on 2007-04-15
All the above replies are great! Already I have a lot more flesh on the bones for debugging what is going wrong!

Of course it would be wonderful if this was integrated in the OS. Something like: After a crash of say Firefox, a notification bubble would tell me: "Firefox just unexpectantly closed. Do you want to see the diagnostic output of the application in question just before it quit?"

---

### Post by x1a4 on 2007-04-15
To debug Firefox, start it from a terminal through a debugger.  

firefox -g

Open the Ubuntu Help Centre (*yelp*) and lookup the man page for the GNU Debugger (*gdb*).  With the *gdb* man page as a reference, use the debugger to see what's going on in Firefox.  Be sure to bookmark the debugger man page and any other pages you view often.  

Another trick I use to view man pages in the GUI is by saving them as PostScript files like so: 

man -t gdb > ~/docs/ref/man/gdb.ps

This will save the gdb man page as gdb.ps in ~/docs/ref/man/

---

### Post by 23meg on 2007-04-17
[QUOTE=motin]
Of course it would be wonderful if this was integrated in the OS. Something like: After a crash of say Firefox, a notification bubble would tell me: "Firefox just unexpectantly closed. Do you want to see the diagnostic output of the application in question just before it quit?"[/QUOTE]

That too exists, in the form of [Apport]("https://wiki.ubuntu.com/Apport").

---

### Post by cantormath on 2007-04-17
When I think of looking under the hood I think of:

> ~$ sudo dmidecode

---

### Post by motin on 2007-04-17
> **23meg said:**
> That too exists, in the form of [Apport]("https://wiki.ubuntu.com/Apport").

Well - I do love the newly improved apport in Feisty - but I have only seen it once or twice yet with at least a hundred unexpectantly shutdowns, 100% cpu session and iabilities to resume after sleep. Great when it works - but not very good at spotting the mentioned buggy behavior.

---

### Post by motin on 2007-04-24
I found the documentation for sysrq very useful. Attached is a PDF version on it - print out and save for being able to trigger traces of running tasks, crashdumps, reboot safely if the system is locked up and more.

---

### Post by motin on 2007-04-25
Now here is exactly what was looking for to investigate 100% cpu usage: The strace attach function of htop!

Added the section "Already running programs - using htop" to [https://wiki.ubuntu.com/Strace](https://wiki.ubuntu.com/Strace)

Copy here:

**Already running programs - using htop**

This is an easy way to run strace on a running program. You will, however, not be able to store the output of the strace in a logfile.

   1.Make sure strace and htop is installed.
      $apt-get install strace htop

   2.Start htop.
      $htop

   3.Use arrow keys to choose desired process, then press "s" to display a strace of the process on-screen.

---

