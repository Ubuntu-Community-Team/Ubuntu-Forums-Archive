---
title: "Configuring an SSH for PuTTY client"
date: 2014-09-04
forum: General Help
---

### Post by sam64 on 2014-09-04
I've already installed the SSH in my Ubuntu VM (in Virtual Box, with a Windows machine being the host that has PuTTY installed on it). Now I'm trying to configure the SSH in my Ubuntu VM using the instructions here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

But I'm still very new to using a terminal. What am I doing wrong here:
[ATTACH=CONFIG]256149[/ATTACH]

---

### Post by TheFu on 2014-09-04
For almost every normal use, there isn't any need to alter the default settings in the sshd_config file.  Basically, you install openssh-server, it is automatically started, and any client can connect - like putty.

OTOH, if you want to make it more secure then ... [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

BTW, can't read your image - my eyes don't work that well. copy/paste of text is helpful here and MB less bandwidth/storage.

---

### Post by papibe on 2014-09-04
Hi sam64.

One line at a time ;)

First this:
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults
```
press enter, then this:
```
sudo chmod a-w /etc/ssh/sshd_config.factory-defaults
```
Let us know how it goes.
Regards.

---

### Post by sam64 on 2014-09-04
Well, the terminal didn't appear to give any errors, but it didn't indicate that it did anything either:
[ATTACH=CONFIG]256151[/ATTACH]

---

### Post by TheFu on 2014-09-04
What did you want it to say?  Those commands don't do anything, really - just make a backup of a config file.

Seems like a beginning book on shell and common linux commands might be helpful?
A free PDF: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Spending 30 minutes skimming it will pay back 1000x.

---

### Post by papibe on 2014-09-04
> **sam64 said:**
> Well, the terminal didn't appear to give any errors, but it didn't indicate that it did anything either:
[ATTACH=CONFIG]256151[/ATTACH]
The Linux philosophy when it comes to error messages is 'no news, good news'. In other words, your commands executed successfully (for the most part that is the standard).

Let us know if you need more help with that.
Regards.

---

