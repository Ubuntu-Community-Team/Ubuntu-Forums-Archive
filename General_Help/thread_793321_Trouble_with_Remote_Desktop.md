---
title: "Trouble with Remote Desktop"
date: 2008-05-13
forum: General Help
---

### Post by Bennett2005 on 2008-05-13
Well, 'trouble' might not be the right word...probably more along the lines of 'complete and utter ignorance.'

I'm trying to get a remote connection established with my parents computer.  I recently set up Ubuntu on their machine hoping to get them set up and comfortable with the OS.  Part of my plan was to be able to connect to their PC from home so I could continuously help them with any trouble.

I followed a guide I found a few weeks ago, but I'm not sure if it's still valid for Hardy, or if there are other guides out there that might be better to follow.  Here's what I tried:  [VNC- Community Ubuntu Documentation]("https://help.ubuntu.com/community/VNC")

I'd like to do this using the default systems in Hardy Heron.  My attempts so far come back with a "Connection Timed Out" error message.

Anyone have any thoughts?  I'm going to be contacting Linksys directly this afternoon to walk through port forwarding, etc., but I'm wondering about my settings in Ubuntu as well.

Thanks everyone :)

---

### Post by jimv on 2008-05-13
Did you forward the correct port on their router if they have one?

---

### Post by HermanAB on 2008-05-13
Well, the right way to remote into Linux machines is with SSH.  VNC is a very clumsy system and it is insecure - best avoided.

All Unix distributions, except Ubuntu, install SSH by default.  Unfortunately Canonical insists on making it difficult, so you got to install OpenSSH using Synaptic, run the daemon sshd and then you need to forward port 22 in your router to the target machine.

Hope that helps.

Cheers,

Herman

---

### Post by Bennett2005 on 2008-05-13
Thanks guys.

I'm fairly sure I have the right port forwarding set up on their server.  But that's something I'm going to have to look up with Linksys, and I plan on calling their support line tomorrow to double check my work.

I'll try installing the SSH option as well, although it might be difficult to have my folks do the same on their end.  It would be cool if I could get a vnc connection established first, then I could probably set it up myself.

Thanks for the suggestions, I'll mess with this tomorrow.  Any other ideas as to what else I might be missing?  Does Hardy Heron have a firewall set up by default that I need to deal with?

---

### Post by heatpumpcontrol on 2008-05-13
Try this [[COLOR="Red"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=383053&highlight=terminal+sever+will").... It works great. I've used it twice in the last month.

---

### Post by deathkillspt on 2008-05-13
Usually on most modern modems you have to do what is called setting your NAT rules or NAT forwarding - this is like forwarding the outside internet to your router then the router forwards it to your computer(s), just do a google search for NAT rules or NAT forwarding etc. That should get you up on your way, this is what troubled me for a long time.

---

### Post by fragos on 2008-05-15
Prior to 8.04 all you had to do for a LAN connection was set up Remote Desktop Preferences on both ends. To connect you ran "vncviewer {IP address}". That program isn't installed in 8.04. I found the xtightvncviewer package and installed it. The command is now "xtightvncviewer {IP}". quite a mouthfull so I made an alias to "vnc".

---

### Post by Paragtim on 2008-05-19
Jumping In

I have followed the advice of Fragos - many thanks
The viewer connect fine but there is no GUI - only a grey desktop and a terminal window.  How do I get the gui to display in the remote window?

Thanks in advance

---

### Post by fragos on 2008-05-19
In my experience when the screen comes up blank and dark the host is sleeping. When I move the cursor into the window I get an indication that cursor is moving and the other system wakes up and I see the GUI image. In the upper right of the VNC window I see an icon indicating remote access.

---

