---
title: "GoToMeeting like on Ubuntu/Windows?"
date: 2007-09-13
forum: General Help
---

### Post by ELMIT on 2007-09-13
I  wonder if there is a program available which is similar to GoToMeeting, which can be used on Linux and Windows. (GoToMeeting is ONLY for Windows, but we are switching more computers now to Ubuntu)

bye

Ronald

---

### Post by maybeway36 on 2007-09-13
x11vnc is worth a try. You need to set it up in "listening" mode, but otherwise this should be straightforward:
[http://ubuntuforums.org/showthread.php?t=363236]("http://ubuntuforums.org/showthread.php?t=363236")
Ubuntu comes with a VNC/RDP client, but the VNC part of it isn't that user-friendly. (Many alternatives are available.) For Windows, use RealVNC or TightVNC viewer.

---

### Post by maybeway36 on 2007-09-14
Also, Ubuntu has a built-in Remote Desktop feature that can run in view-only mode. It only works when logged in, but that shouldn't be a problem.

---

### Post by dbutler on 2008-02-19
I'm also looking for a replacement.  Requirements are sending someone (windows user) an email with a link in it, they click on it (install something) and I'm able to control the computer.

[http://webex.com/](http://webex.com/) is a similar service that does work in Ubuntu (java).  Not sure if it's supported but works

---

### Post by sethd32 on 2008-02-21
WebEx claims to work on Red Hat Enterprise Linux , Red Hat Desktop, and SuSE Linux.  They state that other Linux distributions may work if they are using:

    * Linux Kernel 2.4+
    * Java Plug-In 1.4.1 or later
    * Xfree86

---

### Post by pangloss on 2008-03-08
Just to note, there are two different WebEx meeting products: MeetMeNow and MeetingCenter. The former is Windows only. I've used the latter with Firefox + Java 5 on Feisty. MeetingCenter's Linux option suffers a little in comparison to the Windows Firefox plugin (missing some VOIP options, doesn't look as nice). More importantly, however, I had trouble sharing applications--other recipients reported severe lag on window refreshes/drawing. No trouble when other people were sharing apps and even on my end, no trouble sharing apps using a similarly spec'ed Windows machine (so it wasn't hardware/network issues on my end).

---

### Post by wormser on 2008-04-23
I created a brainstorm idea for Screen Sharing.  It would be just like WebEx.  

[COLOR=Red]**Vote for it here:**[/COLOR] [http://brainstorm.ubuntu.com/idea/7487/](http://brainstorm.ubuntu.com/idea/7487/)

---

### Post by ELMIT on 2008-05-25
It seems there is still not a working solution available.

Webex is for me not affordable, and so I not even try it! 

VNC is not usable either, since I do not even have the bandwidth to support xx connections. So I have to go through a service. If I would have I would rather spend the money for the bandwidth than for Webex.

---

### Post by possumator on 2008-07-12
I would give NoMachine NXserver some serious consideration. It works over the SSH port 22 and is very bandwidth friendly. 

I have it running on Mandriva 2008.1 and it works fine on machines not running compiz fusion 3d (which seems to break it). 

[http://www.nomachine.com/](http://www.nomachine.com/)

Be sure to install all 3 packages of "NX Free Edition for Linux" in the correct order. Setup is a breeze.

---

