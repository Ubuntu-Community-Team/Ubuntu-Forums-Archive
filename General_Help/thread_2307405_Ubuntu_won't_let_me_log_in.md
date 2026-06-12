---
title: "Ubuntu won't let me log in"
date: 2015-12-24
forum: General Help
---

### Post by ctparson on 2015-12-24
This is going to sound pretty dumb, BUT months ago I was trying to update the look on my desktop and I installed several new themes and icons, shortly afterward I noticed that the battery status was no longer visible in my status bar.  After doing some quick googling I saw a post in the ubuntu forums that provided a line of code that would fix this issue.  I entered it and after restarting my machine ubuntu will no longer accept my password it just spins then says failed to start session, if I try to login as a guest I get the same error message.  I got really busy with work and didn't have time to mess with it (hence I have forgotten what that line of code even was that started this mess) so I have been using an old laptop for months now, but it is getting to the point I need my newer machine back, even if it means wiping the hard drive and starting fresh.  

Really need help to either fix this, or tell me how to reinstall without being able to log in.  Thanks so much for any help with either option

---

### Post by yetimon_64 on 2015-12-24
Without the previously used code to know what potential damage has been done, it is a bit hard to suggest a fix for your situation.
> ... or tell me how to reinstall without being able to log in.
If you can't log in you can use a live cd version and recover any important files from your installation (assuming NO drive encryption is in use) to an external storage device (USB stick, external HDD etc). 

Once you recover any needed files you can just use the installer to overwrite the old install or you can use terminal tools (like "shred" or "dd") to erase the previous install then run the installer, whichever method you prefer. You don't actually have to "log in" to an existing install to do a reinstall.

---

### Post by ian-weisser on 2015-12-24
If you use CTRL+ALT+F1 to reach a console, can you log in?

If so, the mystery command might still be in your ~/.bash_history

---

### Post by ctparson on 2015-12-26
Can you walk me through the overwriting the old install from the command line, thanks

---

### Post by ian-weisser on 2015-12-26
Overwriting from the command line is rather complex.
It's much easier to reinstall by booting from a LiveUSB.
Remember to preserve your old data using the "Try Ubuntu" option first!

---

