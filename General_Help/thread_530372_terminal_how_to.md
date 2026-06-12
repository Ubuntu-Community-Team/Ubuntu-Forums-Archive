---
title: "terminal how to"
date: 2007-08-20
forum: General Help
---

### Post by kolbydukes on 2007-08-20
Hello, here at work we use a unix server and we always had dummy terminals that logged into the server through telnet, and we eventually ventured into the horrible world of windows and we used anita to emulate the unix terminal and I was really wanting to use linux for security reasons and it would be easier to maintain. So i installed it and brought up terminal and i telneted into the server and it worked OK, but all the f2 f3 and all the f keys were not mapped correctly, so i installed konsol and same problem, but when i use the f keys in other programs and with shortcuts in ubuntu (7.04) and everything works well, except for what i need, terminal. can anyone help me out here? thanks! - kolby dukes - kolbydukes.com

---

### Post by kolbydukes on 2007-08-20
bump.... i really need help.... help.... help... my boss is getting tired of me spending all this time working on something that he sees as pointless when windows works and i don't want to live in a microsoft world anymore! help!!

---

### Post by dad311 on 2007-08-20
I believe the F key functions are assigned in the dumb terminal itself.  Try going into the setup on the dumb terminal and find the F key setup.

---

### Post by kolbydukes on 2007-08-20
what do you mean by looking in the dumb terminal settings? just to clarify i am using a gateway pc with ubuntu 7.04 installed and i am trying to get it to work in order to replace the dumb terminal

---

### Post by PacketCollision on 2007-08-20
If you're using gnome-terminal, try **Edit->Keyboard Shortcuts** and disable all the shortcuts that involve the F-keys.  That should get things working as far as the terminal.  You might need to use a different telnet program (try PuTTY or something) if the F-keys aren't sent to the remote host correctly.

You might also have to mess with the terminal emulation settings.  If you set it to the same kind of terminal as the old dumb-terminals were, you might have more luck.  Try VT320 or something.

---

### Post by kolbydukes on 2007-08-20
thanks i will try those things out and let you know how things went! your help is very appreciated

---

### Post by dad311 on 2007-08-20
Im sorry, the term "dumb terminal" typically refers to a stand alone terminal(ie. vt100).  Try edit> keyboard shortcuts in the terminal program window.

---

### Post by kolbydukes on 2007-08-22
i know what dumb terminal means.... we were using stand alone terminals that was all they could do was log into one server... with the old green and black screen and we are trying to replace those with ubuntu machines, and i can't get gnome terminal or konsol to work and i have tried keyboard shortcuts nothing... anything else i could try?

---

### Post by PacketCollision on 2007-08-22
Well, I know that gnome-terminal sends F-keys, because I've tested it with htop, but it's probably getting lost somewhere between the terminal and the remote server.  I'm guessing the telnet program you're using is causing problems.  What telnet program are you using, the default netkit one? Have you tried putty?  (sudo apt-get install putty) It has many options for terminal emulation.  How about other telnet clients?  Have you messed with the options for netkit telnet? Again, what type of dumb-terminal were you using?  What version of UNIX is the server running?

If you provide more information, there is a better chance of someone being able to help.

---

### Post by kolbydukes on 2007-08-22
ok... i have tried putty but it could not render the telnet program... we use open systems acounting software (it was software written specially for us) and i do not know what dumb terminal we were on I will try to find out... hope this helps

---

### Post by PacketCollision on 2007-08-23
Do you know what kind of server it runs on?  For example, knowing that it was an IBM minicomputer running AIX 4 would help.

---

