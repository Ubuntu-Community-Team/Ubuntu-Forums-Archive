---
title: "Cant connect with Ubuntu"
date: 2007-02-13
forum: General Help
---

### Post by scannerman on 2007-02-13
I am still having trouble connecting to the internet via ubuntu? Can anyone help me?

I had a little help with a thread that i posted yesterday but to no avail so am a bit stuck!!

I am in the process of watch some videos on how to install ubuntu while still keep windows xp so that i will have the choice of the two when booting up so i will soon be running ubuntu from my hard drive.

I must admit that i am really begining to love ubuntu and am nearly a linux convert, its just connecting to the internet thats stumping me!!

Also, i have two hard drives but i cant seem to access them from ubuntu when i am running from the live cd? Anybody know why and how i can resolve both these problems?

Cheers

---

### Post by Soulxlight on 2007-02-13
Open your network settings in system > administration...what do you see ?

---

### Post by MCSE_Crossover on 2007-02-13
How are you attempting to connect to the internet? Are you using a traditional NIC or are you connecting wireless? If wireless, what type of wireless card? Are you configuring using Ndiswrapper? Are you using a static IP or DHCP? If you can answer all of these questions, it would really help! :)

---

### Post by scannerman on 2007-02-13
Well i wish i knew my way around my system like you guys do as i cannot tell you what system i am using so i will explain as much as i can.

I use a router that is connected to my computer through a network cable. I enter the ip address from the box which then allows me to enter my isp details, then it says i am online and i just open firefox and i am online. I have tried this through ubuntu and it says i am online but when i try and connect to any internet site it will not connect me. I am not sure where i am going wrong as to get it connected?

I think i am using DHCP but not sure what that stands for?!!!! The router i am using is a GURU if that is any help??

AS for what admin says these are the menus: device manager - gnome partition editor - install - keyboard indicator plugins - keyring manager - language support - login window - networking - networking tools - printing - services - shared folders - software source - synaptic package manager - system log - system monitor - time and date - update manager - users and groups

---

### Post by Soulxlight on 2007-02-13
:) What I ment was when you click on System > Administration click on Networking, and tell me what you see there.

---

### Post by MCSE_Crossover on 2007-02-13
> **scannerman said:**
> Well i wish i knew my way around my system like you guys do as i cannot tell you what system i am using so i will explain as much as i can.

I use a router that is connected to my computer through a network cable. I enter the ip address from the box which then allows me to enter my isp details, then it says i am online and i just open firefox and i am online. I have tried this through ubuntu and it says i am online but when i try and connect to any internet site it will not connect me. I am not sure where i am going wrong as to get it connected?

I think i am using DHCP but not sure what that stands for?!!!! The router i am using is a GURU if that is any help??

AS for what admin says these are the menus: device manager - gnome partition editor - install - keyboard indicator plugins - keyring manager - language support - login window - networking - networking tools - printing - services - shared folders - software source - synaptic package manager - system log - system monitor - time and date - update manager - users and groups

Just so you know, DHCP stands for Dynamic Host Configuration Protocol. It is what allows your router to dynamically allocate an IP address for your local machine instead of having to hard code a static one. You should have an address like 192.168.0.1 or something.

What you can try doing is opening up a terminal window and executing a "sudo dhclient." This should cause your NIC to poll for a broadcasted DHCP message, or in other words, configure itself with an IP address if it hasn't already. You should see a message stating something to the extent of "Polling message inbound blah blah blah" or something. When it completes, it should show you an IP address, something like what I listed above.

let me know if that works for you...it appears like everything else is configured.

---

### Post by scannerman on 2007-02-13
When i go to networking a new box called connections comes up with:

Wired connections- Address which is says is DHCP
General- Host Settings - Host name it says is ubuntu and the domain name is blank
DNS- DNS servers - this just shows the number i enter from the router box 192. etc

any ideas?

---

### Post by MCSE_Crossover on 2007-02-13
That should be ok...sounds like it is working. Does it show that device as enabled? You could try disabling and re-enabling it. If you go to a command line and type "ping 192.x.x.x" - being the IP of your router, do you get a response?

---

### Post by Soulxlight on 2007-02-13
First of all is it enabled...I assume it is. Well if DHCP isn't working for you for some reason, let us go with static, and see if it will correct your problem...you can always go back to DHCP.

Click on your Ethernet Connection, and then click on properties.

Make sure enable this connection is darkened, and go down to configuration, and and select Static IP address. 

Set this... Ip address: 192.168.1.97

subnet mask, I think auto sets itself as 255.255.255.0

Gateway Address will be the same as your DNS server > mine, and maybe yours : 192.168.1.254

Make sure you default eth0 is right...and click ok. maybe even restart, and see if it works now ^^

*Edit* Do what Crossover says first :)

---

### Post by scannerman on 2007-02-13
I am glad you are all bearing with me as linux is new to me and i am nearly a full blown convert to ubuntu, its just so difficult when you new to this stuff!!

I have tried enableing and disableing the device but again i cannot connect to the internet, it just times out every time. I typed ping and my ip address and it just kept scrolling alot of lines with my ip address at the beginging of each line?

---

### Post by llamakc on 2007-02-13
Pardon me for interrupting, but isn't the OP using the LiveCD? Any changes will not last after a reboot.

---

### Post by Soulxlight on 2007-02-13
:O Oh, I missed that...Thanks for bringing that up. I need to read post a little closer...

---

