---
title: "telnet shortcut"
date: 2022-08-15
forum: General Help
---

### Post by volden11 on 2022-08-15
hello, I'm new to Ubuntu, i"m looking for a way to set a desktop shortcut that will connect to a telnet server when someone clicks on it. I'm coming from windows so it was easy to do, and I'm not finding a way to do it on Ubuntu when i google search. any suggestions?

---

### Post by The Cog on 2022-08-16
I think this might do it, though there are many other ways:
Create a text file on the desktop with the following content;
```
#!/bin/bash
gnome-terminal -- telnet 1.2.3.4
```
and make the file executable.

Another way is to create a "desktop launcher" file, but I don't know how to do that (never tried). Here's a link I found: [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux)

You may also prefer to use a graphical program like remmina, which I imagine you can launch with either a desktop launcher, or just an executable text file in Desktop folder that contains the command ```
#!/bin/bash
remmina &
```

I am assuming you are in a position where you cannot use ssh because of the particular kit you are required to work on. If you do have any choice, then choose to use ssh instead - it is much more secure - encrypted and able to use public/private keys rather than passwords.

P.S.
Welcom to Ubuntu.

---

### Post by volden11 on 2022-08-17
i copied your text (the first one), made it excitable, and for some reason when i click on it, it opens in text editor. not sure what is goin on here. not used to this.

---

### Post by The Cog on 2022-08-17
Hmm. On my system I get a pop-up asking if I want to edit or execute it. I guess that's a difference between Ubuntu and Mint (an Ubuntu derivative which I'm using). I'm sorry I misled you there. 
I think you will need to make a proper .desktop launcher - that link should lead you through it.

---

### Post by TheFu on 2022-08-17
> **volden11 said:**
> i copied your text (the first one), made it excitable, and for some reason when i click on it, it opens in text editor. not sure what is goin on here. not used to this.

Some Linux file managers "protect" users from themselves by preventing the execution of programs though clicking.  If you create a .desktop file (it is just a text file like the old Windows 3.1 .PIF files, and point it at the script, it should work.  

Put the .desktop file in ~/.local/share/applications/ .... name it whatever you like, just with the .desktop extension.  May need to logout and login (no reboot should be needed) for the DE to fine it and add it to the menu.

BTW, telnet really shouldn't be used since 2000.  That's 5 yrs after ssh completely replaced all telnet, rsh, rlogin, rcp, and plain FTP tools.  Telnet can be handy for troubleshooting, but I can't think of the last time I used it - perhaps once in the last 5 yrs.  nc is the normal tool used these days, but bash can be used for remote, unencrypted, communications, if that is necessary (which should never happen).

BTW, .desktop files are only useful on systems with a DE.  For systems without any DE, most people would just open a terminal (your choice), then setup either a script or bash alias to make the connection.

Also, you could check your specific file manager version to see if there's an option to allow double-click program execution. This has security implications, so beware.  It isn't too hard to trick most unsophisticated Linux users into creating a nasty little script that allows a reverse shell back into their system.  In my beginning admin class, I'd have the entire class visit a webpage I'd created, have them copy/paste a small command ... which had hidden commands they couldn't see.  Everyone who successful did the exercise would have provided a reverse shell from my laptop back into their system, which I'd use for the rest of the class to screw with them by popping up programs, killing some of their programs, stupid things ... and in the last 10 minutes of class, I'd tell everyone what I'd done, so that they'd be careful.

Beware of copy/paste from websites.

---

### Post by volden11 on 2022-08-17
so here is what i'm looking at. we have a D3 pick server running on a windows VM. they didn't wanna pay for there software for each machine since it was expensive, not everyone needed full functionality, and I could use telnet to connect to it for free. now that windows is moving to TPM i don't want to have to replace the shop computers to, i figured we could run ubuntu on these older machines. on our current machines i run a desktop shortcut that connects directly to the pick server when they double click on it using the cmd. is there something that would work for this in ubuntu?

---

### Post by TheFu on 2022-08-17
The "D3 pick server", whatever that is, would determine what is possible, not Linux.  Which network protocols does it support? What APIs are available? Those would be the first questions, assuming you don't have the .... administrator's guide which would spell out everything.

---

