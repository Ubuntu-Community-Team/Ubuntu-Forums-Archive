---
title: "X display problem!"
date: 2005-05-31
forum: General Help
---

### Post by jchenzhao on 2005-05-31
Hi, there,

Just installed Ubuntu with network runing. I got a problem with display...

I telnet to another workstation (RatHat-based), set the DISPLAY based on my new Ubuntu machine's IP address. In my new Ubuntu, I set "xhost +". Then in the RatHat-based terminal, I tested the display by typing in "xcalc". However, I got a error message:

Error: Can't open display: 3.87.166.27:0.0

I had no this kind of problem when I used RedHat. Does Ubuntu do something different regarding to xserver?

Thanks for helps in advance!

---

### Post by logan2004 on 2005-05-31
aren't you using VNC?

---

### Post by jchenzhao on 2005-05-31
[QUOTE=logan2004]aren't you using VNC?[/QUOTE]
 No, I was not using VNC. I just opened a plain terminal and telnet to the RedHat workstation through it.

Thanks.

---

### Post by jchenzhao on 2005-06-01
It turned out telnet with remote X client is disabled in Ubuntu.
So I am using "ssh -X" now and very happy ;).

Thanks.

---

### Post by Anywhere on 2006-07-26
Hi all,
I've the same problem with TELNET, and i MUST use it because the server pc doesn't use ssh.
Is there any way to enable remote X display on telnet?
many thanks in advance!

---

### Post by patricktnk on 2006-07-31
Displaying Remote X-Windows Applications
== Computing ==
Displaying Remote X-Windows Applications
Thursday, 23 June 2005;    Word count: 472
[http://www.vyvy.org/blogs/index.php/2005/06/23/displaying_remote_x_windows_applications](http://www.vyvy.org/blogs/index.php/2005/06/23/displaying_remote_x_windows_applications) 
Suppose that you are working on machine local_client and would like to use an X Windows application which resides on another machine remote_server. There are several ways you can achieve this, and here are the popular ones.

Native Method
This method is native because it uses only 'pure' X windows system to accomplish the task. No security has been taken care. Nonetheless, the method is still useful in many circumstances and it serves as the basis of some other more sophisticated techniques.

First, on the remote machine, set the environment variable DISPLAY to point to the display of the local machine. If you use bash:

[remote_server] $ export DISPLAY=local_client:0.0 
Or, if you use C shell:

[remote_server] $ setenv DISPLAY local_client:0.0 
The trailing 0.0 is in the form of D.S, which means that the application is to be displayed on screen S of display D. Generally you need 0.0, unless you've set up multiple screens or multiple displays.

Second, allow the remote application to access the local display:

[local_client] $ xhost remote_server 
That's all! Start the X applications as usual and they should work properly. E.g.,

[remote_server] $ xclock & 
The most common error you'll encounter here is that the application complains some connection problem. For this method to work, the remote machine needs to talk with the TCP port 6000 of the local machine. (In general, TCP port 6000+D for display D.) So, make sure that the firewall of the local machine does not block this traffic. If you use gdm, make sure that you have the following in the configuration file on your local machine, usually at /etc/X11/gdm/gdm.conf:

[security]
DisallowTCP=false 
(/etc/X11/xinit/xserverrc  comment -nolisten tcp ??)
This lets the X server to listen to TCP connection.


Secure X11 Forwarding
You can do X forwarding over ssh. Simply connect to the remote machine with -X switch:

[local_client] $ ssh -X remote_server 
Start the X applications as usual and they should work properly. E.g.,

[remote_server] $ xclock & 
You can enable X11 forwarding by default by modifying the local ssh configuration file, usually at /etc/ssh/ssh_config. Specify the following:

ForwardX11 yes
ForwardX11Trusted yes 
If it does not work, then probably the remote server has not enabled X11 forwarding. To enable it, modify the remote sshd configuration file, usually at /etc/ssh/sshd_config. (Note that we have (a) ssh_config for the ssh client, and (b) sshd_config for the sshd daemon.) Specify the following:

X11Forwarding yes 
Remarks
There are always security impacts when you open more ports or enable more communication channels. So be careful if you use these techniques in a 'risky' environment. For more information, refer to the manual pages of ssh_config and sshd_config. For more techniques on displaying remote X applications, refer to Remote X Apps mini-HOWTO.

---

