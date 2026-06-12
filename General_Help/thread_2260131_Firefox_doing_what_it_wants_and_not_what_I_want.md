---
title: "Firefox doing what it wants and not what I want"
date: 2015-01-09
forum: General Help
---

### Post by Evil Wayz on 2015-01-09
So I have my download directory in Firefox sext to home/me/Downloads.  And most of the time, Firefox downloads stuff there.  The exception is torrent files.  Those, Firefox decides it's going to download to /tmp, and then open with VLC player.  Even though if you right click on a torrent file, under the open with tab it shows Transmission as the default application.  If I go under the hood in Firefox to the applications tab, under BitTorrent seed file it also shows Transmission as the default application.  Oh, another fun thing, sometimes I get a nice gray box that asks me if I want to open the torrent file with Transmission, which I appreciate.   But only sometimes. 

So, what's up with this?

---

### Post by monkeybrain20122 on 2015-01-09
I don't know. Maybe those torrent links are fishy. I never have that problem.

---

### Post by Holger_Gehrke on 2015-01-09
This might be a server-side problem. ff relies on the server to give it a MIME-type for the file. If the server gives the blanket term "application/octet-stream" and you at some point in time gave vlc as the right handler for a file with that non-type ...

---

### Post by Evil Wayz on 2015-01-09
> **Holger_Gehrke said:**
> This might be a server-side problem. ff relies on the server to give it a MIME-type for the file. If the server gives the blanket term "application/octet-stream" and you at some point in time gave vlc as the right handler for a file with that non-type ...


I may have, I don't remember.  How do I fix that?

---

### Post by monkeybrain20122 on 2015-01-09
There is a file called mimeapps.list in ~/.local/share/applications. You can edit it (change the application for application/octet-stream) You may need to logout and log back in. The folder .local is hidden. So open the file manager, press ctrl h or choose show hidden from menu, find .local, go down the path of subfolders  and locate the file mimeapps.list click open and edit it.

Alternatively open a terminal and type
```
gedit .local/share/applications/mimeapps.list 

```
edit it then save.

---

### Post by Evil Wayz on 2015-01-09
That appears to have done the trick, thank you!

---

