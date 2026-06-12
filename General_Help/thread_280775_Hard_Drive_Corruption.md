---
title: "Hard Drive Corruption?"
date: 2006-10-20
forum: General Help
---

### Post by Ghozt on 2006-10-20
I've been using Dapper for a while now, and I get this error sometimes when I boot into windows to play a game. Here's what it says:

/dev/hda3 had been mounted 30 times without being checked, check forced.
--------------------------------              50% (Goes through the checking process). Usually it doesn't say anything, but today it said that it had been corrupted and fixed the problems, reboot forced in 5 seconds. It reboots, seems to be working OK.. then X fails to start. I hit enter on yes to see what the problem is and it doesn't do anything, so I Ctrl+Alt+F1'd, it was pretty frozen. I finally got it to reboot and now it's working OK.. the only thing that worries me is that I didn't boot into windows this week, so I don't know why it's forcing the check. Has anyone else had problems like this before? Things I did in the session before I turned my PC off: Installed flash player 9 (just replaced the .so file), Tried to install Gaim 2.0.0.4 beta (alien didn't work, source didn't work, still isn't working...), checked my mail and checked out Digg.

---

### Post by m.musashi on 2006-10-20
> **Ghozt said:**
> I've been using Dapper for a while now, and I get this error sometimes when I boot into windows to play a game. Here's what it says:

/dev/hda3 had been mounted 30 times without being checked, check forced.
--------------------------------              50% (Goes through the checking process). Usually it doesn't say anything, but today it said that it had been corrupted and fixed the problems, reboot forced in 5 seconds. It reboots, seems to be working OK.. then X fails to start. I hit enter on yes to see what the problem is and it doesn't do anything, so I Ctrl+Alt+F1'd, it was pretty frozen. I finally got it to reboot and now it's working OK.. the only thing that worries me is that I didn't boot into windows this week, so I don't know why it's forcing the check. Has anyone else had problems like this before? Things I did in the session before I turned my PC off: Installed flash player 9 (just replaced the .so file), Tried to install Gaim 2.0.0.4 beta (alien didn't work, source didn't work, still isn't working...), checked my mail and checked out Digg.
The force check happens after each 30 boots whether or not there are problems. In your case, it seems to have found a problem. It sounds like it fixed it but it might be worth investigating the problem. How old is the drive? Is there a chance it might be dying? You might want to back up important stuff while you can. If it's an isolated incident then great but if there is a problem it would give you the option of a reformat or replacement without losing data.

---

### Post by Ghozt on 2006-10-20
It's a 300 Gig Maxtor Ultra-ATA that I got from Tigerdirect last year, I don't think it's dying. Are there any tests like Memtest86 that I can run to check the drive?

---

### Post by m.musashi on 2006-10-20
> **Ghozt said:**
> It's a 300 Gig Maxtor Ultra-ATA that I got from Tigerdirect last year, I don't think it's dying. Are there any tests like Memtest86 that I can run to check the drive?

I know my seagate came with a drive utility disc. Maybe maxtor has something on their web site. There is also the ultimate boot cd. It includes some drive utilites as well. If I remember right there is one for maxtor but I'm not entirely sure.

---

### Post by m.musashi on 2006-10-20
Get the ultimate boot cd at [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

### Post by Ghozt on 2006-10-20
I found [This](http://www.maxtor.com/en/support/downloads/powermax.htm), I'll run it tomorrow. Thanks.

---

