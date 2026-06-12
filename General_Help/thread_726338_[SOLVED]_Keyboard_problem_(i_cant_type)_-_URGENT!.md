---
title: "[SOLVED] Keyboard problem (i cant type) - URGENT!"
date: 2008-03-16
forum: General Help
---

### Post by piousp on 2008-03-16
Well hello,
I'm going straigh to the point:

My keyboard was working normally until yesterday. I left the computer on all the night, and when i woke up, the keyboard wasn't working. I thought that a restart would solve the problem, but it didn't.
Just to give you an example of what's happening:
° If i open, say, openOffice, i cant type anything,
° If i open a terminal, same, i cant type.
I thought the something in my xorg.conf was wrong, but as far as I can see, it is healthy.

Out of desperation, i tried to restart X with the keyboard (Ctrl + Alt + Backspace) and it worked!
After i log on again, the problem was still there.
After that, i tried to open a TTY with Ctrl + Alt + 1, and again, that one works.
To my surprise, the keyboard works perfectly fine in the TTY, but once i return to X, it stops working.

I REALLY NEED to solve this issue quickly.

Configuration:
Dell Inspirion 6400
Ubuntu Gutsy

P.S. Its the same whenever i try to use the laptop's keyboard, or an USB one.
P.S2. I'm on a live cd right now, and excuse my bad english.


Thanks in advance!

---

### Post by days_of_ruin on 2008-03-16
Hmmm.
Don't know but try pressing escape before typing because there are some keyboard
shortcuts that can mess that up.

---

### Post by piousp on 2008-03-16
OK, i'm gonna try that

---

### Post by unutbu on 2008-03-16
This is a shot in the dark, but did you try going to the Gnome panel and clicking System>Preferences>Keyboard>Layouts, and selecting your preferred layout as default?
Also, under the 'Keyboard' tab there is a place to type. Do you see anything there?

You might also want to try the following: Press Ctrl-Alt-F2 to go to a virtual console.

```

echo "setxkbmap us" | tee -a ~/.profile

```

This will run the command setxkbmap after you log in to X. It should set your keyboard mapping to qwerty.

---

### Post by piousp on 2008-03-16
The System>Preferences>Keyboard>Layouts looks fine to me. Also, in the textbox area, again, i cant type there.

I was thinking in copying the xorg.conf from the liveCD and use that one, to see if it helps in anyway.

If it doesn't, i'll try ```
echo "setxkbmap us" | tee -a ~/.profile
```

Thanks for helping me out. Back in a few.

---

### Post by piousp on 2008-03-16
Nope, still i cant type :confused: :( :cry:

Ok, i did a back-up of my files, just in case.
:S i REALLY need my keyboard back.

---

### Post by piousp on 2008-03-16
Any other ideas??? I'm out of time

---

### Post by sports fan Matt on 2008-03-16
I had a similar issue a few weeks back..All I had to do is Choose which keyboard I had and all was well..:)  Hope this helps...:)

---

### Post by piousp on 2008-03-16
Well, i guess i'm going for a clean install, since i dont have much time. I'll reboot again, try the keyboard again, check the forum one last time, and after that, reinstallation.

---

### Post by piousp on 2008-03-16
Thanks everyone. I  found the problem.

Let me explain:

I was checking again the System>Preferences>Keyboard
I reassinged my layout and all that.
This is dumb, i know, but i clicked the button to left of the close button (cant remember the name in english :lolflag: ) and there, i went to filters and I notice that the "Slow keys" checkbox was checked.

I guess you can imagine the rest of the story.
What i'm trying to figure out now, its how the heck did the "slow keys" thing got on. :confused:

Anyway, thanks for your help. Viva Linux!

---

