---
title: "use terminal server client to connect to remote assistant on windows xp"
date: 2008-06-22
forum: General Help
---

### Post by Rainstride on 2008-06-22
i was wondering if it is at all possible to use terminal server client to connect to remote assistant on windows xp and fix someones computer and if so how to do it. i have a friend that doesn't know anything about computers so i need to be able to do this, and REALLY don't want to have to dual boot with xp or vista.

---

### Post by Neobuntu on 2009-04-08
That's a good question. Anyone?

---

### Post by DenysT on 2009-04-11
I use terminal server client to connect to XP Pro through remote connections so it should work for remote assistance too. Now if I could just get remote connect from XP to Ubuntu 8.10 to work. :(

---

### Post by Neobuntu on 2009-04-17
1. As I understand it, one can use remote desktop protocols (RDP) to log in; with appropriately setup (and allowed, software able) computers. The controlled computer must be logged out. 

2. Same time control and over the Internet (better be secured) are various forms of the original VNC (Virtual Network Computing) [http://en.wikipedia.org/wiki/VNC](http://en.wikipedia.org/wiki/VNC) . That includes Windows Remote Access, which oddly requires the help services to view. But you can use any server and client VNC programs. 

If you can have (or require) the controlled computer to be accepted by a live person, one of the popular utilities for doing this is (free) "CrossLoop" It is easier, and you only have to give the number on your screen (Share) to the (Access) person, anywhere is the world. It handles the firewall and hopefully secure details.

(free) UltraVNC is also very popular.

Of course with (K)UBuntu, we have our own tools for this. From unsecured XDMC log in (once setup) on private low security LANs (which you can tunnel more securely and better publicly). 

You do know that if you have multiple Ubuntu boxes on your LAN, you can log into any user account, at any box, don't you? That's the (unsecured) XDMC power of X(and why it's called a "server"). There's a log in screen built right into GMD and KDM login menus for it. You just have to wade through the settings (and make sure it's not open to the Internet).  


We have RDP clients with VNC ability as well. KRDP and an invitation program as well. Don't forget, many of the servers for this stuff, require an OK at that end.  

You can also run VNC clients in your browser, as that might be more convenient, in some cases.

Quick and Live CD's like Puppy Linux includes VNC clients. That's convenient. Boot and go.

What's interesting is ultimately, the "client" or "server" in these various controllable, secure and not secure methods, can mix Windows or Ubuntu and/or any combination. It is one of the more interesting ways to run Windows, as a Window in your Ubuntu box (given a spare networked and native Windows box). This is the way many companies keep and access one Windows box where open software is widely (and wisely) deploys. (That right there is worth the "price" of your ticket. I don't care who you are. LOL.)

Sound is even transferred with some. Speed of multimedia can be the problem and works best locally and with at least Gigabit LAN. 

There are even good techniques for not so demanding graphics that work quite fast. Even over very limited dial-up. FreeNX comes to mind. The business world buys Citrix.

I always wanted to test the FreeNX type compression speed ups (for multimedia); over "regular"(cheap) 100BT but haven't gotten around to it. 

So go to your PC!

---

### Post by s3a on 2009-04-17
If you know how to configure Windows to let it be controlled then I can tell you how to connect to it using Ubuntu.

---

### Post by sunlitlaz on 2009-04-17
rdesktop ([http://www.rdesktop.org/](http://www.rdesktop.org/)) is a great RDP tool.  Just enable remote support in XP and then use rdesktop to connect to it.  I think rdesktop is in the repositories even.

---

### Post by Neobuntu on 2009-04-20
A summary of a detailed article I read suggests that unless you need to run your specific and unique applications remotely, you might be better with your data and/or apps, and/or live operating system,  on portable USB sticks. Obviously, with pros and cons.

Also, Internet "places" (servers) might be used. Both for storage, remotely accessed and with the same Internet that it would take to do RDP. Also, you may use available Internet browser applications, like online word processors, as alternatives.

**REMINDER:** 

First: Current reality sees open software, as a viable alternative to Windows (or OS-X). The question is, why aren't most people adopting it?

Secondly, and perhaps even more important, is why are we paying a "toll" for the free Internet. What are we going to do about that? 

If either of these two things aren't available, we all lose.

---

