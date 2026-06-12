---
title: "/etc/ssh/sshd_config &quot;AllowUsers&quot;"
date: 2018-11-30
forum: General Help
---

### Post by mglau72 on 2018-11-30
[COLOR=#000000]I apologize - i also submitted this post under specialist - Security.[/COLOR]
[COLOR=#000000]Who’s up for a good laugh? (I’m not laughing.. but you might)[/COLOR]
[COLOR=#000000]You’ll read this and think I’m a noob. Nope. Been doing this a while. However- I am really tired and was really tired when I made this idiotic mistake.[/COLOR]
[COLOR=#000000]I have a virtual Ubuntu Server running on VMWare. I use Putty to access the server. I’ve been working on this server for about 18 months. Never an issue. This is for a client. They are currently migrating to the Azure. They requested that I setup 2 servers so that they can be logged into, directly, as root. I currently have it setup to login as a regular user and then use sudo for root level commands. They said that the Azure migration can’t do that. [/COLOR]
[COLOR=#000000]These are the things I did;[/COLOR]


[LIST=1]
[*]Changed the password of root with; sudo passwd root. I tested it by running sudo –u and was prompted for the root password. I put in the newly created password and it worked. I then closed my putty session, opened a new one, and tried to login as root. “Access Denied.”
[/LIST]




[LIST=1]
[*]Started digging through the forums and found that one can go to /etc/ssh and edit the sshd_config file. Add PermitRootLogin yes - at the bottom of the file, then save, then restarted the ssh service. I closed my putty session, opened a new one “Access Denied.”
[/LIST]




[LIST=1]
[*]I started digging some more and came across a suggestion… To edit the sshd_config file and add AllowUsers root. I did this. The thought that zipped through my mind was “oh- this will allow root to login.” I didn’t know at that moment that it is actually a security method of just allowing the specified user access to login. I then closed the putty session, opened a new one. I tried to login as root and “Access Denied.” So, I decided to keep working on it and tried to login in as my normal user… Access Denied. Like a Wrecking ball, it hit me- what I had done- what “AllowUsers” really means.
[/LIST]


[COLOR=#000000]The Vsphere access is all messed up.I’m trying to gain access to it.I’m not sure if it will even allow me to login via console?It would be swell if they had a snapshot, but I doubt it.[/COLOR]

[COLOR=#000000]If I go to recovery mode >> choose root >> and then get to a shell prompt, will I again be denied access?Because if I could get to the command line, I could easily edit the SSHD_CONFIG file and everything would be good.[/COLOR]

[COLOR=#000000]Right now?The sky is falling.Any suggestions would be GREATLY appreciated.[/COLOR]

---

### Post by deadflowr on 2018-12-01
duplicate thread
closed

---

