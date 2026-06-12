---
title: "help with shell setting"
date: 2012-11-06
forum: General Help
---

### Post by lun115 on 2012-11-06
Hi people,

I just had a machine installed with ubuntu.  I prefer using c shell in the terminal, but the default one is bash.  Even the Admin changed the content of file /etc/passwd to /bin/csh, it still starts with bash.  Even I type csh command, it is still bash.  Can anybody help me with this?  

Thank you very much!

---

### Post by drmrgd on 2012-11-06
Have you verified that CSH is installed on that system?  Run to check:

```
cat /etc/shells
```

I don't believe CSH is installed by default, and you'd have to install it:

```
sudo apt-get install csh
```

Then, when you have it installed, you can set it to the default by running:

```
chsh -s /bin/csh
```

---

### Post by papibe on 2012-11-06
Hi lun115. Welcome to the forums ):P

csh is not installed by default, did you install it first?

Regards.

BTW, I was a 'intense' user of tcsh ... a long time ago.

---

### Post by lun115 on 2012-11-06
Hi guys, thank you for your replies.
I installed the csh, and can see it using "cat /etc/shells".
But I cannot change it even with "chsh -s /bin/csh".
:(

---

### Post by papibe on 2012-11-06
Try login out and login in again.

---

### Post by lun115 on 2012-11-06
Tried logout and then login.
It is still bash, although it shows csh when I use *echo*, weird.

---

### Post by papibe on 2012-11-06
what happens when you run it manually on the command line?
```
csh
```

---

### Post by lun115 on 2012-11-07
It shows nothing...
When I type "echo $shell", it shows "/bin/csh", but it is still bash.

---

### Post by drmrgd on 2012-11-07
Something seems off there.  Have you really fully logged out and back in after setting your default shell to csh?  You need to completely log out and restart a session or else you'll still be loading the old default shell.  

Also, why do you think (apart from the output of your query) that you're not in a csh shell?  Do you have the default '%' prompt, or are you still seeing your bash prompt?  

Please run the following (copy and paste into the terminal), and post the output here:

```
% echo $shell $SHELL
```

If you're running a csh session from a new login,  you should see:

```
/bin/csh /bin/csh
```

If you're just running a csh session on top of bash, you should see:
```
/bin/csh /bin/bash
```

And, if you're running bash alone, you should see:

```
/bin/bash           
```

---

### Post by lun115 on 2012-11-07
I just rebooted my computer, and it works now!
Thank you guys!
BTW, I cannot use the up arrow key to retrieve the previous commands, need any setting?

---

### Post by drmrgd on 2012-11-07
I don't know quite as much about csh in this regard (I'll be when papibe comes on line later he'll know more).  But, those settings are stored in either a system wide inputrc file located at /etc/inputrc or a local one that you define in /home/.inputrc (for example).  I'm not sure why csh won't read from the same file as bash did, but I did find this that may or may not be helpful:

[http://www.stat.umn.edu/macanova/htmlhelp/node358.htm](http://www.stat.umn.edu/macanova/htmlhelp/node358.htm)

---

### Post by papibe on 2012-11-07
AFAIK, csh does not have the arrows history functionality. It also lacks a lot of usability features.

The main reason for tcsh was to improve csh usability. tcsh has arrow history, tab completion, and other features. However, it remains backwards compatible with csh.

Just a thought.
Regards.

---

### Post by lun115 on 2012-11-07
Thank you guys for your replies.
Maybe I should use tcsh, since it works better.

---

