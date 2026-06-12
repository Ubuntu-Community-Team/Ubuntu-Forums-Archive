---
title: "vnc server help please"
date: 2005-04-01
forum: General Help
---

### Post by wolfwood2x on 2005-04-01
I successfully installed tightvnc server from synaptic. however when i run it with the comand VNCSERVER -geometry 800x600 -depth32 
it loads a server under :1 amd when i connect to it from another machine i dont see my gnome desktop. i see a grey screen with an x for the mouse but i cant right or left click or hit any keys i can just move the mouse around. 


How can i configure it to dump into my gnome desktop? can someone please help

---

### Post by gab10 on 2005-04-01
I'm having exactly the same problem, only I want to load into xfce.

---

### Post by foodcoman on 2005-04-08
Has anyone replied to this one?
I am taking my first Ubuntu spin with Hoary.

I installed SSH and I am able to get the exact same results.

I get a desktop with open shell windows, but no Gnome application bars.

What is the trick.  I installed the TightVNC package???

Who's the master?

I dont mind looking for other solutions, but I want it multiplatform.
This was a no brainer on Mandrivel!

---

### Post by gab10 on 2005-04-09
Have either of you (or anyone else) figured out how to fix this? I'm still stuck at the grey background with an X for the mouse and I can't do anything but move the mouse around.

---

### Post by wolfwood2x on 2005-04-10
alright i figured it out finally.

for anyone else having this problem first read this article:

[http://www.justlinux.com/nhf/Networks/Using_VNC_with_Linux.html](http://www.justlinux.com/nhf/Networks/Using_VNC_with_Linux.html)

and the translation of this is: first get to a terminal and type "su" and hit enter
next type in your root pass. one you get root@machinename$ type in "cd " and hit enter again you will see a blank promt with "/" hit enter one more time and it will clear your path. at this point if you hit "ls" you should see your bootstrap file.
now you can hit this: "cd ./.vnc" and then enter if you hit "ls" again you should see the Xstartup file type "pico Xstartup" and hit enter. then you can alter the line that says exec /etc/home/ blah blah i just commented it out with a # and wrote a new line. I didnt alter any other line except adding one line to the bottom that said "exec gnome-session &" Then i saved the changes and started a vncserver session. when i connected it was my gnome desktop. Im assuming you can change that gnome session to whatever desktop gui you really want. so guys please try this and let me know if it helps you out

---

### Post by wolfwood2x on 2005-04-13
if you dont want to run the vnc server as root you should cd to /.vnc/ from your home directory. its a hidden directory in your HOME directory and the xstartup file to edit is in there. Just follow the same steps as before to change your session to whatever gui you want. I hope this helps

---

### Post by foodcoman on 2005-04-15
[QUOTE=wolfwood2x]alright i figured it out finally.

one line to the bottom that said "exec gnome-session &" [/QUOTE]

Would anyone know what the proper entry to get KDE to load here?

---

### Post by YorYor on 2005-04-16
[QUOTE=foodcoman]Would anyone know what the proper entry to get KDE to load here?[/QUOTE]
 I believe it's "startkde &"

---

### Post by foodcoman on 2005-04-18
[QUOTE=YorYor]I believe it's "startkde &"[/QUOTE]

Yes that worked terrific!

It's interesting that it always starts a desktop session with a console window open.  I will resolve that lastly.


Thank you!

---

### Post by hyapadi on 2005-04-24
what program should i used if i want to access it from windows? I mean the client side for the windows.

Thanks

---

### Post by foodcoman on 2005-04-25
[QUOTE=hyapadi]what program should i used if i want to access it from windows? I mean the client side for the windows.

Thanks[/QUOTE]

[http://www.tightvnc.org/download.html](http://www.tightvnc.org/download.html)

---

### Post by emmort on 2005-04-30
Hello,

If you find some client VNC for windows, check the two URL here.

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)
[http://www.realvnc.com/](http://www.realvnc.com/)

Personnally I use real VNC., no problem with NT ( Neanderthaler technolgy) and 98.

god luck.

---

### Post by t3rror on 2005-05-02
***EDIT***

Nevermind guys, I was able to get SSH tunneling VNC working fine.  This is all I need.  Thanks.

***EDIT***

I am trying to get tightvnc allow me to automagically login to the x-session currently in place.  I can try to connect, but it says 'Please Wait - Initial Screen Loading'.  On the machine I am trying to connect to it is asking me if I want to let another user control my desktop.  I press 'Agree' and I can see the whole desktop and take over no problem.  How can I just automatically connect?

---

