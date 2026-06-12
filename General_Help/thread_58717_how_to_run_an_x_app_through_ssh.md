---
title: "how to run an x app through ssh"
date: 2005-08-21
forum: General Help
---

### Post by nbx909 on 2005-08-21
I have ubuntu on my server as well as my desktop, how can i run gedit for example via ssh?

---

### Post by adwait on 2005-08-21
You could pass commandline parameters to gedit, with
```
ssh your ip -x 
```
But I doubt if there is anyway in SSH to actually start that application on your computer, remotely. You can use the Remote Desktop Tool for that...

---

### Post by macgyver2 on 2005-08-21
[QUOTE=nbx909]I have ubuntu on my server as well as my desktop, how can i run gedit for example via ssh?[/QUOTE]
Okay, for all of the below stuff, I'm assuming that you're using the commandline.

First, on the *server*, do you have the package [font=Courier New]openssh-server[/font] installed?

If you don't
```
sudo apt-get install openssh-server
```
The install should start the ssh daemon automatically. You can check if it's running (either after you installed or if you had it installed already) with
```
ps -A | grep sshd
```
If you see a line with [font=Courier New]sshd[/font] returned, then it's running.  If nothing is returned, then it's not running.

If it is running, skip the rest of this paragraph.  If it's not running, type
```
sudo /etc/init.d/ssh start
```

Next, check [font=Courier New]/etc/ssh/sshd_config[/font] to see if [font=Courier New]X11Forwarding[/font] is set to [font=Courier New]yes[/font] and that the line isn't commented out with
```
grep X11Forwarding /etc/ssh/sshd_config
```
It should show
```
X11Forwarding yes
```
I think that's the default setting, but if it's not, go into [font=Courier New]/etc/ssh/sshd_config[/font] and change the [font=Courier New]no[/font] to a [font=Courier New]yes[/font] and/or remove the [font=Courier New]#[/font] at the beginning of the line.

If it was set to [font=Courier New]yes[/font] and not commented out originally, skip the rest of this paragraph. If it was set to no and you had to change it to yes or you had to uncomment the line, you'll now have to restart the ssh daemon with
```
sudo /etc/init.d/ssh restart
```

After that the server should be set up.

Now, on the *client*, all you need to do when logging into the server is add the [font=Courier New]-X[/font] flag to what you normally type to ssh in. Try gedit (or whatever other graphical program you want) and it should work. Hopefully I didn't miss anything.

---

