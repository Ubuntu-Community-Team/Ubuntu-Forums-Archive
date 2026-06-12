---
title: "Sharing files with Windows in VmWare"
date: 2007-01-15
forum: General Help
---

### Post by Spankmaster79 on 2007-01-15
Hi guys,

I have a problem making files or network nevices available via smb to my Windows client in vmware. :confused: 

I don't know if it really is a network or vmware problem since I didn't manage to make network devices available in the VM on a Windows host also.

I'm using a bridged Network and I can surf the I-Net through the VM, so network is up and running. I just don't know what is the best way to make files from my Ubuntu host available for the VirtualMachine.

I thought sharing them as network devices via smb would be the easiest way but my XP VM always tell's me that there is no "Spanknet" available and if I do have the rights to search my "Spanknet". :D 

I just virtualized my XP with the new vmware-converter, because I wanted to switch completely to Ubuntu and only use Windows in vmware. 

Does anybody have experience on this ????

Greetz
Spanky

---

### Post by mdurham on 2007-01-15
I'ne never heard of "spanknet",  what is it? Sounds like something a virus might produce.

---

### Post by Spankmaster79 on 2007-01-15
:-D :-D :-D *lol* ooops you got me laughing....sorry.....*rofl*:-D :-D 

"Spanknet" is not a virus. It's the name of my Windows Network. I named it like that. Spank-master - Spank-Net - Spank-omedia 

You just made my day!!!!! :-D :-D :-D

---

### Post by gh0st on 2007-01-15
I have my machine set up with Samba to share files with my VMWare windows machine. I use bridged networking so it's definitely not that causing the problem. I did have to tinker for a while to get Samba and XP playing nicely together.

I got it working using this guide from the VMWare website, just follow the Bridged Networking section.

[http://www.vmware.com/support/gsx3/doc/network_samba_gsx.html](http://www.vmware.com/support/gsx3/doc/network_samba_gsx.html)

It talks about a tool called GSX which is a Samba derivative made by VMWare but ignore that just follow the bit that says about setting up with Samba already installed.

If you need anything else just let me know. Hopefully that should be of some help to you :D 

P.S - Have you enabled file sharing services on your XP machine by using the network setup wizard to join the workgroup? I managed to forget to do that some how when I first set my machine up... doh! :)

---

### Post by daverave999 on 2007-01-21
[This]("http://ubuntuforums.org/showthread.php?t=296668") thread sorted me out!

---

