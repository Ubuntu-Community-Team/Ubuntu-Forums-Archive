---
title: "[SOLVED] Thunderbird2 in Gutsy crashes when viewing certain emails"
date: 2007-10-19
forum: General Help
---

### Post by tak1150 on 2007-10-19
Just installed Gutsy here. Just like most of you impatient geeks out there, I couldn't wait :)

I was using TB1.5 in Feisty and it worked great! I did try using 2.0 in Feisty and had SCIM problems. So I downgraded to 1.5. In Gutsy the TB in the repo is 2.0 by default.
I have not yet installed the language stuff (SCIM, etc) and I am not sure why TB is crashing.

It is not the theme problem either (I checked with the Human theme and it still crashes).

Here's what I get from terminal:
```
Segmentation fault (core dumped)
```

Anybody with insight / solution?

---

### Post by LanDan on 2007-10-19
sounds like an issue with memory addressing, but not sure if its hard or software

just in case to rule out the hardware option, how much ram and swap do you have?  can you run memcheck without problems???

---

### Post by tak1150 on 2007-10-19
Hi LanDan,

Thanks for replying. I have 756MB RAM.
So I think it's enough?

I just found a possible solution! I uninstalled "thunderbird" from Synaptics and installed "mozilla-thunderbird" (which also makes you install "thunderbird") from Synaptics. Then it worked! It is very strange...

---

### Post by LanDan on 2007-10-19
lol,

yeah your ram is enough, it was the swap i was worried about

---

### Post by shane2peru on 2007-10-19
Hey there TAK, just couldn't wait huh.  I have been using Gutsy for about a week now, I figured 5 days before release should be pretty stable.  :lolflag:   

I have had problems with this TBird issue since going to Gutsy.  I have found that if I just re-install it, it works fine.  I know that is not a good solution, but it works. I run ```
sudo aptitude reinstall thunderbird
```  It doesn't even download it anymore unless I run the clean command for aptitude.  :D  I think it has to do with appamrour or something of that effect.  I'm really not sure. It is annoying.  I have thought about downgrading to Dapper and quit messing up my desktop so much, but I'm too much of a geek, and love the cutting edge to do that!

Shane

---

### Post by tak1150 on 2007-10-19
> I just found a possible solution! I uninstalled "thunderbird" from Synaptics and installed "mozilla-thunderbird" (which also makes you install "thunderbird") from Synaptics. Then it worked! It is very strange...

Ok, actually the above solution did not work. I now have the same problem again. :(
What is wrong with you, TB2?

---

### Post by tak1150 on 2007-10-19
```
sudo aptitude reinstall thunderbird
```
above does work. But if I close Thunderbird and open it again, the same problemo...

---

### Post by LanDan on 2007-10-19
ok, some things you can try

1st check your ram, try to use the memcheck option available on the installation cd
2nd rename the .mozilla-thunderbird file in your home and start thunderbird again
(this is if you copied your old mail folder and there is some old extension/plugin thats bugging you)
3rd check your logs (dmesg syslog apport xorg)  might be a good start there in /var/log

---

### Post by p_quarles on 2007-10-19
I don't know if this will help, but I found that Thunderbird 2 was crashing every time an OSD notification popped up. I was able to fix it by simply turning off the notifications. I think this may be more related to KDE than TB, though, so it might not apply to you.

---

### Post by shane2peru on 2007-10-19
> **LanDan said:**
> ok, some things you can try

1st check your ram, try to use the memcheck option available on the installation cd
2nd rename the .mozilla-thunderbird file in your home and start thunderbird again
(this is if you copied your old mail folder and there is some old extension/plugin thats bugging you)
3rd check your logs (dmesg syslog apport xorg)  might be a good start there in /var/log

Oh, that was another thing I was going to suggest is that Lightning (the calendar) with Thunderbird and Gutsy doesn't work.  Mine is still installed and when I open it up it is fine, however the calendar doesn't display correctly.  I have read that it can cause it to crash too.  Just another thought that LanDan helped me remember.

Shane

---

### Post by tak1150 on 2007-10-19
Yes! Thank you guys! It is the extension!!!
Lightening is the cause here.

I have removed lightening and re-installed it through Add/Remove thingy. And now it works! :)
I'll give it a day or so to make sure everything is working and tag this thread as solved.

Thank you everyone for your help! :-P

PS I was hoping the "SCIM" problem would go away with the Gutsy / TB2 combination. Has anybody tried it yet? I suppose that's another topic for another thread, perhaps... I will make another thread for this SCIM topic for Gutsy.

---

### Post by michaelzap on 2007-10-23
Same thing happened to me. Lightning doesn't display properly, and some emaisl cause TB to crash when trying to view them. Uninstalling Lightning fixes the crashes (phew!), but is there any way to make Lightning work yet?

---

### Post by tak1150 on 2007-10-23
> **tak1150 said:**
> Yes! Thank you guys! It is the extension!!!
Lightening is the cause here.

I have removed lightening and[B] re-installed it through Add/Remove thingy. And now it works! :)
I'll give it a day or so to make sure everything is working and tag this thread as solved.[/B]

Thank you everyone for your help! :-P

PS I was hoping the "SCIM" problem would go away with the Gutsy / TB2 combination. Has anybody tried it yet? I suppose that's another topic for another thread, perhaps... I will make another thread for this SCIM topic for Gutsy.

Have you tried the above?

---

### Post by tak1150 on 2007-10-30
I have tried using TB2 with SCIM support for Japanese and it did not crash!
It does crash, however, if you hit the "Send" button in TB2 while you're in the Japanese entry mode. Anyhow, I now have a working system that lets you use SCIM!

I shall tag this thread "solved"

---

