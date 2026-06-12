---
title: "My Torrent Client works in XP but none work in Ubuntu PLEASE HELP"
date: 2007-11-27
forum: General Help
---

### Post by the-razors on 2007-11-27
I am attempting to move from XP to Ubuntu.  

I had been using Utorrent in XP and felt comfortable with it, and got good up and down speeds.   I need the ability to set speeds according to a schedluer and have tried both KTorrent and Deluge.  Ktorrent will only give me 1/8th of the speed that i should have (both up and down)  and Deluge will download great, but again gives me almost no upload.  

I tried to install Utorrent in wine, and I believe that I was able to get it installed correctly, but when I click in a torrent in firefox, the popup window does not give me the option of opening with Utorrent.

I REALLY WANT TO GET AWAY FROM MICROSOFT (THE GREAT SATAN) BUT I ALSO MUST BE ABLE TO TORRENT - Is there a setting in Ubuntu that is blocking me somehow? My router is wide open, and I have a public IP - I GOT GREAT SPEEDS IN XP USING UTORRENT SO WHY CANT I IN UBUNTU?

PLEASE HELP

Alan

---

### Post by Znort_Ubern00b on 2007-11-27
I know i may be teaching granny to suck eggs here, but did you ensure you encrypted data in ktorrent...it sped up my dow/up speeds no end...also you may need to sort settings in firestarter(if you have installed it) to allow traffic through the ports)

---

### Post by the-razors on 2007-11-27
No, I didn't try encrypting data, I noticed that Deluge defaulted to encryption, but KTorrent didn't - I will give it a try.  ALSO I have never heard of firestarter, so unless it came with, and is on by default in, Ubunutu I don't have it installed. 

 - Thanks for the help I'll give it a try

Alan

---

### Post by emwine on 2007-11-27
It's easy enough to get Firefox to run uTorrent, create a script in ~/bin, say "utorrent"

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/uTorrent/
wine utorrent.exe "$@"

```

Make it executable--```
chmod 755 utorrent
```

Then open a torrent in Firefox, choose "open with", and select your utorrent script.

There is a wealth of information about running uTorrent in linux with wine.  Here's a  [Google link]("http://www.google.com/search?q=utorrent+linux+firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") for more FF/utorrent/linux options.

---

### Post by TidusBlade on 2007-11-27
I am using utorrent in WINE perfectly, but since I have switched to Deluge, I never looked back. Ktorrent is also great. You can also try Azureus, Bittornado and Transmission, they are all found in the repos I beilieve, but Azureus is really bloated so I Dont know...

---

### Post by the-razors on 2007-11-27
I would love to use Deluge, or Ktorrent - both of which look good but like i said before _I just can't get them to work_. 

Azerus was my first client and I hate it - When I have enough money to buy a machine JUST to run a torrent client I may consider using it.  

So if I just COPY the scripts above into the terminal the I should be able to select "Open With - Utorrent" ??

I am not computer illeterate, but I AM pretty much a Linux Noob - does anyone have suggestions / reccomendation on books that teach newbies the basics of Linux?

---

### Post by TidusBlade on 2007-11-27
You can also cd into the directory where utorrent is located and type "wine utorrent.exe"

---

### Post by the-razors on 2007-11-27
"You can also cd into the directory where utorrent is located and type "wine utorrent.exe" 

- Won't that just start Utorrent ?  I can get it started through the GUI, but even with it RUNNING when I click on a torrent it doesn't give me the option of opening the torrent file with utorrent.

---

### Post by emwine on 2007-11-27
> **the-razors said:**
> So if I just COPY the scripts above into the terminal the I should be able to select "Open With - Utorrent" ??

I am not computer illeterate, but I AM pretty much a Linux Noob - does anyone have suggestions / reccomendation on books that teach newbies the basics of Linux?

No.  I made assumptions about your experience level which were wrong.  There are lots of ways my earlier advice could go awry--  you may have installed uTorrent elsewhere, you may not have a ~/bin directory, etc etc.  Since I'm not writing a HOWTO, I have to assume you can get it working if some of those conditions are true.

Basically you create a script (a file that will run uTorrent), and tell firefox to always invoke that script when it encounters a .torrent file.

---

### Post by the-razors on 2007-11-28
I have discovered that if I "Save" instead of "Open With" torrent files I can then manually drag and drop them into the main window of Utorrent to get them working.

I am still amazed that Utorrent in windows or in linux give me 90 KB + upload and download and neither Deluge nor Ktorrent worked.

ANYWAY, THANKS FOR ALL OF YOUR HELP

Alan

---

