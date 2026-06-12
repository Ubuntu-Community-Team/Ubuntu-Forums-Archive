---
title: "Echo Terminal to printer"
date: 2005-08-06
forum: General Help
---

### Post by markehle on 2005-08-06
Hello - 

I am a new Ubuntu user. I work at a public library, and I am trying to put linux in place of windows wherever I can. So far, I have been succesful in using Ubuntu for our online catalog computers. It works really well. My thanks to the folks who cook this stuff up!

I would like to use it for our checkout computers, but there is a problem. We use a telnet application to talk to our catalog server. The windows terminal application that we use, QVT Term, will print stuff to the printer, like reciepts and such. The printer is a little receipt printer that is attached to the parallel port on each checkout station. You can issue a command to the catalog server, and QVT term automatically routes the output to the printer. Must be some sort of escape code or somthing that tells QVT Term to print instead of display on the screen.

When I use gnome-terminal and get to the point where I need to print out the reciept, the receipt is printed on the screen instead of the printer.  How can I change this?

If we can solve this problem, I will be able to pretty much eliminate the scourge that is windows from our library!

Thanks -

Mark

---

### Post by amohanty on 2005-08-06
> When I use gnome-terminal and get to the point where I need to print out the reciept, the receipt is printed on the screen instead of the printer. How can I change this? 

Is this within the app or at the command prompt?

AM

---

### Post by markehle on 2005-08-07
[QUOTE=amohanty]Is this within the app or at the command prompt?

AM[/QUOTE]

This is from within telneting to the server that our catolog runs on. When you are looking at a library patron's record, you can issue the command to print a list and on the windows machines, the output is redirected to the receipt printer that is attached  to the PC. QVT term knows how to intercept the output from the server by way of some sort of escape code. 

From within gnome-terminal, I telnet to the server in the same way, and the stuff that would normally be printed on the printer is displayed on the screen instead. 

Is there a terminal app that runs on linux that could do this? Would kermit do it?

Like I said before, if we can get over this one thing, my boss would let me deploy ubuntu on all of our circulation terminals and get rid of winblows.

Last week we were hit by a windows-based network virus. Nearly brought us to our knees for about 4 days. I would love to get rid of all micro-shaft products if I could.

Thanks - 

Mark

---

