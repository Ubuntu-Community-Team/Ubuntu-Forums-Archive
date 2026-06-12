---
title: "Computer hangs past login screen"
date: 2007-07-10
forum: General Help
---

### Post by sonic167 on 2007-07-10
Hi all,

I've been using Ubuntu on my old AP500 for years and 7.04 for few months now, and all has been working fine until a first ever crash last weekend and a forced hardware shutdown.

This was following installation of the regular latest "System Updates" and a short Firefox session.

The problem now is that after booting and login screens comes up, the system hangs and the mouse cursor no longer moves after about 10-15 seconds.

When able to type in username/password quickly enough within those 10 seconds, I can get passed the login screen, but then it freezes quickly and I don't get to see the "splash window" showing how Nautilus, and other things are loading.

As you can see I don't know the technical terms...

I tried the "recovery" mode, and all seems to start and boot ok. No major (or even minor) errors I can see.

Bottom line, I can't login anymore, and I have to type this from Windows 2000 :mad:

Can anybody help me troubleshoot this?

Thanks,

Vince.

---

### Post by halfB on 2007-07-10
Vince
I am having the same problem: same message when trying a "regular" boot and in safe mode.  I tried a knoppix live cd boot and looked at my root partition and it is full.  Not sure how that happened.  I also do not know where to go from here.  How do I expand my root partition without toasting my setup??
Some folks have had this error and corrected things by changing their boot splash screens or their themes.  I do not think that is my problem.
Will follow along with you Vince.  All I can say is you are not alone.  I hate having to go back to my xp boot.
Eric HalfB

---

### Post by halfB on 2007-07-10
Vince
Here is one of those :this is what worked for me: notes.
I went to login screen and chose login to terminal screen.
In the terminal screen I entered     sudo aptitude clean
This allowed me to clean out enough of my root partition to now boot to safe mode.
In safe mode my root partition was now listed at 95% full instead of the 100% 
I deleted some programs and files without much effect.
It was time for another automatic update which I relucctantly took. 7 files/programs updated.
Afterward I checked and my root drive is now 48%full.
So this worked. Don't know exactly why.  
Good luck.
Eric HalfB

---

### Post by halfB on 2007-07-10
Vince
As I read your note again I see that your problem was different than mine.  I was getting an error message saying I had logged in for 10 seconds and then it would not boot any further.  
Sorry, I am unable to help with your specific issue.
Eric HalfB

---

### Post by sonic167 on 2007-07-11
Thanks Eric for the suggestions.

It does look like a different problem. My /boot has 50Mb. free and my user's home drive has plenty too.

When the login screen comes up (and the login chime!), during the next 10 seconds I hear the (loud) hard drive going crazy, then when it stops the computer is hung.

I tried the recovery mode to look around, but didn't see anything special. Boot seems to be ok, and everything loads fine.
I tried creating another user, but still can't login. It doesn't sounds user specific.

Can anybody describe what the system is doing after the login screen and chime come up?

Thanks,

Vince.

---

