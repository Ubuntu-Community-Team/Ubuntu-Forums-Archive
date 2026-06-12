---
title: "Printing From Windows to shared Ubuntu USB Printer"
date: 2007-04-22
forum: General Help
---

### Post by jrlander on 2007-04-22
Hi,
I was working on this a few months ago, and couldn't figure it out on my own, so I was hoping some here could help me out.  I'm still a novice at linux, but getting better.

Here's the problem.  I have a USB printer (Epson Stylus 870) setup on my machine running Ubuntu (Feisty).  I can print everything fine from Ubuntu.  I want to setup my printer so I can print from my laptop running Windows XP.  I managed to share the printer, and I set it up in XP.  XP shows that the printer is "Ready", and I can even send a document to it, and it will show the document in the print queue.  The problem is, is nothing happens.  The document just sits in the print queue and never gets printed.  I can cancel the print job and it will go away, but no matter what i do, nothing prints.

Does anyone have an idea where I can start troubleshooting this issue?

Thanks.

---

### Post by jrlander on 2007-04-22
Just a little more information on this.  The print file is never actually making it to the Ubuntu print queue, it only shows up in the Windows print queue.  So, I'm wondering if it maybe some kind of permissions issue?

Also, when I print something in Ubuntu, I cannot see it from my Windows machine.  So, it seems like my Windows machine can see the printer on my Ubuntu machine, but for some reason they can't communicate.

Any thoughts?

---

### Post by jrlander on 2007-04-22
Alright, I think I figured some stuff out.  I changed how I mapped to the printer from my Windows machine.  Instead of using \\hostname\Stylus-Photo-870, I used [http://hostname:631/printers/Stylus-Photo-870](http://hostname:631/printers/Stylus-Photo-870).  I assume this works because of different permissions being used in the connection to the printer.

I am glad that everything is working now, but I would still like to know how to correctly get the printer to work by mapping it the first way.  If anyone has any information it would be greatly appreciated.  Thanks.

---

