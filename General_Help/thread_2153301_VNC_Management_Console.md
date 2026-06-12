---
title: "VNC Management Console"
date: 2013-06-10
forum: General Help
---

### Post by Tropicalbound on 2013-06-10
Hello,

I want to be able to manage my Windows clients from Ubuntu.  I need the ability to push VNC (or some other remote control software) I've been searching unsuccessfully for a while now.  Can anyone point me in the right direction?

Thanks.

TB

---

### Post by Cheesehead on 2013-06-10
If you simple need command line access to your clients, then use ssh.

If you need to login to a GUI environment, then both VNC and RDP work quite well.

I happen to use VNC out of habit.
Rather than keep a (exploitable) VNC/RDP server (or client) running on your client at all times,
consider a simple script that:
- SSHs into the client machine
- Starts the VNC service on the client end (and perhaps your end, too)
- Establishes the VNC connection through an SSH tunnel
- Monitors the connection for termination
- Stops the service on the client end (and perhaps your end, too)

---

### Post by Tropicalbound on 2013-06-10
Cheesehead,

Thank you for the reply.  Your solution sounds great.  I currently have SSHd running on a server and from there, I can use PSEXEC to start the VNC service on the client.  However, what I'm needing is a way to push VNC to the Windows client.  Is there such a thing as a silent install that I could run from a CLI (again, I'd be logged onto the Windows client via PSEXEC).

Thanks again.

TB

---

### Post by HiImTye on 2013-06-10
use RDP instead of VNC, the protocol is much more streamlined - VNC sends images of your desktop, while RDP sends window information - sort of like using X forwarding in SSH. VNC also will distort until next redraw over some connections, which is annoying.


I have my box set up with only my SSH port exposed, which I use to port forward to other services, since it's secured with a 4096 bit key instead of a password, and it takes care of any compression. then I just connect my other services to ```
127.0.0.1:<forwardedPort>
```and I'm golden
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Tropicalbound on 2013-06-10
Thanks for the input HilmTye.  This is strictly for administration of a mid-size LAN.  None of what I'm wanting to do will be accessible form the Internet.  One point I inadvertently left out is I want to use VNC or similar so the end user can see the screen also.  RDP will blacken out the screen and then they can't see what I'm doing, or be able to answer my questions.

Thanks again!

TB

---

