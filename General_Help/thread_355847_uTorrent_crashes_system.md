---
title: "uTorrent crashes system"
date: 2007-02-07
forum: General Help
---

### Post by kextyn on 2007-02-07
I'm running 6.06 on a dual P3-800 machine and it will freeze up every single time I load up uTorrent under Wine.  I made sure I am using the latest version of Wine but I'm also using the latest beta of uTorrent which could be the problem.  Sometimes it locks up right away, other times it will be happy for 5-10 minutes before locking up.  Usually if it's not right away it will lock up everything but the mouse and I can still move it around but not click on anything for another minute or so before it eventually locks up as well.

I have looked in all the relevant log files that I'm aware of (syslog, xorg, etc) but I don't see anything that pertains to this problem.  Is there another log somewhere I'm missing?

The reason I am using the beta of uTorrent is because I require the WebUI.  This PC does nothing but handle my torrents and has nothing but a power and ethernet cord plugged in to it.  I use the WebUI from across my LAN and across the internet.  I tried Azureus with the WebUI plugin but didn't like it very much (kept having issues with the script to start it and stop it on system startup and shutdown as well.)  Are there any other alternatives?

---

### Post by CPtAJ on 2007-02-07
You could run rTorrent, or some other terminal-based bittorrent client, through SSH for remote access. Can't think of any other alternatives though...

---

### Post by bionnaki on 2007-02-07
sudo apt-get install ktorrent

---

### Post by CPtAJ on 2007-02-08
Oh damn, you're right. I didn't know ktorrent had a webUI plugin. kextyn, he's right, just use ktorrent.

---

### Post by TheRealEdwin on 2007-02-08
Forgive my ignorance but can I run ktorrent in gnome (normal ubuntu)? I looked on the wiki and didn't see anything mentioned about it.

---

### Post by bionnaki on 2007-02-08
yes. you can run whatever application you want.

---

### Post by kextyn on 2007-02-08
Thanks guys,  I'll look into ktorrent.

---

### Post by kextyn on 2007-02-08
What kind of functionality/features does utorrent have that ktorrent or rtorrent lack?

---

### Post by CPtAJ on 2007-02-08
Heres a full comparison of all major clients:

[http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software)

---

### Post by kextyn on 2007-02-08
Wow, that's a very nice comparison there.  Thanks again.

---

### Post by kextyn on 2007-02-09
Ok, it seems like I'm having the same issues with kTorrent.  I was testing it in Virtual PC and after the recent update was fixed I did a fresh load of Edgy on my 2x P3 800MHz system and installed kTorrent 2.1.  With no torrents loaded it keeps crashing withing a couple minuts of opening the program.  I'm running memtest on it right now but so far no errors.  Which log(s) should I look in for a possible explanation?

---

### Post by kextyn on 2007-02-10
Well I didn't have any errors in memtest.  I didn't see anything in the logs.  This is getting really frustrating.

---

