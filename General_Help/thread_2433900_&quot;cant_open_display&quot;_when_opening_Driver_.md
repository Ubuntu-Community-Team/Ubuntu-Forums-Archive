---
title: "&quot;cant open display&quot; when opening Driver or Software Center"
date: 2019-12-27
forum: General Help
---

### Post by sion26271 on 2019-12-27
Hello Linux experts, 

I'm running a VPS that runs Ubuntu 19.10 with Lubuntu Desktop.
I access  via RDP over SSH and when needed only with SSH.
My client Device is a Android Smartphone.

Everything runs great so far, my only Problem is when I try to open System Applications, like the Driver or Software Center through RDP.

They ask for my User Password, after entering nothing happens.
When I try to open one of the Apps through the Terminal, for example Additional Drivers with: 
/usr/bin/software-properties-qt '--open-tab=4'

After entering my Password again it says unable to open display 10.0.

Of course I Googled and found many solutions. 


I tried: 
-creating a dummy monitor with xorg 
-checking if X11 Forwarding is enabled in sshdconfig (it is)
-tried changing forward localhost to yes or no 
-tried exporting my display to localhost or 127.0.0.1 as well for display 10.0
-tried running xhost + as root and with + localhost, which also just reports unable to open display

Then I read that some kind of Xserver is needed to Display Applications like this.
So I downloaded a Xserver App for Android.
The APP said I should tunnel Port 6000. 
I did it using this command: 
ssh user/root@serverip -R 6000:serverip:22

Then I exported the Display do my local Device. But I still i get the unable to open display message in the Terminal. 
I also tried installing different GUIs, but the Problem is always the same.


At this point I really have no clue what else I could do. I'm new to Linux. 
So if anyone has a suggestion or Idea how I could solve this I would be very very Happy.
Or if someone could tell me if I actually need such a "Xserver" after all I just want Applications to run on my RDP App not through another APP like Xserver.

Many Thanks!

---

