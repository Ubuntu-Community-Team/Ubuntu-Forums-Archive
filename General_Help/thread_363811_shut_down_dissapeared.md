---
title: "shut down dissapeared?"
date: 2007-02-17
forum: General Help
---

### Post by dracomordag on 2007-02-17
i somehow managed to make it so that i cannot shutdown either from the login screen or from inside my account.

how can i fix this? i assume it involves xsession somehow?

---

### Post by dracomordag on 2007-02-19
no one?

---

### Post by punkybouy on 2007-02-19
Not sure what you mean by "inside my acccount" but if you mean the shutdown icon is no longer visible on your tool bar you can right click on the bar and then click "add to panel" and then click on "quit" and add or just drag it back onto the bar.
I suspect this is not what you mean but what the heck I thought I would contribute something.

---

### Post by massivevoid on 2007-02-19
I have the same problem. After I installed Beryl, there is no "Restart" and "Shutdown", when you click "Quit".

---

### Post by sb770 on 2007-02-19
I recently lost my menu items when I last updated using Update Manager.  I couldn't get any menu items back or even get to a terminal window to issue shutdown.  It was wack...

BUT, I did have a file browser window open, so I was able to create a text file, add the line "sudo shutdown -r now" to the file, save it, right-click it, change the properties to allow execution, and then I was able to double-click the file to reboot my PC after being prompted for my passwd.  I'm going to save this file on my desktop in case it happens again.  (I'm at work right now -- on XP -- so I am relaying this from memory, but it did work.)

After rebooting, everything was back to normal...  :)

---

### Post by dracomordag on 2007-02-19
> **punkybouy said:**
> Not sure what you mean by "inside my acccount" but if you mean the shutdown icon is no longer visible on your tool bar you can right click on the bar and then click "add to panel" and then click on "quit" and add or just drag it back onto the bar.
I suspect this is not what you mean but what the heck I thought I would contribute something.
nah, i meant when i click the quit icon, only "suspend" and "hibernate" are options (obv along with logout, lockscreen, switchuser and cancel)

rebooting didnt help

---

### Post by Ramses de Norre on 2007-02-19
Are you using xgl? Because that behavior is an inevitable consequence of it.

---

### Post by dracomordag on 2007-02-19
> **Ramses de Norre said:**
> Are you using xgl? Because that behavior is an inevitable consequence of it.
nope. i did install fluxbox, but i dont use it.

---

### Post by Mikesco3 on 2007-03-18
I had the same issue. My scenario was the following.
   I use two desktop environments (*kde* and *gnome*). So basically I am running *Kubuntu* and *Ubuntu* on the same computer, but my welcome screen was using the *gdm* (Gnome Display Manager).
   I use the kde environment but I have my father as a secondary user and he uses the gnome environment. So when he clicked on the quit, he wasn't able to find **Shutdown** or **Restart**. 
   Well, I upgraded from Dapper to Edgy and then to Feisty, and during the process I was asked to choose what was going to be my main display manager and I chose ***kdm***.
   So I tryed several things first but none of them took care of the issue. 
Then I remembered the welcome screen being in *gdm* so I decided to try switching it back to that and voila, it was solved.

   So if your scenario is the same I suggest to do the following 

**[SIZE="2"]Welcome screen using the kdm (Kubuntu)[/SIZE]**
1) Open a terminal session by pressing **Ctrl+Alt+F2** and login with your username and password. Make sure you have administrative rights or login with a username that does. 
(You can go back to the graphical environment by pressing **Ctrl+Alt+F2** 

2) Type following:
```
sudo dpkg-reconfigure kdm
``` and select ***gdm*** as your display manager

3) Restart the system. 
______________________________________________________________________

   That should take care of your issue although it will change your welcome screen to the Gnome environment. But you can still login to a session in KDE if you have that environment installed.

---

### Post by dracomordag on 2007-03-19
oh, i solved this problem a while ago, but forgot to post the solution (gnome)

in the "start" menu, system -> administration -> login window
local tab
Show Actions Menu

---

### Post by mikewhatever on 2007-03-24
That's a strange problem. I've also had it after installing KDE along Gnome and making kdm default. It was possible to log out of Gnome and then shut down or restart, but not straight. Odd behavior.

---

