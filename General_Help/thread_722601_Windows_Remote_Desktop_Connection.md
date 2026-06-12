---
title: "Windows Remote Desktop Connection"
date: 2008-03-12
forum: General Help
---

### Post by Old Marcus on 2008-03-12
Hi there, I hope this hasn't been asked before, I'm assuming it hasn't since my problem is fairly unique.

In Windows XP, there was a remote desktop connection client that you could connect to other computers with. I use this fairly frequently for connecting to my school's server to do school work on the system. I checked the Remote desktop in admin but it only allows you to open your computer up. I could download the windows version and run it through Wine, but I'm not sure if this will work... Has anybody tested it? 

What I'm asking is basically is there an equivalent version of this in Ubuntu?

---

### Post by Calmor on 2008-03-12
In Applications -> Internet is a Terminal Server Client.  It functions almost identically to Remote Desktop Connection Client.  Set the protocol to RDP and it should connect to any Windows machine - I use it to connect to Windows 2003 Server and Windows XP Professional boxes at home.

---

### Post by Old Marcus on 2008-03-12
Thanks a lot. I'm still fairly new to Linux in general. :)

---

### Post by Malikius on 2008-03-12
I am trying to setup the GNOME-RDP but am "stimied" here. Is there a step by step area and how do I log into the other computer this is also going to be setup with the GNOME-RDP? Is one a server and the other a client? I have tried NOMACHINE and it was to difficult to setup. What is the easiest to use and setup? 

Please help.

---

### Post by Old Marcus on 2008-03-12
Does anybody know if the terminal client only applies to Ubuntu/GNOME/Debian?

---

### Post by Calmor on 2008-03-12
> **Old Marcus said:**
> Does anybody know if the terminal client only applies to Ubuntu/GNOME/Debian?

krdc is in the repositories as a remote desktop client for the KDE-inclined.  I'm pretty much a noob as well, so I don't have any information about other distros.  I last dabbled in Gentoo a couple years ago (for a MythTV box) but I didn't play with it too much.

---

### Post by Calmor on 2008-03-12
> **Malikius said:**
> I am trying to setup the GNOME-RDP but am "stimied" here. Is there a step by step area and how do I log into the other computer this is also going to be setup with the GNOME-RDP? Is one a server and the other a client? I have tried NOMACHINE and it was to difficult to setup. What is the easiest to use and setup? 

Please help.

I'm not quite clear on what you're trying to set up - a remote desktop connection to a Windows machine or your own network of two Ubuntu machines?  I haven't personally done two Ubuntu systems (yet - coming soon), nor have I used GNOME-RDP, so I can't be of much help there. 

For Ubuntu-Ubuntu, try this HOWTO:
[http://ubuntuforums.org/showthread.php?t=122402]("http://ubuntuforums.org/showthread.php?t=122402")

That seems to give a step-by-step on setting your machine up to accept remote logins via VNC.  For Ubuntu-Windows, I've only had experience with the Terminal Server Client, but it's worked without flaw for me.

Good luck and let me know how it works out - I'll be trying it soon.

---

### Post by scottro on 2008-03-12
If I understand your question, you simply want an equivalent to the Windows remote desktop client.  
The other posters seem to be talking about remote desktop clients specific to a particular environment, e.g., Gnome and KDE, but there is a generic program called rdesktop.  I know it's in Fedora, so assume it's available in Ubuntu as well. 

To see if you have it just type in a terminal

which rdesktop

If you get an answer, you're good.  Otherwise, it should be
sudo apt-get install rdesktop

Then, you run it, if you were connecting to a Windows server at address 192.168.1.20 on your network, and wanted to connect as administrator, you would type

rdesktop -u administrator 192.168.1.20

I'm not familiar with either the Gnome or KDE rdesktops, but for what it's worth, this generic one seems to be as responsive as the Windows client.

---

### Post by WildeBeest on 2008-03-13
Maybe I should start another thread, but it seems appropriate here.

I have a problem with the Terminal Services Client. When I try to connect it fails with a Unable to resolve host error.

I can see the windows nodes with the File Browser.

I entered the fields as follows:

Computer:    Name of my windows machine.
Protocol:       RDP
User name:  login name
Password:    ********
Domain:        Blank - since I use a workgroup
Client Hostname:   Ubuntu machine name.


What am I missing here?

I can connect from the Windows machine through Samba.

---

### Post by Calmor on 2008-03-15
> **WildeBeest said:**
> Maybe I should start another thread, but it seems appropriate here.

I have a problem with the Terminal Services Client. When I try to connect it fails with a Unable to resolve host error.

I can see the windows nodes with the File Browser.

I entered the fields as follows:

Computer:    Name of my windows machine.
Protocol:       RDP
User name:  login name
Password:    ********
Domain:        Blank - since I use a workgroup
Client Hostname:   Ubuntu machine name.


What am I missing here?

I can connect from the Windows machine through Samba.

I think there could be one of two things going on:

[LIST]
[*]When I'm at home, I enter the IP of the computer I want to connect to.  I don't remember if this is because Windows required it, or if it was just something I did, but you might want to try that first.
[*]Your computer or user is not set up for remote access.  From what I remember, WinXP Home doesn't work - WinXP Pro, WIn2K, and Win2K3 Server do.  I have no experience with Vista, but the Business and Ultimate versions should work as well
[/LIST]

Unfortunately, my server is not up right now, so I can't test any settings out for you.  Google for enabling remote connections on your flavor of Windows if the IP trick doesn't work for you.

---

