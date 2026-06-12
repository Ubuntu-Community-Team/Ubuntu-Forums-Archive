---
title: "How to remove Smb4k autostart?"
date: 2008-03-16
forum: General Help
---

### Post by DavidOFF on 2008-03-16
Hi,

first post coz I always found answers to my questions in forums until today! I'm using Ubuntu Studio 7.10 and once i installed Smb4k and made it autostart in menu>system>preferences>sessions then decided to remove the autostart so i unticked the box under the tab "startup program"... but smb4k still autostarts! So I removed it from the list, made sure I unticked "automatically remember running applications when logging out" in case, even verified that Smb4k doesnt appear in /home/username/.config/autostart. But still, it autostarts everytime I log in. I can also see it in "current session" tab, please see attached (zipped) pic.  Am I missing something?

Many thanks
DavidOFF

---

### Post by alenis on 2008-04-02
Maybe you already found a solution.I had a similar problem with Thunderbird. I wanted it to autostart and I added an entry to the "sessions" dialog box. Then I changed my mind and I removed it but Thunderbird kept autostarting at the beginning of each gnome session. I solved the problem editing the 
~/.gnome2/session file, removing the line where "thunderbird" appeared and renumbering the following lines. I cannot guarantee that doing that is safe and works always, but it worked for me...

---

