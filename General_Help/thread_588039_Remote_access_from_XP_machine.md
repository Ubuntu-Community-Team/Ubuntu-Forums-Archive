---
title: "Remote access from XP machine?"
date: 2007-10-23
forum: General Help
---

### Post by the_nite_owl on 2007-10-23
I am looking to remote access my Feisty box from a Windows XP device.
I have VNC on the XP machine, what would I need to install/setup on Feisty?  Or is there a better Windows client to do this with?

Thanks.

---

### Post by Seisen on 2007-10-23
Check this 

[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

---

### Post by zaphod777 on 2007-10-23
you should be able to intall VNC from the Synaptic package manager. VNC is the native way to remote control in Linux.

---

### Post by the_nite_owl on 2007-10-23
> **Seisen said:**
> Check this 

[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

I will have to do some playing around with it.  It seems like from what I read that someone has to be at the console to allow the connection.

My Feisty box is a LAMP server with the Gnome desktop installed and I leave it logged in but screen saver engaged with password to unlock.
I want to be able to remote to the server to check/change things remotely, preferably without altering the local display as I do not want the kids to walk by and be able to access the machine.
Any experience with this?

The link above seems to suggest that it can be done but then refers to the security options as if there are only two and both require someone console side to initiate or approve the connection.

I realize now what I did wrong testing last night, I was using the internet address of my server rather than the local LAN address and I had not yet setup port forwarding on the router.  I had just finished replacing the firmware in my Linksys router with dd-wrt and did not get into the fine tuning details yet.  :)

Thanks for the info.  I am a relative noob but learning quick seeing as I have an x64 LAMP server running with web server and MySQL up and working.  I am just too ambitious with the things I want to do and the amount of reading every single thing requires to get it configured.

---

### Post by zaphod777 on 2007-10-23
I would check the settings I am sure there is a setting so that someone doesn't need to accept the connection. I know it is there in the windows version.

Have Fun!

---

### Post by the_nite_owl on 2007-10-23
> **zaphod777 said:**
> I would check the settings I am sure there is a setting so that someone doesn't need to accept the connection. I know it is there in the windows version.

Have Fun!

There is a remote access client already installed that I believe is compatible with VNC, I do not remember it's name offhand and do not have access to a Linux box at the moment to see.
I used VNC under windows many times and did not have the connection issues.  It is probably just something I have not found in the config yet.

---

### Post by Scroobytec on 2007-10-23
> **zaphod777 said:**
> I would check the settings I am sure there is a setting so that someone doesn't need to accept the connection. I know it is there in the windows version.

Have Fun!

There is - I think it is the Remote Desktop settings:

System > Preferences > Remote Desktop 

Ask you for confirmation (ie; someone at the machine must click OK to grant remote access. This will be a problem if you plan on accessing your home machine from work or visa versa, as no one may be there to grant you access.)

---

### Post by NIT006.5 on 2007-10-23
I'm a little confused here. From what I know there should be no extra installation (of VNC or anything) necessary on the Feisty box. You would just need to enable remote connections.

System -> Preferences -> Remote Desktop (or vino-preferences from terminal). This also gives you the option of whether or not someone must "allow" the connection first. For all my users, I have just set a password but no confirmation necessary i.e. when I try to connect I just enter the password and I'm in, whether there's anyone on the other machine or not. 

Granted I'm connecting from Ubuntu to Ubuntu, but that's using the vnc protocol so provided vnc viewer is installed on the XP machine, there should be no difference. So it really should be that simple to the best of my knowledge. Unless I've missed something somewhere?

---

### Post by cacodaemon on 2007-10-23
> **NIT006.5 said:**
> I'm a little confused here. From what I know there should be no extra installation (of VNC or anything) necessary on the Feisty box. You would just need to enable remote connections.

System -> Preferences -> Remote Desktop (or vino-preferences from terminal). This also gives you the option of whether or not someone must "allow" the connection first. For all my users, I have just set a password but no confirmation necessary i.e. when I try to connect I just enter the password and I'm in, whether there's anyone on the other machine or not. 

Granted I'm connecting from Ubuntu to Ubuntu, but that's using the vnc protocol so provided vnc viewer is installed on the XP machine, there should be no difference. So it really should be that simple to the best of my knowledge. Unless I've missed something somewhere?


You are correct.  All a Windoze user would need is a VNC Client Viewer.  I use it this way all the time when connection from Windoze to Ubunto.  It works great.

---

### Post by jscout on 2007-10-24
Tried this and it works fine, but what if I restart Ubuntu from XP? Connection is lost (of course) but I can't reconnect when Ubuntu is up again. 
Using Windws server, I would set VNC server as a service and then I can connect to the server before logon (ie the VNC client shows the server login)
How do I make this work in Ubuntu?

---

### Post by P4man on 2007-10-24
Id like to know too. I'm a Linux noob myself, but if you go into menu
system / management / login manager 
(could be named differently, got it in ducth here)

Click on the tab "remote", and enable it. Im not quite sure it will enable logging in from VNC, but its worth trying. Let me know, I can't test here for the moment.

---

### Post by njparton on 2007-10-25
I'm about to set up a headless NAS based on ubuntu at home at the weekend and I to would like to know how to ensure that I can login remotely (from Vista via UltraVNC) following an ubuntu reboot.

Is there a line that needs to be added to an init.d script somewhere?

---

### Post by njparton on 2007-10-28
Well I've installed Xming under Vista and I can access my ubuntu PC (gutsy 64) via XCMDP - really easy to set up (Administration > login Window) and I don't have to be logged into ubuntu to do it and no messing with VNC.

Just forward UDP port 177 and TCP port 6000 to your ubuntu PC in your router :)

---

