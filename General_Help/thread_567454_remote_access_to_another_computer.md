---
title: "remote access to another computer"
date: 2007-10-04
forum: General Help
---

### Post by leegwebb on 2007-10-04
Hi.

I recently gave an older computer with Ubuntu Feisty to my in-laws, who live in another town.  They are now set up on the internet, but are basically computer-illiterate.  I am looking for a how to on setting up their computer so I can access it from my home to install new things for them and troubleshoot anything that might come up on weekdays when I don't have time to visit them.  There are a couple of posts in the networking section on openvpn and ssh, but they assume a lot of knowledge I don't have.  I am pretty comfortable with the basics but am no pro.  For example, I have no idea how to open a port.  

Can anyone suggest something that is easy to set up and secure?  Basically, I just need to be able to log on and control their computer from my own computer, securely, without leaving it vulnerable to anyone else.

Thanks for any help!

Lee Webb

---

### Post by cmnorton on 2007-10-04
The remote system should be running sshd. I believe Ubuntu installs it by default.

Make sure the remote system's firewall is running, and make sure that ssh could log in. You can probably restrict from which hosts ssh logins would be allowed.

You can use ssh (from your own system) just like the telnet command and enter the remote's IP address. From there you could issue cli update commands.

---

### Post by bodhi.zazen on 2007-10-04
You can look at this how-to :

[http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)

To increase security , learn to forward ports (read the documentation with your router).

Then install the openssh server, change the default port, install firestarter, and ssh in.

If you want a full desktop, forward vnc over ssh :

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

Firestarter : [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

