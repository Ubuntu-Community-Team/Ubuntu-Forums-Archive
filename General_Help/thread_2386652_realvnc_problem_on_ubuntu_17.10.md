---
title: "realvnc problem on ubuntu 17.10"
date: 2018-03-08
forum: General Help
---

### Post by rob141 on 2018-03-08
Good morning everyone.

So i was using ubuntu version 17.04 and i had realvnc working perfectly.

I have done a dist-upgrade into ubuntu 17.10 and that caused me some trouble unfortunatelly. I actually had to get the iso and re-install ubuntu 17.10 with the dvd but in the installation process i had choosed to keep old files and softwares because i did not want to loose everything. 

I am just saying to make sure that any help is up to date to what i did.

So,  so far everything works also perfectly with ubuntu 17.10 and i did not change the gui as i used to install xfce with older version of ubuntu. Now i am using the default one.

I still have the .deb of my realvnc server and when i double click on it, it open in the ubuntu software center and i can install it. it does tell me that it is installed after a few seconds but it is not anywhere ?? If i close the ubuntu software center and double click again on the .deb of realvnc, i still see it in the ubuntu software center as not installed since the button INSTALL is still present.

Does realvnc only work in xfce somehow ??  I have not tryed to install xfce and reinstall realvnc but is that what i should do ?  

Thank you very much for the help in advance ;)

---

### Post by HermanAB on 2018-03-09
Hmmm, just as well maybe.  VNC is mainly a way for new users to get their machines hacked.

Rather use SSH instead and save yourself from a whole load of trouble.  Even Windows now comes with SSH.

---

### Post by rob141 on 2018-03-09
I used to use ssh with putty but i never could get the graphic interface even after enebling the X11 forwarding. That is why i went with vnc.  is there a better ssh then putty that i can have the graphic interface too ?

---

### Post by HermanAB on 2018-03-09
"Putty" - you log in from Windows?  Windows doesn/t have an X server.

Install Cygwin and run it before you run ssh.

---

### Post by rob141 on 2018-03-09
I finally got it to work by following this:   [https://bkjaya.wordpress.com/2017/10/22/how-to-solve-the-problem-of-blank-screen-in-realvnc-viewer-when-connecting-with-remote-desktop-of-ubuntu-17-10-artful-aardvark/](https://bkjaya.wordpress.com/2017/10/22/how-to-solve-the-problem-of-blank-screen-in-realvnc-viewer-when-connecting-with-remote-desktop-of-ubuntu-17-10-artful-aardvark/)  

That solved the black screen problem.  Thx still for your help.

---

### Post by HermanAB on 2018-03-10
OK, so just to clarify the root of the problem:  Ubuntu (and a few other Linux distros) for some time used the Wayland display server, while programs like RealVNC and SSH require an X server.  

If you want to use X forwarding on Wayland, Windows or MacOS, then you got to launch an X server first.

This is one of the reasons why Wayland lost the popularity contest.

---

