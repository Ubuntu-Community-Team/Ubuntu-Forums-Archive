---
title: "Three problems with Ubuntu 8.04"
date: 2008-05-02
forum: General Help
---

### Post by javi0084 on 2008-05-02
1. Sound stops working if I suspend the PC and bring it back, it will only work if I reboot.

2. Firefox 3 Beta 5 crashes frequently. Did it again this morning and now all my bookmarks are gone. Every time I start Firefox, it tells me it didn't close properly and wants to know if I want to start a new session or resume, I DO close it properly. Can I salvage my bookmarks for both user profiles of the PC and install the last working version of FF?

3. This happened ever since FF crashed this morning: If I click the icon that brings up the window to shut down, suspend, log off, hibernate, etc. my task bar at the top will disappear and nothing happens. I don't know what to do except press and hold the power button to shut down.

All this started happening when I upgraded from 7.10 to 8.04 (big mistake BTW).

There are more but these are the top 3 right now.

I appreciate any help.

---

### Post by janfsd on 2008-05-02
Maybe you got a profile problem. Open a terminal and run:
```
firefox -ProfileManager
```
and check if you have got several profiles, if yes, select one and save the bookmarks and so on.

---

### Post by c4v3m4n on 2008-05-02
Yeah, i would definitely say that upgrading to hardy heron right now is not a great idea.  I'm holding off until firefox is stable and hardy is just working better.

---

### Post by ACMiller on 2008-05-02
With regards to the ff3 problem, it sounds like it might be better to go back to ff2 (do this with synaptic, it can't be done with add/remove programs). Problem is ff3 profiles aren't compatible with ff2 (even though ff2 tries to use the ff2 profile), and so when you run ff2 you won't be able to install addons etc. So: go to /home/username/.mozilla/firefox and delete or rename profile.ini, then start up ff2 and it will create a new default profile. 

As for salvaging the bookmarks: You can copy your bookmarks into the new profile's folder that has just been created by ff2 (also in .mozilla/firefox) by copying the bookmarks.html file from the old profile's folder into the new one. When you start up ff2 next your bookmarks should all be there.

Does that make sense? Hope so. Sorry I can't be much help with you other problems.

---

### Post by javi0084 on 2008-05-02
OK, I have two users for Ubuntu, where can I find the bookmarks for "user2"? I'm more interested in saving those bookmarks than saving the bookmarks for "user1". I remember for user1 I ran some sort of command in terminal that copied all the bookmarks in the home folder, I just don't remember what that command was.

---

### Post by Ender305 on 2008-05-02
I don't know about a command buy you can copy ~/.mozilla/firefox/[random numbers].backup/bookmarks.html to the desktop, and then you can put it back in the correct folder once you downgrade

---

### Post by javi0084 on 2008-05-02
Bad news. I un-installed FF3 and installed FF2 but all I get is "Starting Mozilla Firefox" on the bottom then nothing, it just disappears.

I tried installing Opera to get on the internet but Synaptic doesn't list it. sudo apt-get install opera will give me an error saying something about being unable to unlock a file, "maybe a process is using it?" or something along those lines.

I tried launching Google Earth and got nothing, no errors messages or anything. Almost as if I don't click anything.

So because all of this and the other 2 problems above I decided it's just best to make a fresh start with Ubuntu 7.10. There goes half my weekend :( I spent countless hours tweaking 6.10.

Thanks for your help.

---

### Post by greengrocer on 2008-05-03
> There are more but these are the top 3 right now.

You should see how badly Xine works in Ubuntu 8.04, and how you cannot auto play a DVD with anything other than Totem *vomit* (you can try to work around this but its not pretty).

---

### Post by greengrocer on 2008-05-03
> I tried launching Google Earth and got nothing, no errors messages or anything. Almost as if I don't click anything.

Oh yes, thats right, Google Earth would not work on Hardy Heron unless I ran it with sudo.  That was pretty dodgy too.

---

