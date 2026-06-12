---
title: "Git as a user"
date: 2022-10-24
forum: General Help
---

### Post by kalish2 on 2022-10-24
Hello, far from being an expert, I am under ubuntu 18.04. I used to have git on my computer, but I realised some processed called bundle or postgres had users called "git" or "gitlab-+", which I alreaady find quite strange. Each time I try to kill those processes they appear again in the microsecond with a new ID and run like crazy while my system itself seems unaffected except for the excessive processing. I tried to mute them with several solutions like cpulimit but they seem completely unaffected by what I did. So I decided to remove all packages related to git: git and gitlab-ee. But even after that, those users and those processes are still there. To be clear about what the problem is: if I make a top, there are more than two users ("my name" and "root"), there is "git" and "gitlab-+" in addition, with processes running continuously, and I suspect they should not be there.
I never saw any list of process that looked like that so I am a little worried.

Thank you

---

### Post by &amp;KyT$0P# on 2022-10-24
Sounds like malware that doesn't actually have anything to do with git.

---

### Post by TheFu on 2022-10-24
Unix systems have lots of non-human users. These are part of the system security and very common.  If you didn't install gitlab, then there wouldn't be any extra users related to 'git'.  git almost always runs under the human's userid and only when they specifically do something to cause it.  A software developer running an IDE or in a terminal can cause git to do things, but I'd never expect my mother to have git installed on her ubuntu system.  It wouldn't make any sense.

So, the first thing is to figure out which git program is running, where it is and what it is really doing.
I'd start by using 'lsof' to see which files it is accessing and if it is connecting to the network for any reason.  There are lots of tutorials for how to use lsof. 

My company uses git in a team environment, but we don't use gitlab or any GUI for it.  that just isn't necessary, though the PHB types like a webGUI for some reason.  It isn't easy to automate things in a webgui, whereas it is very easy to automate normal CLI/shell commands, like 'git push' and 'git pull'.

As  halogen2 wrote, it could be malware.  Before I make that jump, I'd start by assuming ignorance first, before jumping to malicious reasons.
Daemons/services that restart are very common and usually desirable.  For 50 yrs, admins have created tools to do just that, so by itself, it isn't that odd.  systemd, which is the daemon launcher in modern Ubuntu systems makes automatic service restart trivial.

But, if it is malicious, how far back to your backups go?  You might need to restore from a time before any of this happened if it is malware.

---

### Post by kalish2 on 2022-10-25
I just checked today, and they seem to have all gone since I rebooted. We use git because it's asked by the university. What I find odd is that it was always running even when I didn't use git and as I said, it was logged as a user. Frankly I don't really like those version manager softwares, it might be great when you know what you are doing, but I feel like a windows user in front of a debian distribution when I use git, or an elephant trying to drink tea in a porcelain cup. anyway. I also suspected a malware. I might just have installed it like a **** or used it the same way, I don't know. I guess you can pretend being a user while you are another user. How a program can do that? How could I know that all processes under my name or under the root user are what they are supposed to be? (maybe root has extra protection). I will carry on inspecting.

---

### Post by TheFu on 2022-10-25
I suspect you are confusing "git" with some other program that might happen to have "git" in the name.  git doesn't run as a daemon.  It is an end-user command like wc or ls.  We run it, give it a command to accomplish and it returns, usually with plenty of feedback for what it did or an error if it couldn't do anything.

DVCS are amazing for a specific need.  For decades software developers used other methods and techniques.  OTOH, if you don't understand how DVCS works, then I can understand the confusion. Much of the power comes purely through social agreements, not anything mandated.  When you need to know more, watch a youtube video with an overview.  Don't worry about the actual syntax of any commands. The human-to-human agreement is much more important at the early stage.

Unix-like systems are all multi-user from the core out. Always.  They have always been that way, even on single human-user devices.  I don't know what more there is to day about that.  On my laptop that is only used by me, there are 60 user accounts, but only 2 are for humans.  The rest are used by different daemons/services to run in protected memory areas so they can't harm other running processes.  It is a security thing.  You should like that security, especially since we've had it since before 1970 and it has been working all this time in banks, insurance companies, telecom and spacecraft.  Oh ... and lots of people have been using it on their home computers since the mid-1980s too.

Root has few protections on Ubuntu. There are other OSes with many more limits on the root account. If you care, you can look up "roll based administration".  To my knowledge, Canonical has no plans to enable anything like that.  Most Linux systems don't have it outside a corporate environment and last time I was researching it (long ago), only RHEL and SuSE had packages to do it.  That isn't to say that Ubuntu can't do it, but there's no "official", approved, method that I'm aware.

If you want to know more, I'd suggest walking before jumping into the deep end of the ocean.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good beginner text to learn the basics.  No GUI.  Don't confuse the GUI with the OS. They are very different things.

---

