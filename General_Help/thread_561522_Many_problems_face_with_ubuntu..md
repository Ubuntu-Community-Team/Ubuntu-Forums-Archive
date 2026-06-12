---
title: "Many problems face with ubuntu."
date: 2007-09-27
forum: General Help
---

### Post by grungy on 2007-09-27
Hi folks,

First, i cant give you all my system details because i cant run "hardware information from the system/adminstrator. I can t  even run a lot of things. I think that when i am on my desktop (friendly mode), i have no privileges in most of the applications i wanna start. So i have to go on console then su root, and pray god to find the application i wanna lauch in the black box (console). So how can i fix this problem and eventually get root privileges without switching to console.


I installed ubuntu like 2 days ago. Everything was going smooth until i started installing packages that other packages needed, that were in turn needed by others etc..

Now, my problems are:

My wireless card is not recognized anymore. (This happened when i was testing my private security network with airecrack and airodump etc. I also installed ieee80211-1.2.18 that created me problems when i wanted to install my ipw3945-1.2.2.tgz).

I couldn't finish to install avg, cause i failed to install the prerequisites like pygtk-2.10.6.tar.gz due to pygoocanavas related problems.

I installed firestarter as a firewall, but it cant launch on startup because it needs root privileges. So every time i run my laptop i have to go on console and su root then start it up, however if i close the console afterwards the firewall shuts down too.

I have the same problem with checkgmail, but i fixed it. Now i have another problem. When i receive a new email, and i go on the checkgmai tray, a quarter yellow page shows up and stick on the desktop. Checkgmail freezes and i can t remove the yellow page that is showing the new emails i received over my desktop.


I feel like my system is not stable to summarize, is there any problem checker on ubuntu like windows (sorry for the word :P).


i really wanna switch to Linux, but i have many problems here in just 2 days !! It s kind of pissing off, but i am ready to struggle because i think its worth it.




Finally, thank you for your support. I am waiting for you suggestions. 
You can ask me question ill answer as soon as possible!

---

### Post by Buffalo Soldier on 2007-09-27
Whenever you want to run an "admin" level program, it will ask you for a password. You should be seeing a window something like the one I attached here.

What you need to enter/type is YOUR password. The password that you entered during installation, the same password that you used at the login screen.

---

### Post by cmnorton on 2007-09-27
If you installed the system, it asked for the Administrator account. You entered a name and a password. You can run hardware information from the system/adminstrator and other things like Synaptic Package Manager by giving the Administrator's password when prompted to do so.

If you are running priviledged programs from the CLI, then preface the command with sudo <space>, and give the administrator's password when prompted to do so.

If you did not install the system, then find out who did, and get the username and password, or ask the Administrator to add your login to the sudo proxy.

---

### Post by lisati on 2007-09-27
If you're running stuff in the terminal that asks for your password, don't worry if your password doesn't show on the screen - this is normal, and your password will still be recognized.

---

### Post by grungy on 2007-09-27
> **Buffalo Soldier said:**
> Whenever you want to run an "admin" level program, it will ask you for a password. You should be seeing a window something like the one I attached here.

What you need to enter/type is YOUR password. The password that you entered during installation, the same password that you used at the login screen.

thankls for the reply.

What about firestarter that doesnt run on startup (it need root priv.)

---

### Post by Buffalo Soldier on 2007-09-27
Firewall in Linux is not 100% exactly like in MS Windows (as with everything else). In the case of firewall, it is not an "add-on" software. You could say the concept of firewall is already built-in into the Linux OS.

- [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
- [http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
- [http://www.netfilter.org/projects/iptables/index.html](http://www.netfilter.org/projects/iptables/index.html)

If I'm not mistaken, Firestarter is just a GUI frontend for **iptables**. It is mainly used to (a) help you configure iptables and (b) visible indication as to what is entering which port.

You don't need it to load during start-up to have firewall running, as iptables is already running in the background. But if you still want to go down that road, here's a guide -> [http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

Somewhere in the middle of it is an explaination on how to get it running at start-up. It requires you to edit the sudoer list. Basically a file with the list of users who have the privilage to run as admin. I would suggest you get comfortable with the rest of the OS before going into something deep like this.

---

### Post by grungy on 2007-09-28
bump

---

### Post by Buffalo Soldier on 2007-09-28
> **grungy said:**
> bump

Have you tried the link that I gave? [http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

---

