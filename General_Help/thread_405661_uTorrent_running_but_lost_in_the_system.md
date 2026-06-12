---
title: "uTorrent running but lost in the system"
date: 2007-04-10
forum: General Help
---

### Post by ethidda on 2007-04-10
So I ran uTorrent with ```
alltray --icon blablabla.png wine /home/ethidda/.utorrent/utorrent.exe
``` but no tray icon shows up. However, I can see in my gnome thing that the upload rate is going at about 350kB. I can also see utorrent.exe in my when I do top. Additionally, when I ask for a new instance of the wine utorrent command above, a tray icon shows up to say that it is already running...

I tried to killall utorrent.exe, and in top it adds <defunct> to the end of it without really killing it. Even when I restart, it's there! Help, any ideas on how I can find it again/restart it? Thanks!

---

### Post by josephus on 2007-04-10
i think you need to kill the wineserver.

a defunct process is killed but it remains there for bookkeeping purposes because the parent process still exists.

---

### Post by pingpongboss on 2007-04-10
i'm not sure if this tip will help in ur situation, but whenever utorrent misbehaves for me, I always delete the settings.dat file for it (~/.wine/drive_c/windows/profiles/<username>/Application Data/uTorrent/settings.dat   [ or something like that >.> ]) and it almost always runs correctly when i start it again. 

good luck

---

### Post by ethidda on 2007-04-10
Thank you both so much! I killed the wineserver and then deleted all the data files in the fake c drive, and restarted it and now I finally have access to the gui again. :)

---

### Post by pingpongboss on 2007-04-11
sweet! glad i was able to help. You should also know that if you run uTorrent with wine, you can use its own tray icon implementation. Is there a particular reason why you're using alltray?

---

### Post by stuffradio on 2007-04-11
don't think I had this issue... when I was running uTorrent and things like winamp it stays in the tray at the top

---

