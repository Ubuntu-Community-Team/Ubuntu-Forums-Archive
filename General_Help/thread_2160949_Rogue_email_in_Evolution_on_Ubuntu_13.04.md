---
title: "Rogue email in Evolution on Ubuntu 13.04"
date: 2013-07-08
forum: General Help
---

### Post by MickG01 on 2013-07-08
I have one rogue email in my Inbox. It's a spam email I have seen several times before when I was using Thunderbird which was reducing my system to a crawl. Hence the switch to Evolution.
I tried seeking the Inbox to see if I could simply edit it with a text editor but didn't find it. I believe its in the Home/Share/.local/.evolution tree
Can anyone suggest how I deal with this since as soon as Evolution starts the screen goes Busy (dark) and never comes out hence just trying to delete or Spam it fails.

Thanks

---

### Post by genterminl on 2013-07-10
If Evolution displays anything at all of the message before going out to lunch, you can try grepping for it.  In a terminal, cd to the top of the evolution folders and do 'grep -ir "something from the message"'.  Also - do you see anything useful in the status bar at the bottom of the evolution window?  I've had some hangs where it seems to get caught trying to fetch some image in the email, leading me to find some network issues.  If you can find the message, you can try looking it it in some text editor, or just deleting it.

---

### Post by MickG01 on 2013-07-10
I'll post this in case someone else experiences this with evolution:
I had a partially set up new email account which put up a dialog requesting a password each time I started evolution. I found that leaving this up I could scroll through the folder list and using arrow keys make sure I was on the 'inbox' then a right click let me mark all messages as read. then I cancelled the Password dialog gave a quick right click on the mesage and selected delete. Everything froze again except I could force close evolution via the 'X'.
Upon restarting evolution the message was deleted.
BTW the Grep -ir "Ink and Toner" (the start of the message subject) in a terminal gave 'Binary file mail/local/folders.db matches'

Thanks for the valuable suggestions which made me go down that path.

---

### Post by genterminl on 2013-07-13
I don't know Evoluntion's innards very well, but I suspect the folders.db hit was only on it's indexing info pointing to the message by title.  Not sure why it didn't find the message itself, but good you got it sorted out anyway.

---

