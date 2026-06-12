---
title: "new to ubuntu and shh, not sure how to do this"
date: 2015-07-25
forum: General Help
---

### Post by matthew_smith2 on 2015-07-25
SO I have created a Amazon EC2 Ubuntu instance and I have started some .bin program over the ssh terminal.  This is a spot instance that may be shut down and restarted often based upon my bid and current cost.  I would like some help doing two things:

1.  I would like a way to make my program start, with command line options, when the instance restarts.

2.  I would like to reconnect via ssh and see the output of the program as if I had started if via a ssh connection.

Is this possible?  How would I do it?  Thank you.

---

### Post by TheFu on 2015-07-26
Yes, it is possible.
Cannot answer how YOU would do it - but how I'd do it is outlined below.  The great thing about Unix/Linux is the nearly infinite flexibility. That is also a curse for new people, since there are usually 5-100 different ways to solve anything. The way I would do it is the best I know, but that doesn't mean it is the best for your specific situation or your current skills.  Someone with more skills than I might do it completely differently.  Make sense?

You have a little learning to start.  Be very careful at this stage just using websearch to get answers. There are thousands of options and most will not be good for you.

The approved way to start and stop a program is to write a daemon start/stop script, drop that script into /etc/init.d/, make it executable, then setup the correct links based on runlevel for it to be started and stopped as expected. The  update-rc.d program is normally used to make the links. Everything prior to that is done with standard tools - sudo, vim, chmod. If all this is greek (and I expect it is), get ready to learn some basic Unix CLI stuff first.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is an excellent free PDF book - or you can purchase it at any bookstore. By working your way through it, you won't have huge gaps of knowledge and you won't jump to expert level tasks before the other skills have been mastered.

Don't underestimate the quality of the Ubuntu Server Guide either. help.ubuntu.com has it.

To see the output of a command, Unix people generally redirect that output to a file then we can review it later by using more/less or tail if we want to see what is being appended "right now".

There are lots of example start/stop scripts in /etc/init.d/ ... which you can mirror/copy.  Some are overly complex, so look for some easy ones to use as the starting template.

Anyway - hope this helps.

---

### Post by Lars Noodén on 2015-07-26
> **matthew_smith2 said:**
> 2.  I would like to reconnect via ssh and see the output of the program as if I had started if via a ssh connection.

In your startup script, you would want to launch your program inside a [tmux](http://manpages.ubuntu.com/manpages/trusty/en/man1/tmux.1.html) or screen session.  I recommend tmux these days.  Then later, after the instance is fully started, you can log in with ssh and then attach to the existing tmux session and see what has happened and is still happening.  

As mentioned by TheFu, the TLCL is a good starting point and has a good section on scripting.

---

