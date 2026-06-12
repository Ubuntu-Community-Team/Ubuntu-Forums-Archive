---
title: "&quot;Login Screen Setup&quot; &amp; XDMCP - locked out of computer"
date: 2008-02-21
forum: General Help
---

### Post by none-letmebe on 2008-02-21
Hi, 

I have locked myself out of my Ubuntu 7.10 installation :(

How did I do this you ask?

I configured the login manager to start with a window that allows one to enter an XDMCP host on the network.  (I did not mean to do this).  There are no other option available to perform a local login.

When the manager starts I enter the host of my computer but the connection is refused because XDMCP connections are disallowed, which means I cannot login.

I booted into single user, logged in as root, and did a startx.  Gnome came up, but the programme under Administration menu called  &#8220;Login Screen Setup&#8221;   is not there so I cannot change it under the root login.
 I tried to run gdmsetup as root from the command line, but it would not start.  (I think it might have been called "Login Screen" instead.  

In single user mode I su ed to my user login and tried to startx but it died because a windows manager was already running (as root because I am in single user mode) so I could not access the "Login Screen Setup" option as my user account.

Question: 
Is there a way to lauch the "Login Screen Setup" from the command line as root?
Where is the configuration file that i) allows XDMCP connections, and ii) where is the configuration file that is written by the  "Login Screen Setup"?

I would apprieciate a reply because I had a deranged wife screaming at me this morning because I have broken the computer.

Regards.

---

### Post by SpaceTeddy on 2008-02-21
> **none-letmebe said:**
> 
Question: 
Is there a way to lauch the "Login Screen Setup" from the command line as root?

i have never started the xserver as root, as it is not good not suggested, but i suspect that you can do this... but then running gdmsetup would have been my choice aswell...
what you might want to do is (temporarily) all all connections to you host by typing "xhost +" which allows any connection from anywhere to your xserver. Of course, this is a huge security risk, but i have a hunch that that is the least of your concerns right now :)

> **none-letmebe said:**
> 
Where is the configuration file that i) allows XDMCP connections, and 
ii) where is the configuration file that is written by the  "Login Screen Setup"?

gdm is configured in /etc/gdm/gdm.conf. But since i have never really worked with that file, i cannot tell you what to do, exactly...but a quick google search show [this]("http://ubuntuforums.org/archive/index.php/t-381418.html") article that ought to help you enable remote logins. Looks pretty good to me

> **none-letmebe said:**
> 
I would apprieciate a reply because I had a deranged wife screaming at me this morning because I have broken the computer.
Regards.
my condolences :)

---

### Post by none-letmebe on 2008-02-21
> **SpaceTeddy said:**
>  all all connections to you host by typing "xhost +" which allows any connection from anywhere to your xserver.
my condolences :)

Impossible to do this because one cannot login to the machine except as root in single user mode because of the reasons detailed in the original post.


gdm is configured in /etc/gdm/gdm.conf. But since i have never really worked with that file, i cannot tell you what to do, exactly...but a quick google search show [this]("http://ubuntuforums.org/archive/index.php/t-381418.html") article that ought to help you enable remote logins. Looks pretty good to me
[/QUOTE]
Thank-you for the link. I think this bit might help:

 /etc/gdm/gdm.conf: 
Also, under the XDMCP section, change
Enable=false
to
Enable=true

