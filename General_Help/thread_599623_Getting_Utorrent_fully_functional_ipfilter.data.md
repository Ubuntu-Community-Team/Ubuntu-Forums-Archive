---
title: "Getting Utorrent fully functional/ ipfilter.data"
date: 2007-11-01
forum: General Help
---

### Post by 449 on 2007-11-01
I need help getting Utorrent fully functional under Ubuntu 7.10. My current problems are the following:

-when minimized, then maximized only the very top part of the window shows up and the rest just shows the desktop, I have to double click on the top tray icon to get it up.

-Ipdata.filter doesn't load, I put it in c:\windows\profiles\$USER\ folder. Instead I get to messages in the logger tab of Utorrent. "UDP port bind() failed" and "error opening Windows firewall: 0x80040154."

-I have to manual drag .torrent into Utorrent to get them to download. I also can't figure out how to make Utorrent my default torrent program for Firefox, does not give me the option in preference.  

I have the lastest version of wine installed emulating windows xp. Any help on these issues would be greatly appreciated. Thanks.


ps, quick offtopic question: how do you change the default programs, ex. if I wanted video files to be opened with VLC player. Thanks Again.

---

### Post by minus198 on 2007-11-01
> **449 said:**
> 
ps, quick offtopic question: how do you change the default programs, ex. if I wanted video files to be opened with VLC player. Thanks Again.

Rightclick on the file you want to open -> Properties -> Open With -> Add -> VLC -> Add -> Set it to default. -> Your done :)

And about that with uTorrent min/maximize issue: Everyone has that issue. The same thing about having to manually load the file into uTorrent. 

I recommend using Transmission instead of uTorrent i linux.

---

### Post by 449 on 2007-11-01
> **minus198 said:**
> Rightclick on the file you want to open -> Properties -> Open With -> Add -> VLC -> Add -> Set it to default. -> Your done :)

And about that with uTorrent min/maximize issue: Everyone has that issue. The same thing about having to manually load the file into uTorrent. 

I recommend using Transmission instead of uTorrent i linux.

I think I'll give Transmission a try ,but how do I get ipfilter.data working?

---

### Post by 449 on 2007-11-01
bump ](*,)

---

### Post by 449 on 2007-11-01
> I think I'll give Transmission a try ,but how do I get ipfilter.data 

Hate to bump ,but it got pushed to 4th page pretty fast.

---

### Post by zhinker on 2007-11-04
When I was installing utorrent via Wine I just checked off the box asking if I wanted to make utorrent my default torrent search engine and the next time I tried downloading torrents in firefox Utorrent was the first option in the 'open with' drop down box.

---

