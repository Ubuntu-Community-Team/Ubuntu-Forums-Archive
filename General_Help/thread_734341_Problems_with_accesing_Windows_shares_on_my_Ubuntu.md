---
title: "Problems with accesing Windows shares on my Ubuntu computer"
date: 2008-03-24
forum: General Help
---

### Post by rnorthco on 2008-03-24
Hello,

I'm a new user of Ubuntu, and I would like to say that I like what I see so far:) I've been able to resolve most of my issues, and seem to be learning quite a bit. My first major problem that I've run into has to do with sharing files and accessing network shares.

Here's the lowdown:

I have 3 computers networked together, one is running Windows XP, another is running 2K and the third is running Ubuntu(of course). I have shared folders as follows:

Windows XP: SharedDocs
Windows 2K: My Documents is shared
Ubuntu: /home/raymond/Documents

All computers are in the WORKGROUP workgroup and the computer names are as follows:

Windows XP: Jacks
Windows 2K: Surplus
Ubuntu:raymond-desktop

So here's my problem: I can browse all shares on the network using either Windows machine, but when I try to browse the shares using the Ubuntu machine, none of the computers show up. To make it even weirder, when I first set up the sharing Saturday night between the Ubuntu and Windows XP machine, I was able to see both computers, from the Ubuntu machine, but couldn't access the share on the Windows XP machine. I though maybe it had to do with the number of files that are in that shared folder, which is why I added the 3rd computer this morning, only to discover that now the Ubuntu machine sees none of them.  The last twist in this problem is that I can mount the shares by Using the connect to server option under the Places menu and the computer ip addresses, and once they are mounted, can browse the shares no problem.  

Here's my questions: Is this the way it is going to have to be setup? Or should I be able to browse the computers using the Network option under the Places menu. Also, once they are listed again, do I have to do something special to be able to browse them from my Ubuntu machine? Hopefully this makes sense, and any help would be appreciated.

---

### Post by PinkFloyd102489 on 2008-03-24
I dont think you can browse shares without mounting them somehow, like with the Connect to Server.

---

