---
title: "Aegis AntiVirus"
date: 2005-06-26
forum: General Help
---

### Post by Sir Osis Of Liver on 2005-06-26
I finally figured out how to access the Repositories, got the various necessary support files installed and got Aegis installed. When I look at the installation in Synaptic, it says it's installed correctly.

Where's the link to start/open the program?

All I've found is a shortcut in /usr/local/bin (might not be correct, I'm not at that machine right now). When I double-click the shortcut, it asks if I want to Run it, Run it in Terminal, etc. Regardless of what option I choose, nothing seems to happen.

I want to ensure I don't pass along an infected attachment, so I'd like to have some antivirus running, but this has me baffled.

I only installed Linux yesterday and this is my first exposure, so be gentle with me...
 :)

---

### Post by apollo2011 on 2005-06-26
Hello Sir Osis Of Liver and Welcome to the wonderful, magical world of *Free* Software!

I have installed Aegis Antivirus scanner and haven't really gotten it to work like it should.  First, Aegis doesn't scan for files harmful to Linux (there are none, yet) it scans for Windows viruses so that if you are sending files to Windows users (which most anyone is) you don't pass on viruses.  Also, I don't think Aegis is able to scan incoming/outgoing mail but simply files on your PC.  So if you have a file you created, it should be clean, but if you are passing on a file forwarded to you from someone else, you should save it and then scan it and then send it.  It can't do anything to your PC because you are running Linux and there are currently no viruses compatible with Linux :-)

Now, the problem you are having is executing it.  When you install a program on Linux, it usually puts a shortcut in one of several places (you found it in /usr/local/bin).  Anything you type into a console window without ./ in front, will be assumed to be a file in /usr/bin, /usr/local/bin, etc.  So you can run the file by typing the name of the shortcut from any console window.

From what I can see, the command to load Aegis is, "aegis-virus-scanner".  So if you open a new console window, and type that, Aegis should load.

The problem I am having, is that it always says there is a new update and updates but then says there is a new update the next time I load it.  It seems this is because you need to run it as sudo root in order to allow it to update.  But that should answer your question.

---

### Post by Sir Osis Of Liver on 2005-06-26
Doh. I did everything but run it from the command line. Thanks. I was hoping for something that would integrate into my email, but this will at least scan saved attachments.

Now to figure out how to put a shortcut on my desktop so I can eliminate all the typing. I seem to have a long learning curve ahead of me.

---

### Post by apollo2011 on 2005-06-27
Yes I am not exactly sure how you would add a shortcut to the desktop.  I use Kubtuntu which, uses the K Desktop Manager where as the normal Ubuntu uses Gnome.  I do have Gnome installed but I am not at my Linux PC at the moment.

I must say that I think you picked the right flavor of Linux to start out with.  I originally chose SuSE and it worked well and I got everything working for the most part when I started hearing about Ubuntu, I tried it out and have never ceased to be amazed at how much better it works and how much easier it is to get things working.  I started out on SuSE in January 2004 and started using SuSE primarily in January 2005, in between was some off and on usage where it sometimes got a little frustrating when I couldn't figure out things.  Now Ive learned the basics and am slowly switching all my PCs to Ubuntu and saying good bye to Windows. Amen.  :)

You should find that Linux has much better free support than Windows, or any other OS.  Many of the people who can help you learn or answer questions are the people who are helping test/develop the software.  Windows is only developed by a small group of people at MS and few of them go on and offer free support aside from Microsoft.

---

### Post by David Ranieri on 2006-04-29
Well now this is okay if only it would add itself to applications accesories panel

---

### Post by dallas7 on 2006-05-24
Aegis AntiVirus is broken and a waste of time.

---

### Post by raymurph on 2007-08-14
Hello Osis

I was able to add aegis to the list of Applications in the drop down menu by right-clicking on 'Applications', selecting 'Edit Menus'. In the 'Main Menu' window that pops up highlight 'Accessories' on the left and then select 'New Item' which will open a 'Create Launcher' window. Fill "aegis" into the 'Name' field and the command "aegis-virus-scanner" into the 'Command' field and press ok. Now press 'Close' on the 'Main Menu' window and the shortcut should be there when you next open Applications 

Hope that helps :)

---

### Post by gobbles414 on 2007-08-14
Hi all,

Dallas7 is correct! A quick Google search confirms that the old Aegis project has been abondoned, in favor of a new version powered by ClamAV. Take a look [here]("http://jodrell.net/journal/article/jgjgge.html"). I've had a lot of experience trying to find the perfect antivirus solution for Linux. So far, the best that I have found is the free version of Avast.

---

### Post by MerlinsLair on 2007-08-24
Glad I found this thread. I just want to make sure that I don't pass on anything to my Windoze-using friends. Will give the Avast app a try. But I have a question first....how are you getting it to run as it seems to be a Windoze app?

---

### Post by gobbles414 on 2007-09-18
MerlinsLair,

There is an official Linux version too. You can find it [here]("http://www.avast.com/eng/download-avast-for-linux-edition.html").

---

