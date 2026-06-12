---
title: "How do set up home network?"
date: 2005-05-26
forum: General Help
---

### Post by DutchLau on 2005-05-26
Hello Ubuntu community,

I have been playing around with networking and setting up a home network for a while. I have samba and smbfs installed, but with the instructions of the Ubuntu guide I cannot figure out how to set up a home network to share files. How should I do this? I have two computer set up with a hub and my internet is connected to the hub to share the connection. 

Could someone please explain how to set up a up the home network so I can share files? Only files will do. Thanks alot already,

DutchLau

---

### Post by Sleeper Service on 2005-05-26
Firstly, I'd *really* recommend a firewall.  You can either get hardware firewall/routers, or else get an old PC and install [Smoothwall](http://www.smoothwall.org/) on it.  That's a very easy to download and install distro that is a firewall and nothing else.

My system goes: broadband router > smoothwall > network switch > other PCs.

If you're going to make files available to other machines, you're taking a big risk without a firewall.

Beyond that, it would be helpful to know what kind of machines you want to network.  Are they both running Ubuntu?  If so, you could simply create a shared directory on each machine that you could mount from the other.

---

### Post by DutchLau on 2005-05-26
Hello, and thanks for the speedy reply.

I have both computers running Ubuntu 5.04 with Firestarter firewalls. What must I do to get the network up and running though? I don't want a server because I use both computers intensively and I want to interchange files. 

Thanks already,

DutchLau

EDIT: My network works as such. I have an ADSL modem that is plugged into slot one of a hub, then I have 2 computers (currently) plugged into other slots of the hub to share the internet.

---

### Post by MrTom on 2005-05-26
I am guessing that the ADSL modem is a modem/router thing? and that you want to simply share files?

system->administration->shared folders allows you to create folders shared on one computer, then places->network servers->windows network should find the folder on the other.

I hope that helps.

---

### Post by DutchLau on 2005-05-26
I'll give that a try, the only thing is that I don't have windows at all. Is this a problem?

---

### Post by MrTom on 2005-05-26
no, SAMBA can do anything! You could use NFS, but it would make life more complicated  especially if a friend wanted to use a windows machine on the network.

---

### Post by DutchLau on 2005-05-26
Okay, so all I have to do is go to System=>Administation=>Shared Folders   and select the folders I want to share? And to access them from the other computer I go to Places=>Network Servers=>Windows Network   and I will find the folders/files there? It just *can't* be that simple. Are you sure that's it?

---

### Post by MrTom on 2005-05-26
It should be ;)

under 'General Windows Sharing Settings' setting the workgroup to the same thing will help things (makes it obvious things are working)

Make sure your firewall allows windows network traffic (ports 137-9) on the local network. Otherwise  all the filesharing will be blocked.

---

### Post by DutchLau on 2005-05-26
Alright, I set up that porst 137, 138, and 139 are open. Now I'm off to see the wizard...  :razz: 

Thanks a ton guys, I will report back when I get it working!

---

### Post by DutchLau on 2005-05-26
Okay, after having done this on my two computers, it still doesn't seem to work. I installed ' samba ' and ' smbfs ' and I can't see any shared folders. 

I go to Places=>Network Servers=>Windows Network (which takes a while to load) and then when I'm there, no shared folders/files show up! Even though I have shared my /home directory with SMB, nothing happens  :-| 

What am I doing wrong? Could someone please help me? My family is about to kill me because I threw windoze off both computers and I only have Ubuntu, but they (and I) want filesharing! Now they're talking about putting windoze back on.. Please please help!  :-|  I'm baffled

---

### Post by YaAqoB on 2005-05-26
Hi I have samba setup one my Ubuntu PC and WinXP Pro on the other. I have set the shared folders etc.
On the Windows PC i can see the files I have shared on the Ubuntu machine. When I try to access them it asks me for a login and password.
How do I set the samba login and password?

---

### Post by MrTom on 2005-05-27
Are both machines in the same workgroup? Windows is a bit funny about that.

---

