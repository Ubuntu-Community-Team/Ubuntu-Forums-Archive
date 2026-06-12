---
title: "FirstClass Program Association"
date: 2006-10-07
forum: General Help
---

### Post by brich on 2006-10-07
We have just successfuly installed Ubuntu on an old HP Brio from a SHIP-IT install CD and everything works very nicely. 

We use FirstClass as our mail system, and have installed the Debian Version of the 8.1 client on the computer:fcc-8101-1-Linux-i686.deb which came from Centrinity's web site at:
[http://www.firstclass.com/ClientDownloads/FC81LinuxDownloadPage](http://www.firstclass.com/ClientDownloads/FC81LinuxDownloadPage)  This worked first time and seems to work pretty well. 

The only problem with this is that - with the Windows and Mac versions - clicking on a Word or Excel document will launch the appropriate Office application. We had hoped that - in FC/Ubuntu - the attachment would launch the appropriate Open Office application, but this doesn't happen.

If I save the document to the desktop and click it there, the association works and Open Office launches.

Is there something else I need to do, or is this likely to be a FirstClass problem?

Brian Rich
ruralnet|uk
[www.ruralnet.org.uk](www.ruralnet.org.uk)

---

### Post by HellRat on 2006-12-16
No answer yet, huh.. =(

Well I have a similar (same?) problem. If a a message in FirstClass contains a link and I click it, one would think firefox would open the url. That's just not the case on my ubuntu installation. 

At my university they run Debian Linux and FC but there it works. Mucho Strange..

Another thing about FC. When I login, the login seem to have forgot my saved password everytime I start FC. It looks as if there was a saved password but everytime I want to login I have to enter my password, save it and then login. It doesnt work if I just enter the pw and then click login, I have to save it first. And the next time I start the client... same thing again. Could this have to do with write-permissions or something? I don't know in which file the pw is saved.

---

### Post by HellRat on 2006-12-18
I found an answer to your problem but not for my link-problem though. 

Put this line in your ~/firstclass/fcapps:

.*      = gnome-open %f

It worked for me. It needs a FC restart to activate though.

It seems like the passwordproblem I had was a bug in version 8.1. Should work in later versions. I'll just have to wait I guess.

---

