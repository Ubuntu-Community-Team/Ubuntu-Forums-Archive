---
title: "Desktop on Server Log of issues!"
date: 2013-12-29
forum: General Help
---

### Post by steve.in.spain on 2013-12-29
Hi,

I am farly new to Ubuntu although have used debian in the past.  I am hoping someone can advise me on a problem.  We operate an online radio station and the software the runs it clearly needs to be online 24/7. Until now we have used a Windows server (2012) and can log in with RDC when we need to see the screen but Windows is expensive *adds about $25 a month to our server costs!

The software we use is compatible with WINE so I have played with it on various platforms and it works very stable.  Therefore to replace windows we want to run it on our server with WINE.  We have a number of servers around the world doing different things but because we need the GUI we were advised by OVH that we should use Ubuntu Desktop on one server, install wine and we are good to go.  This works and is perfect however...

Their installation comes with X2GO which is great except for when you log off it suspends your session, thus closing the running softeware.  So, for the software to run I must remain logged in here.. if my internet blips out I loose the X2GO session and tha software shuts down.  With Windows server I can log in with RDC and log out and the session remains active.  Is there any way I ccan achieve this with Ubuntu?

Is Desktop the wrong version to have on the server and wold Ubuntu server achieve better results similar to windows server? If so would I be able to have a GUI (with audio) on the server edtion and of course would I be able to install Wine?  Or, am I just missing the point here and logginf out of X2Go in the wrong way?

I should add they the X2O window will not close unless you either log out, suspend or terminate and all of these options have the same effect - to effectively log out the session on Ubunto Desktop.

Any help would be gratefully appreciated... you know when you are so near buy so far? lol!

Thanks!

---

### Post by damage3025 on 2013-12-29
I guess you probably want to use xrdp?

Microsoft uses Ubuntu and xrdp in its demo of Prime Challenge.
[URL="http://www.youtube.com/watch?v=xaVi8WDoVSA&feature=youtu.be"]http://www.youtube.com/watch?v=xaVi8WDoVSA
[/URL]
There is no much difference between "desktop" and "server" for Ubuntu, as open source software only have one awesome edition [1].
The only difference is that default selection of packages are different in desktop image and server image (Linux/Unix server traditionally do not have desktop).

1. [http://www.codinghorror.com/blog/2009/07/oh-you-wanted-awesome-edition.html](http://www.codinghorror.com/blog/2009/07/oh-you-wanted-awesome-edition.html)

---

### Post by steve.in.spain on 2013-12-29
Thanks for the reply but y question is a way to close the RDP connetion but leave the programmes running.  X2GO closes wlll programmes when you log out.  Is XRDP dfferent_

---

### Post by steve.in.spain on 2013-12-29
Tried XRDP and logs in fine but the display is nothing... a black and white dotted display.. Any advice would be gratefullty areceived!

---

### Post by damage3025 on 2013-12-30
Which version of Ubuntu are you using?
I guess your issue is similar to:
[http://askubuntu.com/questions/91657/blank-desktop-when-logging-in-via-xrdp](http://askubuntu.com/questions/91657/blank-desktop-when-logging-in-via-xrdp)

If you are using 12.04, you can use the top voted answer.
If you are using releases newer than 12.04, you should use the second-top voted answer.

---

