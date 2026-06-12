---
title: "Emulating Windows Thin Client"
date: 2007-07-05
forum: General Help
---

### Post by Nimaran on 2007-07-05
Help. In order to access my internet I need a thin client( because of a device that blocks all traffic without one) 

However, this client is only available for Windows and Mac Operating systems. I need a way to emulate this program in Linux. All it is is a small program that comes on when I start my Windows and runs in the background. If needed I can get the Window's .exe, or the Mac .tar

Please help!!!

By the way if it is any help I have Wine installed.

---

### Post by dfreer on 2007-07-05
Can you provide a link to this software? We *might* be able to get it running, but your best option (and your right!) would be to call your ISP and let them know that you use Linux and you need access to the internet. If they refuse, refuse to pay them anymore and find yourself another ISP.

Another option would be to use NAT, either from another physical windows machine or a virtual windows machine on your ubuntu system.

---

### Post by Nimaran on 2007-07-05
I don't know if I could get you a link, but I may be able to upload it or email it to you. It'll take a little while though.

However, what is  NAT. I would be willing to try it. (Is it kind of like Wine?) 
If it helps the system using Linux is on a dual boot with Windows XP, and I have full access to that partition, which has the client installed.

I hope that information helps. Thank you for your help.

---

### Post by dfreer on 2007-07-05
NAT stands for Network Address Translation, it is built in to almost every home router because most ISP's only provide users with one IP address. Since you can't have more than one computer using an IP address at the same time normally, NAT was created. The machine with NAT has to have at least two ethernet ports (or a virtual ethernet port, I'll explain later), one to hook up to the ISP, one to hookup to a switch so that multiple PC's can "share" the NAT's internet connection. It is more of a network design scheme or protocol than anything else.
Wine is software, something completely different. Wine is designed to let you run windows programs on linux, although it isn't perfect yet so your software may not work (I seriously doubt it).

Really, First thing I would do is talk to your ISP. You are paying them to use the internet, why should you have to reformat your PC or buy extra hardware cuz they are being difficult. Explain to them your situation, and see what solutions the offer. If they refuse to help, take your money elsewhere.

Of course, they may be the only ISP in town, so here's what else you can do. Run vmware from windows (that can connect to the internet) and install ubuntu on it, it will be able to use the Windows Network connection to access the internet. You can try running vmware from ubuntu with windows installed on it, but I'm willing to bet that will just discourage you from ever wanting to touch ubuntu again. 

Who's your ISP, btw? (dunno if that is against the forum rules or not, I just want to see if they are really as hard headed as to prevent internet access without a piece of windows crap software).

---

### Post by Nimaran on 2007-07-05
Sorry, I guess I didn't specify well enough. It is not my ISP. It is a small device called a D-Link Secure spot, and it sits between the modem and the router, and provides, parental controls, firewall, and a whole bunch of other useful tasks for network security. I don't want to bypass or get around it or anything like that. I just need it to work with Linux, which it's thin client currently dosen't support. So I don't know if this NET thing will still work, but any further help would be great. Thank you.

---

