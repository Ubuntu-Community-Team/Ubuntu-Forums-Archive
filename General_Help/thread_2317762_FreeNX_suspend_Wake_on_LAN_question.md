---
title: "FreeNX suspend Wake on LAN question"
date: 2016-03-19
forum: General Help
---

### Post by transporter_ii on 2016-03-19
I swapped a server in my closet from Windows 7 Pro to Ubuntu. On windows, I used remote desktop to get on this server. I would put it to sleep and then use WOL (wake on LAN) to bring the server back up. With FreeNX, when I suspend the server, it hangs the NX client up for waaaayyyyy too long and I'm forced to just sit and look at a frozen screen I can't get out of. Does anyone know of a better to solution for this problem? A command to force close FreeNX? A way to just force minimize the NX client? A remote, easy way to suspend the server? I've searched and can't find anything.

I know I can SSH into the server and suspend it from the command line, but it seems rather much to log out of the NX session, fire up SSH, log in and suspend the server. There has got to be a more elegant solution. I have even thought of scripting an SSH command, but nothing has just jumped out at me as The Way to go here.

It seems people have gone to a lot of trouble to make WOL work. I find it hard to believe that Sleep On LAN was never contemplated. Yeah, I understand putting other people's computer to sleep, haha, but a person would think someone would have written a snazzy client server gui that automates remote commands like this.

As a user of Mikrotik Routerboards, something scriptable similar to the gui Winbox, that would let you execute commands on a remote server would be neat. Does anyone know of anything like this?

---

### Post by transporter_ii on 2016-03-19
Well, I did finally find something close to what I was looking for, that sorta kinda runs on Linux. Anrdoid SSH Buttons. Too bad nobody has done a non-android version of something like this that I can find:

[IMG]https://lh4.ggpht.com/lOOFxfEIC0nq4AOO9TDZQu71arjLpxnKrCrBZWq28V1vOf_voV94v7p2mupNjY0yN-I=h900[/IMG]

---

### Post by transporter_ii on 2016-03-27
I finally got around to fully testing SSH Button. It does work and does what I need it to do. However, I can't find a way to get it to respond to the password request when you issue a sudo command, and that seems to be required to suspend a Linux box from SSH. I will post my work around for it. I had to edit a file to make it not request a password to issue the command "pm-suspend". Here is what I had to do:

-=-=-=-

Open up a terminal and exebute sudo visudo.

Then you can edit the sudoers file where you can specify who can execute which command as root with and without password. At the end of the file you paste either this line

nonprivilegeduser ALL=NOPASSWD:/usr/sbin/pm-suspend-hybrid

for every user to be able to execute that command as root without password, or

Your_Username ALL=NOPASSWD:/usr/sbin/pm-suspend-hybrid

for only your user to be able to do this (of course you have to adjust it for your user). Then you save the file (should be Ctrl+O) and exit the program (Ctrl+X).

At last, you have to edit your command to read sudo pm-suspend-hybrid instead of gksudo pm-suspend-hybrid.

NOTE: There should also be the possibility to do this with dbus (doesn't require sudoers editing) but this solution has the advantage that it works with every UI.

-=-=-=-

After it didn't require a sudo password, SSH Button suspends the system with the click of button, just as advertised. I have a script file on my main box to wake the server with a magic packet. I don't like having to find my phone to do this, but it is way better than it locking up FreeNX on me for two minutes while my screen is frozen.

---

