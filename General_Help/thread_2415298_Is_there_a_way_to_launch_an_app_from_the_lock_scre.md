---
title: "Is there a way to launch an app from the lock screen?"
date: 2019-03-23
forum: General Help
---

### Post by zevermx on 2019-03-23
I'm running Ubuntu 16.04 as a media PC using Kodi. What I would like  is for anyone to be able to launch Kodi from the lock screen. Right now I  have to login and the launch Kodi, which leaves all the files  accessible to anyone else. If the app could be launch from the lock  screen I won't have to worry about files being moved or deleted by  someone else.
  
The Kiosk mode on Chromebooks comes to mind, but I would like for the user to go back to the lock screen when the app is closed.
  
Would it be possible to do this through by adding an icon to the lock  screen? Either on the screen somewhere or on the task bar at the top. I  also like the idea of a keyboard shortcut, but an icon would work  better for my purposes.
     
Thanks for your help.

---

### Post by TheFu on 2019-03-24
You can setup the kodi userid to login automatically, by default.  There are guides to accomplish that.
If you do this, be certain to lock down your account with stronger permissions to prevent the kodi userid from access.

---

### Post by coffeecat on 2019-03-24
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by HermanAB on 2019-03-24
Enable the Guest account and make Kodi available there.

---

### Post by zevermx on 2019-03-24
Thanks for the suggestions about another account. Does Ubuntu support having multiple accounts logged in at the same time like Windows? I have stuff running on my account that other PCs on my network rely on.

---

### Post by TheFu on 2019-03-24
> **zevermx said:**
> Thanks for the suggestions about another account. Does Ubuntu support having multiple accounts logged in at the same time like Windows? I have stuff running on my account that other PCs on my network rely on.

All Unix systems are multi-user from the ground up since the 1970s.  I've worked places with over 3,000 concurrent users logged into a single machine.

However, if those things need a GUI, then you'll have to change them over to non-GUI variations or use a virtual desktop.  A GUI session is a huge amount of overhead and should be avoided. Point-n-click uses about 20% of the power of any computer, including Windows.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a book that you can buy in any bookstore or just download from that link (no hassle) which will provide a little background on non-GUI techniques.

---

### Post by zevermx on 2019-03-24
Thanks. I'll check out the link.

Is it possible to add something like what I asked about in my original post? If not I think a second account is going to be what I have to do.

---

