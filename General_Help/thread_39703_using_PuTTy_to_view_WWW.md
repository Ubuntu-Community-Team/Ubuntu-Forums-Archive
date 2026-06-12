---
title: "using PuTTy to view WWW"
date: 2005-06-06
forum: General Help
---

### Post by boosted on 2005-06-06
Is it possable to use putty (SSH) from a windows desktop to access my ubuntu box and once I am connected browse the web?

---

### Post by SNo0py on 2005-06-06
[QUOTE=boosted]Is it possable to use putty (SSH) from a windows desktop to access my ubuntu box and once I am connected browse the web?[/QUOTE]
Yeah, install links (apt-get install links) and then you can surf the web, eg. links [http://ubuntulinux.org](http://ubuntulinux.org)

---

### Post by boosted on 2005-06-06
well that kinda works, but I can't really understand anything it displays??  Also I tried going to an https site and got an error msg saying it can't veiw ssl pages??  Is their a browser that is more ..how can I say, Visual??  like a normal web browser views web pages?  hhmmm, can I view X with putty(SSH)?  or just be able to run firefox or konqueror from putty?  the reason for this is I am at work and they block so many sites it's not funny and I want to be able to view my gmail, which is a https site, and some forums that I can't get to.

---

### Post by SNo0py on 2005-06-06
We are talking about console here ... so no graphics.

Regarding https, links tells you another browser you can use...

Regarding X - you can use VNC to connect to your home desktop, then you can use whatever is installed on the machine. Or you can use ssh to forward your X-Session to your working-computer, that should work too.

The last option I see is to install Apache and CGI-Proxy ([http://www.jmarshall.com/tools/cgiproxy/](http://www.jmarshall.com/tools/cgiproxy/)) - then you can use your home-computer as a proxy, this works very well.

---

### Post by boosted on 2005-06-06
hhmm...  so how do I go about forwarding my X session to my computer at work through putty?  I tried the link you gave me and can't view it here at work LoL!

---

### Post by SNo0py on 2005-06-06
[QUOTE=boosted]hhmm...  so how do I go about forwarding my X session to my computer at work through putty?  I tried the link you gave me and can't view it here at work LoL![/QUOTE]
[www.google.com](www.google.com) ;) 
There are tons of tutorials about this out there...

---

### Post by boosted on 2005-06-06
well to do that it says i need to install cygwin on my work computer..well seeings as how I have no admin rights I can't install anything  LoL   about the Links browser...  the error msg about https is this:
This version of Links does not contain SSL/TLS Support
the only option is to cancel    I didn't see where it gave me another browser to use?

---

### Post by SNo0py on 2005-06-06
Try VNC, then you don't need cygwin - e.g. TightVNC.

---

### Post by pietro_spina on 2005-06-06
I had no luck getting puTTY to forward an X session.  However using cygwin was successful. I did not have admin privileges when I installed it on my [XP box](http://mysite.verizon.net/vze7cyof/pics/cygwin.jpg)  at work... however because of a glitch or bug in AutoCAD I think we all have membership in a group called "PowerUsers" Maybe that bestows upon me some admin like privileges...

It is important to have Xforwarding enabled on the Ubuntu box.
In my C:\cygwin\usr\X11R6\bin\startxwin.bat file I used the following lines...

```
run XWin -fullscreen -clipboard -silent-dup-error
run xterm -sl 1000 -sb -rightbar -ms red -fg black -bg white -e ssh -Y -l root 68.163.138.148
```

one line sets up fullscreen mode the other runs ssh and forwards the xsession using an xterm. I think this  is kinda kludgey but it worked... I would then run fluxbox from that xterm... 

I could then alt-tab between my home computer and work... Not exactly the snappiest way to surf but it worked for me...

P

---

### Post by rothbart on 2005-06-06
[QUOTE=boosted]well to do that it says i need to install cygwin on my work computer..well seeings as how I have no admin rights I can't install anything [/QUOTE]

If you can't install anything you're outta luck (unless you use the web interface for VNC).  I use Hummingbird's Exceed for an Xwindows server and forward the Xwindows stuff via putty's built in forwarding.  Works fine.  But I do that from my work PC where my company bought Exceed, I wouldn't want to buy it myself just for that, it's great but spendy.  If you could install stuff, I'd recommend going through the hassle of setting up FreeNX because once you do get Exceed working and remotely access stuff, you'll realize how slow it can be (even via broadband).  FreeNX is a godsend in that case.  You're supposed to be able to use the GUI "usably" via dial-up (I've not tried this myself).  But via broadband speeds (upstream limited to 384kbps) it performs *almost* as fast as a local machine.  Of course that's all 2D stuff.  My work PC isn't set up for GL stuff.  So I'd say your best bet is the web interface for VNC (still needs Java for your browser -- hopefully it's already installed for you since you can't install stuff)

---

