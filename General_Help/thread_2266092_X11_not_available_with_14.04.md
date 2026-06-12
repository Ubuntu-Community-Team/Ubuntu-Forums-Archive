---
title: "X11 not available with 14.04"
date: 2015-02-19
forum: General Help
---

### Post by Deb_T. on 2015-02-19
Hi Everyone,

I recently upgraded our two servers to ubuntu 14.04 and have not been able to open an X window on either machine logging in with either -X or -Y (Error: can't open display). I've tried the fixes that I've found in this forum and on other online resources (e.g., restarting lightdm; reinstalling server-xorg) but nothing will remedy the problem. I don't have a xorg.conf file in /etc/X11/ but read that it is no longer required with this version of ubuntu. I was wondering (and hoping) you might have some helpful suggestions. Thank you!

Sincerely,
Deb

---

### Post by TheFu on 2015-02-20
Just to clarify - you are remote from the servers and want to open a shell that is capable of running X/Windows apps with the display shipped back to your X/Windows server-running-local-PC?

Something like:```

ssh -X romulus /usr/bin/xterm  -sb
```
doesn't work, but 
```
ssh romulus 
```
does?

---

### Post by Deb_T. on 2015-03-03
Thanks for your reply. I just saw it now or I would have posted this sooner. As to your question, I am remote from the server and want to open a shell capable of running an x-window (I am working locally on a Mac). My ssh command does not work with either -X or -Y...for example ssh -X [email]romulus@server.ip[/email] does not enable me to open an x-term after I am logged on.   I am able to connect but not run any x-apps. I have not tried a code similar to your first example.  Thanks!

---

### Post by tgalati4 on 2015-03-03
Try performing some updates on the servers to make sure they are up to date:

```
sudo apt-get update
sudo apt-get upgrade
```

Reboot and try again with your remote ssh.

Look in your log files on the mac (probably /var/log/auth.log) to see what is failing.

---

### Post by TheFu on 2015-03-04
> **Deb_T. said:**
> Thanks for your reply. I just saw it now or I would have posted this sooner. As to your question, I am remote from the server and want to open a shell capable of running an x-window (I am working locally on a Mac). My ssh command does not work with either -X or -Y...for example ssh -X [email]romulus@server.ip[/email] does not enable me to open an x-term after I am logged on.   I am able to connect but not run any x-apps. I have not tried a code similar to your first example.  Thanks!

"romulus" is the remote server name for me. I assume you are using it as the userid?

The remote server  needs to allow X-forwarding. That is set in the /etc/ssh/sshd_config file.  Just change that setting to "yes".  Of course, the OSX machine will need to be running an X/Server. Is that enabled by default on a Mac?

---

### Post by Deb_T. on 2015-03-06
Thanks to you both for your replies. I've tried updating the server followed by a reboot, which did not work. 

Yes, I just used your romulus example to illustrate my login scheme (guess it didn't go over well). My ssh_config file allows X11 forwarding for trusted (ForwardX11Trusted yes) but is set to no for ForwardX11. I thought it was not wise to set the general X11 forwarding to yes for security reasons. Is that what you are recommending?  Yes, I have the Server running by default on my Mac. Thank you for your help!

---

### Post by TheFu on 2015-03-06
There are two config files - ssh_config and sshd_config. sshd_config is for the openssh server processes on the machine. It needs to allow X11Fowarding or it will not work.  The client side ... can be over-ruled in your personal ~/.ssh/config file with anything you like. The settings are fully documented in the manpage for each file. Some important caveats for X11Forward are in the manpage too.  Of course, this should only be used on the same LAN. Over a WAN connection, X11 is too slow.

---

### Post by Deb_T. on 2015-03-06
Thanks for your explanations. The X11 Forwarding is set to yes in my sshd_config file but it is still not working. We have a long analysis running on the machine now but I can try a reboot when it's finished.

---

### Post by TheFu on 2015-03-06
No need to reboot - just restart sshd for force the config file to be reread. This is on the ssh-server side.
```

sudo /etc/init.d/ssh restart
```

---

### Post by Deb_T. on 2015-03-06
Thanks. I tried that before and just tried it again but it still can't open display.  !!!!

---

### Post by tgalati4 on 2015-03-06
What was in the log files?

---

### Post by TheFu on 2015-03-07
> **Deb_T. said:**
> Thanks. I tried that before and just tried it again but it still can't open display.  !!!!

X on Linux sorta "just works" - do you know for certain that the X/Server on your Mac is really working? 
I wrote an article years ago about running remote programs ... 
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) 
Perhaps something will "click" with that?
Also, as tgalati4 asks - what is in the log files on both the X-client (remote server) and the X-server (local Mac)? I don't know anything about Macs and X/Windows ... I'd check all the logs for error and warning using egrep -i

---

### Post by tgalati4 on 2015-03-07
The logs on the Mac are generally in the same location.  It depends on what X-server is running, there are a few to choose from.  Is it a DISPLAY environment variable error, is it an authentication error, is it a garbled X command that can't be rendered?  The log files will generally capture this.

---

