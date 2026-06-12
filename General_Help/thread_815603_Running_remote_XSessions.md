---
title: "Running remote XSessions"
date: 2008-06-01
forum: General Help
---

### Post by CactusWren on 2008-06-01
Hello,

I am running hardy haron and have vpnc working to connect me to my work network.
I need to run various xwindows-based applications on linux server at work.

Because of accessibility reasons, I cannot use vnc or NX to do this.

My question is:
Is there a way to run an xwindows application on the remote linux server and have it display locally.

I have run 

ssh -X
to connect to the remote server.

I have two basic questions:
1. what is the best method for setting my DISPLAY variable on the remote server?
2. Is there anything else that needs to be done to enable the xwindows applications to run?
I am assuming I have xserver running on the remote system.
How do I know if the xserver is running on the remote server? the remote system is an rhel 4 system.

---

### Post by HalPomeranz on 2008-06-02
> **CactusWren said:**
> 
I have run 

ssh -X
to connect to the remote server.

I have two basic questions:
1. what is the best method for setting my DISPLAY variable on the remote server?
2. Is there anything else that needs to be done to enable the xwindows applications to run?
I am assuming I have xserver running on the remote system.
How do I know if the xserver is running on the remote server? the remote system is an rhel 4 system.

Answers:

1) Logging in with "ssh -X" should set your $DISPLAY environment variable automatically.  You can check this by running "echo $DISPLAY" on the remote machine-- you should get output like "localhost:10".  If you don't get any output it probably means that X11 forwarding has been disabled in the SSH server configuration on the remote machine (or there was some other problem like the SSH server on the remote system not finding the xauth program) and you'll need to talk to the admin of that machine about turning it on.

2) Nothing else need be done to make X apps work.  Just run an app on the remote system like "xterm" and the window should pop up on your local display.  There does not have to be an X server running on the remote system for you to do this.

---

### Post by digitalbenji on 2008-06-02
Yes, ssh -X should be all that is required, assuming that your work VPN or network allows this.  You also need to have an X windows system on both ends for this to work.

---

