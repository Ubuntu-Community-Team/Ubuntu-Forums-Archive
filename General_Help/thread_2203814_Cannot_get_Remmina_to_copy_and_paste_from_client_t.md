---
title: "Cannot get Remmina to copy and paste from client to server"
date: 2014-02-05
forum: General Help
---

### Post by pastim on 2014-02-05
I have found quite a few posts on the subject of getting Remmina 0.9.99.1 to be able to copy text from the client and paste to the server, or vice versa.  However, I haven't found any solutions.

Does it ever work, and if so, how?

I am on ubuntu 13.10 client, xubuntu 13.10 server.

---

### Post by TheFu on 2014-02-05
I don't use remmina (tried it but seemed to complex for my needs), but I use remote desktops all the time - on one right now. A remote desktop is my native way of working. 
Don't use copy/paste much - I use **select/paste** all the time - maybe 50 times a day. X/Windows has select/paste built-in and programmers have to go out of their way to disable it. A few programs do just that, for some unknown reason, I notice it in Firefox and Thunderbird.  Sometimes I can slip a select/paste though even with those programs, however.

[http://raven.iab.alaska.edu/~ntakebay/teaching/programming/xlivecd-doc/doc/copypaste.html](http://raven.iab.alaska.edu/~ntakebay/teaching/programming/xlivecd-doc/doc/copypaste.html) explains select/paste, though I have "focus follows mouse" set in the window manager, so my method is left-mouse button to select and center to paste. No need to click to focus.  If that doesn't work when using remmina, I would have switched to a different tool immediately. It is central to the way that I work.  Select paste does NOT work with remote MS-Windows machines. We can't have everything and MS isn't likely to help.

BTW, I use the **NoMachine 3.x NX client** (Windows and Linux versions) to connect to **FreeNX** servers running on Linux boxes. It is unclear to me which remote desktop type you are using, so those might not be options.

---

### Post by pastim on 2014-02-05
My client is Remmina, the server is running xrdp.  Both systems are ubuntu 13.10.

---

### Post by Adam_GUI on 2014-02-05
I had this same problem having no copy/paste tools with Remmina 0.9.99.1 using RDP.  
Using XUbuntu 12.04 to log into a local Windows 8.1 machine.

However, there is a way to share a folder during the connection.
Right click your connection in your connections menu and click Edit.

On your credential page for an RDP connection, at the bottom, should be an option for "Share Folder".
I pointed remmina to a folder called "/home/<username>/TestConnect".

The Shared Folder shows up in the server's connected "Devices and Drives" section of Windows Explorer. 

This method isn't as convenient as Copy/Pasting.  But, it was a decent work around.

I don't see any of the same options for connections other than RDP.
Either way, I hope this has helped.

---

### Post by pastim on 2014-02-06
Thanks.
 
I'm not really clear how sharing a folder helps me cut and past text, and at first sight I don't see how to use it in ubuntu (I'm not using Windows) or why it helps.  I already have network file access between the two machines.

---

### Post by Adam_GUI on 2014-02-06
> **pastim said:**
> Thanks.
 
I'm not really clear how sharing a folder helps me cut and past text, and at first sight I don't see how to use it in ubuntu (I'm not using Windows) or why it helps.  I already have network file access between the two machines.

My mistake.  I had to check my email and see your unedited post to see I never addressed copy/pasting text.
I completely glossed over that part and thought you meant copy/pasting files.

remmina doesn't grab your keyboard input by default.

After you connect, press <Right Ctrl + R>, and the client will grab your keyboard.
You should have text copy/paste working for text input.

---

### Post by pastim on 2014-02-06
So I start Remmina and connect.  I hit Right Ctrl and r (or R?), highlight some text on my client, then what?  I can't get it to paste into the server using Left or Right Ctrl v (or V).  I'm baffled.  Am I being really stupid or what?

I can see there's a toolbar icon to grab keyboard events, so I tried that as well to no effect.   I have had problems with keyboard layouts.  It is possible that my Right Ctrl is not being recognised.

Edit: - I have checked Right Ctrl is working using it with f to toggle full screen mode.

---

