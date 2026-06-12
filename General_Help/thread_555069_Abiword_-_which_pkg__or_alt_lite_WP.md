---
title: "Abiword - which pkg ? or alt lite WP?"
date: 2007-09-19
forum: General Help
---

### Post by bill45 on 2007-09-19
On my relatively new 7.04 install I decided to try Abiword.  Yes I have ofc00, but I read somewhere that Abiword was a less complex WP.  I see in Google search results many failed attempted installs of Abiword.  In the Syynaptic pkg there are 5-6 choices three of them being Abiword as well as help files and plugins etc.  

What is the difference and which Abiword should I install?  This is on an old slow Dell 
Plain - Gnome - or Common?  All Three? Is Abiword still in beta?
The package list definitions should explain these choices more clearly. 

What other recommended WP lite is out there that is a match for WordPad?
Do Linux/Ubuntu WPs accept RTF files?  What is the equivalent to Word Pad in Linux that retains basic paragraph formatting like RTF?

Bill C
[email]mozsugg@isp.com[/email]

---

### Post by por100pre1 on 2007-09-19
First remove your e-mail address from your post, you will get lots of spam! 

Just install abiword package first:

```
sudo apt-get install abiword
```

it will install other packages if needed.

---

### Post by yabbadabbadont on 2007-09-19
If you are already using Gnome as your desktop (you didn't say), then you might as well install abiword-gnome.  Otherwise install abiword.  Any required dependencies will be pulled in automatically.

Edit: Doh!  I seem doomed to post late today.  :lol:

---

### Post by bill45 on 2007-09-19
OK, Abiword is downloaded and installed but I can't find it.  what is the default location for application installs.  It is not appended to applications list.   It does show up in Gnome add/remove. 

I'm on a different machine now so give me just a general rule where to look for apt - get downloads.   I also installed Midnight Commander and that evokes from the terminal command line easily enough and I found the mc folder.

Bill C

---

### Post by yabbadabbadont on 2007-09-19
Try logging out and back in again.  A lot of times, new menu entries don't show up until the gnome-panel is restarted.  If you feel adventurous, hit Alt-F2 and run "killall gnome-panel".  Your panel(s) will disappear and then reappear.

---

