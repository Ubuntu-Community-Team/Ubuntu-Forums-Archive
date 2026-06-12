---
title: "Windows Integrations  Problems"
date: 2004-10-28
forum: General Help
---

### Post by jmoulinier on 2004-10-28
Hi....
 I migrated to Ubuntu from Suse. I am tunning my box, but i have a serius problems with my windows netwok. I have two servers, one W2000 and other with Suse (samba).
I cant connect to my samba server without any problem, but I can't connect to any  windows machine, because a errors appear:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "Windows Network: mazinger".


I had been configured the network windows support on "Network Settings", but doesn't work.

I need help. Thank for all.
 :confused:

---

### Post by JKSteger on 2004-12-15
I'm having the same problems here. It's probably because I'm a total Linux Noob :D , but everyone starts somewhere.  All that I do know is that when I was running Fedora Core 2 I could browse the Windows network and all the windows servers were listed and then when I tried to connect to a server I would get a window that prompted me for my Windows username & password.  I would then add my username (domain\username) and then my password.  At that point I could connect to shares.  Is this possible in Ubuntu?  

BTW, I actually got my WiFi card working in Ubuntu, a task that I could never complete with any other distro!

Ubuntu Rocks!

JSteger

---

### Post by wulf on 2004-12-15
I'm not having any problems connecting to my Windows 2003 server... but I did have to install some extra software for that to work (at least one of smbfs, smbclient and libsmbclient - I think I put one of those on and the other two installed as dependencies).

Have you got those packages installed on your machines?

Wulf

---

### Post by JKSteger on 2004-12-15
[QUOTE=wulf]I'm not having any problems connecting to my Windows 2003 server... but I did have to install some extra software for that to work (at least one of smbfs, smbclient and libsmbclient - I think I put one of those on and the other two installed as dependencies).

Have you got those packages installed on your machines?

Wulf[/QUOTE]

Noob Alert!!! Noob Alert!!!
After posting I installed the above mentioned software the installed an application NetNeighborhood. I am able to browse shares and connect to my Windows Network.

Thanks,
Jeremy

---

### Post by jakeslife on 2004-12-17
I know that you're able to browse Windows folders from Linux on a network, but are you able to write to them or copy from them? Even though I know linux has poor NTFS support (or the other way around) I was wondering if it's possible.

---

### Post by wulf on 2004-12-17
[QUOTE=jakeslife]I know that you're able to browse Windows folders from Linux on a network, but are you able to write to them or copy from them? Even though I know linux has poor NTFS support (or the other way around) I was wondering if it's possible.[/QUOTE]
 Writing should be alright using a Samba connection - Linux sends a request to the Windows machine and Windows takes care of writing to the NTFS storage on it's hard drive. I've  been using this at work for a couple of years with no problems - I actually do 99% of my ASP based web development from the same machine and using the same tools (vim, a browser and a terminal) as I do for PHP, even though the system is hosted on my Windows Server 2003 box.

The place you are more likely to run into a problem is if you are trying to write to an NTFS partition on the same machine, where Linux has to work directly on the disk rather than just passing the information onto Windows. That's the setup I've got on my home laptop; I've set my access to the WinXP partition to be read only and haven't experimented with writing to it.

Wulf

---

