---
title: "odd ssh connection errors"
date: 2007-01-26
forum: General Help
---

### Post by GrayMagiker on 2007-01-26
My ssh sessions die on me after a few minutes of being connected to a newly set up server on the lan.  

I am using putty to connect from a windows XP machine from in the same office.  I installed ssh with the following command

```
sudo apt-get install ssh
```

It worked fine for a few days, and now I will get disconnected every several minutes or so.  I get disconnected while in the middle of working (so it is not a time out issue).  Additionally I have set the "Seconds between keepalives" to 60 in putty.  

Putty gives the following error:
> Network error: Software caused connection abort

Additionally, sometimes I cannot connect at all with putty, receiving:
> Network error: Connection Timed out

I do not beleive the problem is strictly related to putty, as I can connect to the server at my school from the same windows machine fine.  

However if I try and reconnect a minute or two latter I can connect, but get disconnected as above right in the middle of what I was doing. 

where are the logs for the ssh server?

What could be causing this problem?


**Edit 0845 MST to add updates and sshd_config file**

Ok, I attached my sshd_config file.  I have confirmed the issue is not with putty, as I experience the same difficulty getting a connection (though I do eventually) and disconection shortly after while using Cygwin from the windows machine.

---

### Post by HumanAnarchist on 2007-01-26
This is not a solution to your problem, but it's a nice habbit/workaround

You should use the program 'screen' when you're working in the consol. Screen is like a window manager for you consol and all you programs live inside of the screen. If your session is disconnected, you can reconnect and resume from where you left with the command 'screen -r' 

This is a nice tutorial to get you started:
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

-ha-

---

### Post by bernied on 2007-01-26
/var/log/auth.log
/var/log/messages might also be worth a look

Are you sure there's nothing in between the two machines (like a router) that is objecting to the traffic and closing the port?
What happens when you ssh localhost from the server machine?

---

### Post by bernied on 2007-01-26
I would also suggest that you change this line:
```
PermitRootLogin yes
```to, no unless you have good reasons not to. You can su to a root login after you've done a normal user login.

---

### Post by wraithe on 2007-01-26
apt-get install ssh openssh-server

Install that, then try putty again...
thats the only install i use, have more trouble when forget to set the right ip address...
i use both ssh from terminal and putty from windoze, usually am connected for up to 10 to 12 hours non stop...for added security, look at using a rsa passkey...

and check the attached config file, it is what i start with till everything is stable and working...

---

### Post by GrayMagiker on 2007-01-26
>  apt-get install openssh-server
is the same as
> apt-get install ssh

I verified this by running The first command as you sugested, apt-get reported that openssh-server was already at the current version, and: 0 packages were installed, 0 packages upgraded, and 1 package not upgraded.  

So it must already be installed, even though i didn't instal it.

I then did 
> apt-get remove ssh

following that

> apt-get remove openssh-server

results in the apt-get message
> openssh-server not installed, so not removed

then verified there was no ssh server running by
```

$ ssh localhost
connection to local host reffused, port 22
$

```

Thus no ssh server was installed at that point.  

I conclude that, to apt-get, "openssh-server" == "ssh"

The log file is like that, because I started with a fresh install when I began having problems and wanted to change as little as possible until it worked.  

I do not see the need for rsa key based logons right now, as this machine is not visible outside the lan; I only connect to it from a windows machine based on the lan.


> Are you sure there's nothing in between the two machines (like a router) that is objecting to the traffic and closing the port?

We are on a small lan, 3 computers, and there is a router that connects to a cable modem and to the internet.  But since I am accessing the machine via it's local ip address the router shouldn't interfere with that, correct?  If it were a firewall, why am I able to get a connection for a little bit? I suspect if it was an intentional firewall/port block I would not get any connection, at least I think so.

---

### Post by GrayMagiker on 2007-01-29
Ok.  The problem doesn't happen all the time, but when I get disconected I can't connect fro about 5min or so.  This, combined with the fact I have Putty set up to send keepalive packets, is probably proof it isn't a time out issue.

Does anyone have any advice on how o troubleshoot this issue from here? 

I have the machine set up as a webserver to our local intranet as well, and I don't seem to have any problems loading pages from it.

I have looked at /var/log/auth.log and /var/log/messages as sugested, but I don't know if it is out of the ordinary or not.  I have attached /var/log/auth.log here incase anyone sees something which indicates a problem.  

Thanks for the help above, and thanks to anyone that can offer some direction for troubleshooting from here.

---

