---
title: "Helping my friend switch to ubuntu..."
date: 2007-05-28
forum: General Help
---

### Post by Ripfox on 2007-05-28
My friend is computer challenged, but I got him going on his FIRST pc with ubuntu running gnome. He would like my help when he does small mistakes like removing things from his panel ect...

Is there an EASY way I can set it up so that I can control his desktop from time to time and avoid LONG phone calls, I feel like a 24/7 tech support here :)

Thanks

---

### Post by smoker on 2007-05-28
do a search for VNC in synaptic package manager, i believe there are a few choices that will do what you want, 

best of luck

---

### Post by Ripfox on 2007-05-29
Problem is I know nothing about VNC. I have been looking, but sounds complicated.

I keep truckin'...

---

### Post by Ek0nomik on 2007-05-29
Ubuntu comes with VNC availability right out of the box.

All your friend has to do is:

System/Preferences/Remote Desktop

He just needs to enable it, and setup a password if he chooses, and he is completely set on his end.

Now, for your part, open a terminal:

```
sudo aptitude install xvnc4viewer
```

Once that is finished, you only need to run a single command to connect to him:

```
xvnc4viewer xxx.yyy.zzz.vvv
```

Where xxx.yyy.zzz.vvv = **his** IP.

If he doesn't know his IP he can find it easy enough by searching:  "What's my IP?" on Google.

//////////

Now, I will say, I don't personally find the build in remote desktop (vino is the software) to be all that great.  I find it to be buggy at times.  I don't use VNC currently, but when I did I was on Edgy, and the two following links might help if you can't stand vino.

[http://ubuntuforums.org/showthread.php?t=122402&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=122402&highlight=x11vnc)
[http://ubuntuforums.org/showthread.php?t=363236&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=363236&highlight=x11vnc)

I personally have used the second one listed there back when I was running Edgy.

I don't know if any of these work for Feisty, or at least yet, but you can check it out.

Good luck!

---

### Post by Ripfox on 2007-05-29
Thank you lots that was EXACTLY what I needed.

---

### Post by irish_flu on 2007-05-29
Good luck, Ripfox.

If it makes you feel warm & fuzzy, I recently did the same thing for a friend (who had similar computer experience to your friend) and he loves his Ubuntu box now.  :)

---

### Post by Ek0nomik on 2007-05-29
If you have more questions feel free to ask Ripfox.

---

### Post by Ripfox on 2007-05-29
Thanks again, and I'm fairly positive I will....heheh

---

### Post by Ek0nomik on 2007-05-29
Feel free to PM me or respond to this thread.

I am going to bed, but I might have time to check back in on you tomorrow at work.  ;)

---

### Post by Ripfox on 2007-06-02
ok it just blinks...

---

### Post by Ripfox on 2007-06-02
I let it sit for awhile, still no action...whats it supposed to do?

---

### Post by steveneddy on 2007-06-02
> **Ek0nomik said:**
> 

If he doesn't know his IP he can find it easy enough by searching:  "What's my IP?" on Google.


Good luck!

Try [ipchicken.com]("http://www.ipchicken.com/")!

---

