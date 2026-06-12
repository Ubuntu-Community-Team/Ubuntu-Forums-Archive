---
title: "Dash Button Made Crazy Graphics Error"
date: 2013-05-07
forum: General Help
---

### Post by Myst1234 on 2013-05-07
Hi everyone,

I recently upgraded to 13.04, but had a slew of problems so I created a bootable usb with 12.10 on it. Now it seems I STILL have issues. I love Linux but I'm about ready to smash the computer and say eff it. 

What I've noticed, SO FAR, is when i hit the dash button to search for an app, my screen went absolutely nuts, and now my menu bar on the left is pixelated to the point it is unreadable.

So what happened? And how do i fix it?

I was running 12.04 for like a year and almost never had an issue. All of a sudden I upgrade and it's like everything went to ****, what's going on?

I have done a few small things like installing zram, jupiter, medibuntu and ubuntu restricted extras, and changed my swappiness. Does ANY of this have to do with the problems I'm having? Or is Ubuntu and their sub par releases?

So confused and frustrated:confused::mad:

any and all help is greatly appreciated, I need my computer for work and it's close to useless for the past 3 days!!

---

### Post by hil4vitkutin on 2013-05-07
Hi there,

Have you installed any proprietary display drivers? Or changed any settings using tools like *CCSM *(CompizConfig Settings Manager)?
[FONT=arial]
If you have or haven't done any of the above, you can always try resetting unity...

[/FONT]```

[FONT=arial][FONT=courier new]sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity[/FONT]
[/FONT]
```

Does this graphics 'glitch' appear every time you are searching the Dash? Can you repeat it?

---

### Post by Myst1234 on 2013-05-07
No proprietary drivers, just a typical b43-fwcutter install because affter the fresh install of 12.10, I had no wireless

Yes it happens everytime, although sometimes more violent than others.

Your command produced this -

E: Unable to locate package reset
E: Unable to locate package /org/compiz
E: Unable to locate package setsid

---

### Post by hil4vitkutin on 2013-05-08
Oh! Sorry I made a foolish mistake typing those commands there. They were supposed to be on their own lines, not on the same... :oops:

(The post is now *fixed*, pelase try the commands again, executed separately)

---

### Post by Myst1234 on 2013-05-08
Ok, so uhh I have no idea how to even explain what happened when I entered

setsid unity

The terminal did a bunch of stuff, then started coming back with ERROR messages, then everything froze, and then (this is where it gets extremely strange) My screen went black, came back on with the messages of "stopping xxxx" like when you restart or shutdown your system, but it kept repeating "failed to idle on channel 1" then channel 2 and it kept repeating that, on top of the screen blacking out completely intermittently.

This happened for long enough to where I just shut off the laptop and restarted it manually. 

Now that it is back on it keeps telling me there are system errors.

---

### Post by Myst1234 on 2013-05-09
My graphics error has moved from the Dash Home button to basically everything. Not sure what to do.

---

### Post by 25tom on 2013-05-09
At this stage I would back up everything and do a clean install if possible... When you installed 12.10 from USB, did you check the image file for corruptions? If it was corrupted, that may well be the cause of these problems. Hope this helps :)

---

### Post by Myst1234 on 2013-05-09
My USB has 12.10 on it from UNetbootin, I don't think it would be corrupted, but I guess I will try again

---

### Post by 25tom on 2013-05-09
This should help you to check the image file for corruptions: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by hil4vitkutin on 2013-05-09
Yep, I would also recommend a clean install, as your system seems to have some "critical" errors... :/

---

### Post by Myst1234 on 2013-05-09
> **25tom said:**
> This should help you to check the image file for corruptions: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

thanks for this, one question though -

"First download the MD5SUMS file to the same directory as the iso"  -- How do I do this?

---

### Post by Myst1234 on 2013-05-09
I couldn't get the downloading and running through th terminal part to work, but I manually checked the hash with Ubuntu Hashes and it matched

---

### Post by 25tom on 2013-05-09
You don't really need to do that; personally, I'd follow the manual method and just visually compare the resulting hash with the one on the Ubuntu website for whatever .iso file you're using. Hope it works :)

EDIT: posted just a little too late :)

---

### Post by Myst1234 on 2013-05-09
Thanks everyone. I'll mark this as solved, although it wasn't really solved but rather Re-Did

---

