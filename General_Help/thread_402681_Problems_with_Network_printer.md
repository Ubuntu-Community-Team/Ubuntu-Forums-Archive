---
title: "Problems with Network printer"
date: 2007-04-06
forum: General Help
---

### Post by Mrlush123 on 2007-04-06
Im new at this and I am starting to understand. I configured a lot of things. I just cant get my HP Photosmart 2600 printer working. I installed it from system > admin > printing. I installed all the drivers the Hplib and the ppd files. It just still wont work.

What am I doing wrong? Can anyone point me in the right direction. I am trying many avenues and it still wont work.

Just so you understand my configuration. I have Ubuntu 6.06 and my printer is connected by network, (not another comupter). I have the IP address, the host name, the entire specs on the printer. I just cant figure this out. The icon comes up like it is going to print and it never does. Im frustrated with it. Can anyone help?

:confused:

---

### Post by Smuve on 2007-04-06
I'm not sure exactly what to tell you, but I can tell you how mine is set up.  I have an el cheapo HP D1341 hooked up to a D-Link Print Server.  These instructions are from my old Canon, I just haven't updated with my HP, which I just hooked up a few days ago.  The steps are the same.

Add Printer
Choose CUPS Network LDP
Host: 192.168.0.10 (This is the IP Address of my print server)
Queue: /dlinkps-454e04/iP4200 (I get this from the status page of my print server via the web admin)
Driver: Canon > iP4000

Getting the host and queue correct are probably why you're not getting any output.

Good Luck

---

### Post by Mrlush123 on 2007-04-06
[SIZE="2"][SIZE="1"]I'm not sure exactly what to tell you, but I can tell you how mine is set up. I have an el cheapo HP D1341 hooked up to a D-Link Print Server. These instructions are from my old Canon, I just haven't updated with my HP, which I just hooked up a few days ago. The steps are the same.

Add Printer
Choose CUPS Network LDP
Host: 192.168.0.10 (This is the IP Address of my print server)
Queue: /dlinkps-454e04/iP4200 (I get this from the status page of my print server via the web admin)
Driver: Canon > iP4000

Getting the host and queue correct are probably why you're not getting any output.

Good Luck[/SIZE][/SIZE]

I understand everything except the queue part and driver part. Can you tell me where or how I can exactly configure those things. Any help will be appreciated. 

Are you using ubuntu 6.06 or does it even matter?

---

### Post by Smuve on 2007-04-06
I'm using 6.10, but I don't think it matters.

The driver issue should be self explanatory.  One of the dialog boxes tell you to select your printer driver/.ppd.  You should just select your brand, then model.  When I first started with Linux, I kept hitting the Install Driver button after I selected my model.  Don't, just select your model and hit Forward.  If you found it, that means it already installed.

As for the queue, it's probably going to depend on how you have it set up.  As I mentioned earlier, I only know how mine works.  Mine is on a print server.  I type the print server's IP address into my web browser and navigate to the status page.  The status page has a Queue field, I simply copy and paste.

How is your printer networked?  If it's not on another computer, Is it on a print server or direct connect via ethernet?

---

### Post by Mrlush123 on 2007-04-06
[SIZE="1"]As for the queue, it's probably going to depend on how you have it set up. As I mentioned earlier, I only know how mine works. Mine is on a print server. I type the print server's IP address into my web browser and navigate to the status page. The status page has a Queue field, I simply copy and paste.

How is your printer networked? If it's not on another computer, Is it on a print server or direct connect via ethernet?[/SIZE]

It is not on another computer. I dont know what the difference is of print server and direct connect. Maybe if I explain you can tell me.

There is my hub, My computer is connected to it. My printer is connected to it. What would that make it?

---

### Post by Smuve on 2007-04-06
I have no idea if my terminology is correct but yes, that helps.  Your printer is connected via an ethernet cable, just like your computer.  

Just so know the difference for future reference, my printer is connected via a usb cable to a print server that connects to my router via ethernet.  Your printer is smarter than mine.

Anyhow, you need to find out your printer's ip address and queue.  Both should be in the manual or by scrolling through the menu's on the printer itself.

I think most ethernet printers use LDP, so you should be fine there, but you may want to check and see if it's on by default or if you need to activate it somehow.

You could also find the ip by logging into your router and seeing what's connected.

So, the three things you need to figure out are:
LDP on?
IP Address
Print Queue

---

### Post by Mrlush123 on 2007-04-06
LDP on?
IP Address
Print Queue

Ok LDP...?

When I was in windows at one point it worked. I had the same set up as now and I could connect and print no problem. So I think that is on. I think. How will i know for sure.

IP Addess is 192.168.1.101 

I can go to in from a browser but there is no print queue. Where or how do i go about finding that. I went to my printer and i printed out a report with all the network info and I dont see anything about print queue.

This is what the report says

Network status: Ready
Active Connection Type: Wired
URL: http//192.168.1.101
Hostname: hp2600
etc....

there is nothing about queue.

I set it up like you said. The print icon comes up and it says it is printing. But it does no such thing.


Any suggestions?

---

### Post by Smuve on 2007-04-06
I'm not at my pc at home, just going on memory here.

Try entering the hostname as your queue.  You might have to try different variations.  I seem to remember actually being very close at one point before I figured out that I need the preceding slash.

So now you have:
LDP: check
IP: 192.168.1.101
Queue: /hp2600

Notice how in mine, it looks like this /dlinkps-454e04/iP4200 because I have the D-Link between my router and the printer, so in your case, you can skip that part and go straight to the /hp2600.

Give that a shot, you've got to be close.

I've got an appointment out of the office, then I'm heading home.  I'll check this thread and my settings when I get home in a couple hours.

Good luck.

---

### Post by Mrlush123 on 2007-04-06
I figured it out. I needed to set it up network printer > HP JetDirect. I went into windows to look at the setting and it showed me 2 types of options the Queue option which is LDR and the RAW option which is with port 9100. HP JetDirect showed the 9100 port. And I figured it out.

I learned a few things about prints today. Thanks for your help.

Test Page 100% success

---

### Post by Smuve on 2007-04-06
Sweet, I'm glad you figured it out.

---

### Post by Mrlush123 on 2007-04-07
By any chance do you know anything about hooking up a Creative Zen on Ubuntu?

---

### Post by Smuve on 2007-04-07
Sorry, I don't have a clue.  I have an iPod and for the most part, it just works (except for couple quirks here and there).  I had Rockbox installed on it for a while.  That made file management really easy, but the battery life was terrible, so I went  back to the original firmware.  

Search the forums, I'm sure you're not the only one with a Zen.  Try this:
[http://ubuntuforums.org/showthread.php?t=352014](http://ubuntuforums.org/showthread.php?t=352014)

I seem to have had the most luck with Amarok as well.

---

