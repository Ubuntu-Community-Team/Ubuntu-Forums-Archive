---
title: "Need Help Fast!!!"
date: 2007-10-21
forum: General Help
---

### Post by sharrell on 2007-10-21
I was playing with some settings on the screens resolution and refresh rate, now my laptop screen will not show anything after the Ubuntu loading screen.  I do not even get to the login aspect.  is there any way to restore the settings?????? please help!

---

### Post by chrisccoulson on 2007-10-21
Do you just get a blank screen, or do you get an error telling you that X failed to start? Can you switch to a terminal (CTRL+ALT+F1)?

---

### Post by jpittack on 2007-10-21
sudo dpkg-reconfigure xserver-xorg

---

### Post by chrisccoulson on 2007-10-21
> **jpittack said:**
> sudo dpkg-reconfigure xserver-xorg

After logging in via a terminal of course ;)

---

### Post by sharrell on 2007-10-21
I get to see Ubuntu loading (orange progress bar) then once it is done, nothing.....wait one sec my laptop turned the screen back on , 

ps would i place this in recovery mode? sudo dpkg-reconfigure xserver-xorg

---

### Post by jpittack on 2007-10-21
i suggest it, especially since its a safe bet

---

### Post by chrisccoulson on 2007-10-21
You should still be able to switch to a terminal and do it without booting in recovery mode

---

### Post by sharrell on 2007-10-21
I will go through that process anything i can do if it does not work

---

