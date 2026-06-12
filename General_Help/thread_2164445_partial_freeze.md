---
title: "partial freeze"
date: 2013-07-31
forum: General Help
---

### Post by gulmer on 2013-07-31
My desktop goes into a partial freeze, the cursor still moves, the keyboard works, what stops working are the icons on the ubuntu top panel. The cursor will move over the panel, but there is no action. The close,min.,and move to dock icons for the existing open window (like Firefox when at max) disappear from the top ubuntu panel. Even though the cursor moves around there is no response to clicking with the mouse. All this can be fixed with a log out/log in action, then the desktop behaves. I was hoping that a new kernal update would fix the problem,but it didn't. I'm running 12.04LTS on an AMD dual core processor with an Nvidia graphics card upgrade.When I first noticed the problem I checked for additional drivers and found the Nvidia driver I initially selected was disabled, so I chose the recommended driver and tried that to solve the problem, no luck. Went back to driver 73, the first driver used at installation, still did not fix the problem. 
I'm stumped.

---

### Post by TheFu on 2013-07-31
Which DE are you running?  Unity?  Partial freeze can just mean that the DE is stuck, not the entire OS.  From another computer on the network, can you remote in using whatever method you like and does everything work fast as usual?

---

### Post by gulmer on 2013-07-31
Unity and the driver I stated as 73 is actually 173. Since the keyboard's ctrl-alt-delete still works, I can get the log out to come up and hit enter on keyboard which gets me back to the log in screen. Probably can remote in, haven't tried that yet and when I log back in, everything is up to speed. Just takes a double log in, like double clutching a standard shift car that won't go into gear on the first clutch shift.

---

### Post by TheFu on 2013-08-01
It would be helpful if you didn't stop the GUI that appears locked up - came in from another PC and looked at the process table to see which process is sucking all the CPU.  **top** is the normal CLI program to see that information.
Any other questions?

---

### Post by dino99 on 2013-08-01
Looks like a compiz crash; into a terminal, run:

> dconf reset -f /org/compiz/
> setsid unity

---

### Post by gulmer on 2013-08-03
The CPU isn't getting sucked up when this happens. The meters are at 0, and I'm not sure on how to get into this computer from another. Not using compiz, this computer doesn't like compiz, so I'm using metacity.

---

### Post by TheFu on 2013-08-03
> **gulmer said:**
> The CPU isn't getting sucked up when this happens. The meters are at 0, and I'm not sure on how to get into this computer from another. Not using compiz, this computer doesn't like compiz, so I'm using metacity.

If the GUI is locked up, the meters will not move, right?
To access 1 Linux PC from another, use ssh and ssh-server. There's a howto - [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
After you install the ssh-server, please install **fail2ban** too. It is a security thing.

If your other computer isn't Linux or OSX ... er that sort implies Windows - use Putty to connect. Login with your Ubuntu userid and password, then type "**top**" and watch the screen.

---

### Post by gulmer on 2013-08-07
Got ssh installed on remote computer and got folders and files loaded after top search. What am I looking for? also, the computer that has the freeze problem, decided to cooperate for the first time in weeks and not freeze up, while I was working on the remote computer, go figure.

---

### Post by TheFu on 2013-08-07
> **gulmer said:**
> Got ssh installed on remote computer and got folders and files loaded after top search. What am I looking for? also, the computer that has the freeze problem, decided to cooperate for the first time in weeks and not freeze up, while I was working on the remote computer, go figure.

When the problem computer freezes, go to the other commuter and remote in. Run the **top** tool to see what is eating all the CPU - that will tell you where the problem is.  I think it is strictly a GUI problem, so Compiz or GPU drivers are likely the issue.  Save all the logs from /var/log/* and review them for errors and warnings - specifically around hardware or crashes.

If I'm wrong and the entire OS is locked up, you won't be able to ssh in. then it is likely you have a hardware issue to resolve.

See, Linux isn't like Windows. When Windows locks up it is the entire OS. With Linux, it is almost always a GUI tool - which is why people like me and other admins don't run GUIs on servers.  We use only ssh for access to manage out Linux machines around the world.

It has been so long since this thread started - I don't actually remember the issue as I write this.

---

