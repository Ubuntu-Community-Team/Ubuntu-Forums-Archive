---
title: "the problem with exiting the standby mode"
date: 2021-05-22
forum: General Help
---

### Post by fireguardspb on 2021-05-22
I have an asus ux431fc laptop that has Ubuntu 21.04 installed on it. And there is a problem that after closing the lid of the laptop, the laptop goes into standby mode and after opening the lid it normally exits from it, but if you close the lid for the second time, the laptop also goes into standby mode, but after opening the lid from this mode already does not come out, the indicator on the keyboard is on, but the screen is turned off and does not react to anything. I can turn off the laptop only by long pressing the power button or reboot via REISUB. Help solve this problem, please.


I shot a video of how all this happens.
[https://drive.google.com/file/d/1OLhsyD9LQjxaqXwd7siGSkdTR4i1pjRN/view?usp=drivesdk](https://drive.google.com/file/d/1OLhsyD9LQjxaqXwd7siGSkdTR4i1pjRN/view?usp=drivesdk)

---

### Post by TheFu on 2021-05-22
Can you change to a different tty or ssh into the system from another machine?

---

### Post by fireguardspb on 2021-05-22
> **TheFu said:**
> Can you change to a different tty or ssh into the system from another machine?
   I started a local server on my laptop and tried to connect to the server from my phone after I opened the lid. After the first time, as I wrote about this before, everything connects normally. But after the second opening of the lid, the screen is off again and there is no connection to the server.

---

### Post by TheFu on 2021-05-22
And ssh?

---

### Post by fireguardspb on 2021-05-22
> **TheFu said:**
> And ssh?
  
 I don’t know how to connect via SSH without a local network. My laptop is now connected to the hotspot on my phone.

---

### Post by TheFu on 2021-05-22
> **fireguardspb said:**
> I don’t know how to connect via SSH without a local network. My laptop is now connected to the hotspot on my phone.

I don't understand what you mean by "connection" then.  

ssh is the core method for connecting any system to any other system.  With ssh, we get scp, sftp for free automatically and rsync, sshfs, x2go with just a little more effort.

Also, you said nothing about changing to a different tty and how that worked or not?  I'm trying to eliminate stuff often overlooked.

So - ssh and changing to a different tty worked or not? Please be explicit.

---

### Post by ajgreeny on 2021-05-22
Just in case you are unaware of the tty consoles, they are moved to with Ctrl+Alt+F1-6 for the text consoles, and Ctrl+Alt+F7 normally takes you back to the GUI.

Try switching around in those and finally back to the GUI.

---

### Post by fireguardspb on 2021-05-23
> **ajgreeny said:**
> Just in case you are unaware of the tty consoles, they are moved to with Ctrl+Alt+F1-6 for the text consoles, and Ctrl+Alt+F7 normally takes you back to the GUI.
 
 Try switching around in those and finally back to the GUI.

Nothing happens. So I shot a video of how all this happens.


[https://drive.google.com/file/d/1OLhsyD9LQjxaqXwd7siGSkdTR4i1pjRN/view?usp=drivesdk](https://drive.google.com/file/d/1OLhsyD9LQjxaqXwd7siGSkdTR4i1pjRN/view?usp=drivesdk)

---

### Post by ajgreeny on 2021-05-23
Other than the fast speed at which you were trying to move between the various tty consoles that is very strange.

Can you switch between them and back to a GUI if you start from a full GUI desktop?

---

### Post by fireguardspb on 2021-05-23
> **ajgreeny said:**
> Other than the fast speed at which you were trying to move between the various tty consoles that is very strange.
 
 Can you switch between them and back to a GUI if you start from a full GUI desktop?

 Yes of course.
In the link to the video where I start from a full GUI desktop.


[https://drive.google.com/file/d/1OjzLhP89O6PBvkZU4feXzOJ9duLVPiVv/view?usp=drivesdk](https://drive.google.com/file/d/1OjzLhP89O6PBvkZU4feXzOJ9duLVPiVv/view?usp=drivesdk)

And here is a link to a video in which I once again try to switch after the second opening of the laptop lid.

[https://drive.google.com/file/d/1OopIFR2jCA4bcOnp9mv76yUFpvu1PeWS/view?usp=drivesdk](https://drive.google.com/file/d/1OopIFR2jCA4bcOnp9mv76yUFpvu1PeWS/view?usp=drivesdk)

---

### Post by fireguardspb on 2021-05-30
Have idea anybody?

---