Any other suggestions from peeps out there?  (no intention of knocking SpaceTeddy's answer.  The link is useful).

---

### Post by none-letmebe on 2008-02-21
I have managed to get dhcp working in single user mode so that I can post this message.
The above suggestions all failed. 

gdmconfig does not exist on Ubuntu and nor can I find it in apt-get install gdmconfig so thats screwed.

I started Gnome (startx) from single user mode and tried to run gdm-setup but it told me: 
GDM (Gnome Display Manager) is not running!!!!! ????

I tried to run /usr/bin/network-admin and it said:
Configuration could not be loaded. You are not allowed to access the system configuration.!!??!?  I am running as root.  Is the s/w incapable of checking which uid is running the process. Some error messages from this :
# network-admin 
(network-admin:14425): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
(network-admin:14425): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
(network-admin:14425): Liboobs-WARNING **: could send message, OobsSession hasn't connected to the bus
(network-admin:14425): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
(network-admin:14425): Liboobs-WARNING **: could send message, OobsSession hasn't connected to the bus
(network-admin:14425): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed



I uncommented the entry in  /etc/gdm/gdm.conf in the [xdmcp] section
Enable=false
to
Enable=true
This let me select this host, but tring to connect to it restarted Gnome and took me back to the original XDMCP chooser window.

All the normal user accounts desktop have a programme that I mentioned before called "Login Screen Setup" in  the Administration menu.  Why is it not listed on the root menu?  If I could find this programme I could undo this mess because this the menu I used to screw it up in the first place with.  I have searched through the user directories (find /home/ -exec grep Login {} ; ) and have found nothing.  Is there a place where the user Gnome menus are stored? Does anybody know how to launch this programme?

Alternativly, is there anyway to completly remove GDM and Gnome and start again?  I don't want to reinstall Ubuntu because it took me four days last time (including backing up and restoring the disc data).

My wife is now refusing to talk to me over this, which is better because its better than earlier when she was shouting at me. I am very tired.

---

### Post by SpaceTeddy on 2008-02-21
well, as a last resort, you could always try to remove the gdm package along with the xserver (purge it via aptitude) and reinstall them.. but that will have pretty much the same effect as a reinstall, if not worse. i would not recommend that.

what i don't get tho, if you can run a "startx" in single user mode, have you tried (after the xserver is loaded) to load the gdm and then run the gdm setup (just guessing here) ? i suppose you know that you can start gdm via /etc/init.d/gdm start.

i really don't know if that works, but it might help... a little. 
And no one else seems to be willing to contribute anything to this thread...:(

---

### Post by none-letmebe on 2008-02-21
I tried to run gdmsetup after runnning startx but gave the error message "GDM (Gnome Display Manager) is not running."

I have managed to get gnome running in multiuser by:
Cntl-Alt-1 to get to the console login window. 
Then I listed all gdm and X processes and killed all of these at the same time (including X and X11 and gdm).
Then I logged out as root, and logged in as a normal user. 
Then I ran startx as the normal user and got Gnome runnung.

However, the menu item in the Admin menu is not there :(  Its disappeared!  (the "Login Screen Setup" that it)
I ran gdmsetup in this mode and still got the same message as above.

---

### Post by none-letmebe on 2008-02-21
I tried a dpkg-reconfigure gdm and it made no difference. 

 I still think the missing key here is the missing System -> Administraition -> Login Screen  menu.  

I don't understand why this has disappeared.

---

### Post by none-letmebe on 2008-02-21
I managed to run gdmsetup by rebooting and then killing all instances of X X11 gdm. 
Then either ( i have forgotten) ran /usr/sbin/gdm && startx or in reverse.

However, although I ran the gdmsetup menu, I could not see anything to stop the gdm XDMP chooser window instead the original Gnome user login window (I do not know its real name).

---

### Post by SpaceTeddy on 2008-02-21
really sorry, but i am now all out of ideas... really... if nobody else has something smart to say, then i fear there is no help here left.... truely sorry... i really am

and i hate surrendering :(

---

### Post by none-letmebe on 2008-02-22
Well, no one has added to this thread so I think I will have to either reinstall Ubuntu or revert to WinXp and if I do the former then I shall never change anything on Ubuntu again.  It makes Solaris seem really really easy!  (Long live CDE - basic but understandable :D  )  

On a final note, I ran a dpkg-reconfigure gdm && reboot , but this made no difference and the XDMCP greeter was still displayed instead of the normal login screen.

---

### Post by none-letmebe on 2008-02-22
What should the Chooser path be set to in gdm.conf?
In the documentation it is set as: Chooser=bin/gdmchooser --disable-sound
Does this setting have any bearing on which screen is displayed on the pc after GDM has started. (Currently, it shows the gdm xdcmp screen only)

---

### Post by none-letmebe on 2008-02-22
**Problem solved.**

After killing all instances of gdm and X except the PPID of the gdm and logged in as normal user I started x [startx].
Then opened xterm and started gdmsetup [sudo gdmsetup]
**Select this tab: Security -> Configure Xserver (at the bottom of the menu) -> Click on on the Launch button and change *chooser* to *greeter.***
Logout and restart gdm [/etc/init.d/gdm restart]

Phew!

---

### Post by marcvilleneuve on 2008-02-25
Hi

I'm new in ubuntu world, and while testing a few things, I went into troubles, among which the exact same problem as yours.

But I could find out a way to fix it.

If it is not too late for you, you could try it , it worked for me!

In file /etc/gdm/gdm.conf-custom, find this section
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 
#MVchooser=true
#MVhandled=true
flexible=true
#MVpriority=0

and comment out the lines chooser=true, handled=true and priority=0

Restart ubuntu and select the normal way to start it.

Good luck!

---

### Post by geezerone on 2008-04-02
> **marcvilleneuve said:**
> If it is not too late for you, you could try it , it worked for me!

In file /etc/gdm/gdm.conf-custom, find this section
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 
#MVchooser=true
#MVhandled=true
flexible=true
#MVpriority=0

and comment out the lines chooser=true, handled=true and priority=0

Restart ubuntu and select the normal way to start it.

Good luck!

marcvilleneuve - what a scholar and a gent! :guitar:

Thanks for taking the time to post. I *think* this deserves a note in my siggy for a while at least :)

---

