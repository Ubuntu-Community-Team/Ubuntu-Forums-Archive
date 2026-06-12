---
title: "Accessing WIndows 10 Remote Desktop from Ubuntu 18"
date: 2021-07-08
forum: General Help
---

### Post by artist-wavenet on 2021-07-08
A friend who has a Windows 10 computer needs help, and has agreed to give me Remote Desktop  access to help her. My OS is Ubuntu 18.04.

I see in my computer's Remmina application where to enter her computer's IP address. Trouble is her computer is on a home network, and so the question is raised how to get through that network's router to her computer. The IP address of her computer would be the one it has on that router's network which would not visible to the World Wide Web. I could enter her household's router's gateway IP address, but then how would that router know which computer on its own network to route my RDP traffic? Would her computer have to be put in that router's DMZ? Are other options besides the DMZ? is there a way for Remmina to use her computer's name on that router's network?

I know it is more easily done with an application such as TeamViewer. But I want to avoid the subscription fee for it.

---

### Post by TheFu on 2021-07-08
Use **teamviewer**.  TeamViewer is free for occasional use and it has instructions for Linux.

That would be more secure than opening RDP to the internet and getting hacked.  Based on the questions above, doing that would be a really bad idea.  Having a remote desktop directly available over the internet is a bad idea for everyone.  I allow ssh or VPN connections from the outside world, so network authentication has to happen, then, I use a remote desktop tool (which won't connect to MS-Windows) only when necessary. 99% of the time, I work over ssh in a CLI situation - no GUI.  I provided support to my Mom's system 3 states away for years doing it this way.

There are all sorts of options, but using something like TeamViewer is the easiest for Windows people and for people who don't fully understand networking and network security.

---

### Post by HermanAB on 2021-07-10
You need to configure her internet router to forward the RDP port 3389 from the internet side to the LAN IP address of her PC.  That can work, but you should disable it as soon as you are done to prevent hacker problems.

---

