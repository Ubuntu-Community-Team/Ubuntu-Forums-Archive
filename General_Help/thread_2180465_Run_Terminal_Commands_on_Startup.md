---
title: "Run Terminal Commands on Startup?"
date: 2013-10-13
forum: General Help
---

### Post by Line-X on 2013-10-13
Hello!  I would like to have the terminal open up and run a command in a window on or right after the DE starts up. I am using Xubuntu.  To be more specific, I would like Xubuntu to open Terminal windows in specific positions and sizes, in a specific workspace and run specific sudo commands automatically. Is this possible? Could it grab my password from login instead of having me enter it again?   P.S. I am not new to Linux, to Forums or to the Ubuntu Forums, but it's been a while since I've posted anything relevant  and the account is new.

---

### Post by volkerbradley on 2013-10-13
Pardon me if my response is not a good way of doing all this.  I'm not a programmer and don't use Xubuntu and so am not sure that any of this will work in your distribution.
If I wanted to do this, I would add "yourloginname ALL=(ALL) NOPASSWD: ALL" to the bottom of the sudoers file
Then I would make a bash file that runs the desired sudo command and make that file executeable
Then make a small file in /usr/share/applications that executes this bash file and set it to display the terminal
Lasly, add this program to the the autostart menu

---

### Post by Lars Noodén on 2013-10-13
Don't give blanket sudo to that account, too much can go wrong.  You can give NOPASSWD privileges for just specific programs and leave it at that.  You can even define which specific parameters are allowed to be passed to those particular programs.  Here are two examples.

```

%users ALL=(ALL) NOPASSWD: /usr/local/sbin/ddclient ""
%users ALL=(ALL) NOPASSWD: /usr/sbin/gpioctl gpio0 6 on, \
                          /usr/sbin/gpioctl gpio0 6 off, \
                          /usr/sbin/gpioctl gpio0 6 [012]


```

---

### Post by buzzingrobot on 2013-10-13
If you do not explicitly need to run the commands in a visible Terminal, i.e., if you don't want to actually see the commands run, you might put them in a shell script that runs at login.

---

### Post by JKyleOKC on 2013-10-13
And you can invoke that single shell script with sudo, and not have to prefix each command inside it with sudo. This means that the NOPASSWD option can specify just that shell script, thus minimizing the security risks. When a script is executed, bash clones off a secondary shell using the privilege level under which it's running at the time, so all the included commands inherit root permissions.

---

