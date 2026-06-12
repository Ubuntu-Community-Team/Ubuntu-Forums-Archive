---
title: "Unable to Start Pigdin Internet Messenger"
date: 2008-06-22
forum: General Help
---

### Post by oib111 on 2008-06-22
I recently installed Ubuntu 8.04 in Dual-Boot Mode on my computer. At first run, Pigdin Internet Messenger worked great and I was able to chat away with my buddies with msn messenger. But now whenever I try opening it says "Starting Pigdin Internet Messenger" and then that goes away and nothing happens. If I go into the process list, it shows that the pigdin process is running. But the window isn't opening. Here's a picture:

[IMG]http://i165.photobucket.com/albums/u49/oib111/Screenshot.png[/IMG]

---

### Post by munkyeetr on 2008-06-22
Do you have pidgin set to automatically log in? I see the pidgin icon in your status area (1st icon on the left). When you click on the icon does the buddy list open?

---

### Post by oib111 on 2008-06-23
That's probably it, but now when I reboot and choose to boot into Ubuntu it doesn't load correctly and just goes to the shell. Anyway to fix this, or causes for it?

---

### Post by undertakingyou on 2008-06-23
sounds like an X issue.  You could try the code 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by oib111 on 2008-06-23
That didn't work. Should I just reinstall Ubuntu?

---

### Post by oib111 on 2008-06-23
-bump

---

### Post by undertakingyou on 2008-06-23
Shouldn't have to.  With situations like this it is hard to diagnose without being there.  Does the computer say anything like 'X won't start' before you get the login prompt?  What does your xorg.conf look like?  What is your video card?  Did you change your xorg.conf or any video drivers before you restarted and had this new issue?  (In your original issue pidgin was running fine, it was just minimized to the system tray.)  Did you do a <CTRL><ALT><BACKSPACE> in an attemp to fix something?  If you type sudo gdm restart or sudo startx in the terminal what happens and what does it say?

But in short we should be able to figure it out and not have to reinstall ubuntu.

---

### Post by oib111 on 2008-06-23
Lol. This isn't about pigdin anymore.

[quote="oib111"]
That's probably it, **but now when I reboot and choose to boot into Ubuntu it doesn't load correctly and just goes to the shell**. Anyway to fix this, or causes for it?
[/quote]

---

### Post by undertakingyou on 2008-06-23
hence why I said new issue. ;)

---

