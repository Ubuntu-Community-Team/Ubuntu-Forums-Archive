---
title: "How to set up openssh server for Kubuntu? (lots of questions)"
date: 2006-08-07
forum: General Help
---

### Post by ewl1217 on 2006-08-07
I just installed the package "openssh-server" so I can access my computer remotely, but I'm a bit confused about all of it. Here's a quick rundown of what I need to know.
[LIST]
[*]Will the ssh server start automatically when booting up? If not, how can I make it do so?
[*]What is a good ssh client to use on Windows?
[*]How can I access my computer with a GUI through ssh? I know this is possible, but how?
[*]Is there a way to get sound through ssh? If so, how?
[*]I'm behind a router using DHCP. Is there any way I can make my IP static? Will I need to do any extra configuration (like port forwarding) with the router?
[/LIST]

**EDIT:** I forgot one last thing. How exactly is ssh encrypted? Are there any security concerns with using ssh?

---

### Post by jordanau on 2006-08-07
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

A quick glance through that will answer many of your questions

---

### Post by ewl1217 on 2006-08-07
Thanks for the link, but I'm really confused about the "Public key authentication" section. Could someone explain this bit to me?

---

### Post by gorded on 2006-08-07
I can answer the first two questions and the last one.

I think what you mean by the first question is will you be able to login via ssh without running command and that is, yes.

The secound i have used putty.exe on windows it works well from what i've used it for. [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Your last question, I am using a router, D-link. What i did go to DHCP tab  and assigned my computer a static IP within my home network.   

Enter hostname, Ip address, Mac Address (DHCP client should already be there) enable and add to the list of Static DHCP clients

Then goto the Advanced tab then Virtual Server, Enter hostname, The static IP you just assigned your self, Private Port (ssh default port 22), Public port same as private schedule Always. 

Now you should register your IP with a hostname, no-ip.com you can register 
and assign your IP address to one of many hostnames. If you have a dynamic IP then you should download no-ip from the ubuntu packages. 

then run  no-ip -C  follow the directions, and either reboot or start the script right away with /etc/init.d/no-ip start


Hoped that helped

---

