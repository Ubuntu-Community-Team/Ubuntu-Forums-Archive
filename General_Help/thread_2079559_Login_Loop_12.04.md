---
title: "Login Loop 12.04"
date: 2012-11-02
forum: General Help
---

### Post by DrSnooz on 2012-11-02
I was trying to watch a movie tonight on my laptop. I was changing over to my external monitor when my system locked up completely. Mouse wouldn't move, completely unresponsive. I did a hard power reboot. After entering my password at the login screen, I got to the desktop whereupon the system locked up again; mouse wouldn't move. On the second hard reboot, I got a login loop. I enter my password and get dumped right back into the login screen. 

I tried renaming my .Xauthority file in the text console per the suggestions of another thread. Now I can't even log in as my user in the text console. It just gives me "login incorrect."

Exactly how screwed am I? Will I ever see my data again? I've been working on this for a few hours now and have only made things worse so I'm starting a thread for it. 

PS: I'm working from the Guest account, which does not seem to be afflicted. 

Thanks everyone.

---

### Post by DrSnooz on 2012-11-02
184 views and no love? Is it that bad? The problem is that I no longer have a working admin account with which to make any changes. I'm dead in the water.

---

### Post by steeldriver on 2012-11-02
How about

1. boot to the recovery console

2. reset your password[ - see http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

3. check you can log in at the text console again

4. delete your ~/.Xauthority and ~/.ICEauthority files

4. check the contents of your ~/.xsession-errors for clues as to why the session is failing to start

---

### Post by DrSnooz on 2012-11-02
No go on the password reset. Still getting "Login Incorrect" in the text console (Ctrl+Alt+F1). 

The  worst thing that can happen to a user is a loss of data. It alarms me  that I can be using Ubuntu in the most ordinary manner imaginable when  the earth opens up and swallows every last bit of data I have on the  computer. I'm no fan of Windows and I know all their problems well, but  this kind of thing simply would not happen with a Microsoft product. If  Google results are any indication, I'm not the only one with this  problem. It should be Ubuntu's top priority and a solution should be the  first hit on any search engine. Instead, no one seems to know why this  happens or how to fix it. I'm sorry, but as long as this kind of  haphazard, death star code exists in Linux, the OS will never be seen as  anything other than a unusual novelty. If I have to scale the Linux  learning curve, I should, at the very least, be able to expect that my  data won't just up and randomly vanish into the ether.

---

### Post by pqwoerituytrueiwoq on 2012-11-02
is your /home encrypted? if no you can get it with a live cd/usb/dvd (or removing the hdd and connect it to another computer via usb/sata/ide)
login loop sounds like the session process is exiting due to a error
did you recently add something to your startup?
 > but  this kind of thing simply would not happen with a Microsoft product.true, you would not even be able to get to the guest account, and it would bsod instead of sending you back to the login screen

---

### Post by DrSnooz on 2012-11-02
Okay, I'm back in. This was my first time using the text console (tty1) "Ctrl+Alt+F1". The first time, I logged in by typing "sudo" followed by my username. I'm not sure why, but after that, I only had to type in my username. Can't tell you why. Anyway, once I got in, I renamed my ~/.Xauthority and ~/.ICEauthority files per steeldriver's suggestion above. That did it. 

In the interests of helping others who might read this thread, be sure to type "exit" when finished working in the tty1 console. If you don't, the console will remain open and active in the background even after you return to the GUI console (Ctrl+Alt+F7). You won't be able to reboot and the login loop will persist until you exit. 

PS: I'm not a fan of Windows and am transitioning away, but I have blown it up in some truly amazing ways, by doing some really boneheaded things. I've always been surprised by how my data is always preserved, even if I, say, hard power down the computer in the middle of a big database operation. I'm not sure how they do it, but they do. Yes, it's unstable and virus prone and all the rest, but the user data is sancrosanct. 

My Ubuntu data is still good, so I'm alright now. I'll keep moving forward with Ubuntu, but I'm a little concerned that it would just go poof without provocation. 

Thanks for your help steeldriver and pqwoerituytrueiwoq!

---

