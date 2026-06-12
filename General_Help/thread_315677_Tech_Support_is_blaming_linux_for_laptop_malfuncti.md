---
title: "Tech Support is blaming linux for laptop malfunction."
date: 2006-12-09
forum: General Help
---

### Post by Bastanteroma on 2006-12-09
My laptop (hp dv2xxx) began to malfunction a few days ago and tech support insists that I eliminate linux as the culprit before shipping it to them.  But I wiped Windows and installed Edgy first thing after I bought it a month and a half ago, so I can't compare.  

Until a week ago it worked perfectly, suspending and everything, except that when shutting down the usplash image, using the nvidia binary driver, would flicker and jump around a bit.

Now it turns itself off suddenly, with no warning.  And when I restart the screen doesn't light  up.  Or it shuts down on command, but the screen is dead when I start it again (no bios HP logo or anything).  Taking the battery out and holding the on button for about 30 seconds seems to allow it to reboot properly.

Tech support (eager to blame Linux, of course) suggested that maybe the os isn't shutting the computer down correctly, creating static on the motherboard, possibly related to the distortion in the usplash image.  The other suggestion was to start using a surge protector, which I've done, and this seems to have possibly fixed the problem.

Which leaves me with two questions.

First, if this happens again with a surge protector could something in ubuntu be at fault or does this sound like a hardware problem?

And if a surge protector solves the problem, is it fixing faulty hardware?  Are laptops so sensitive that people often need to carry surge protectors?

If this does sound like a hardware problem I'd love some arguments to put to tech support.  Reinstalling Windows will require ordering disks and will be quite a pain.

---

### Post by highneko on 2006-12-09
You say you're using Ubuntu so I'll assume you're using gnome. Try -> System -> Preferences -> Power Management -> and try making it not sleep or do any power saving thing. Search with adept for some laptop related packages maybe?

You say it randomly did this, but could you have left it alone? Did it randomly shut off when you were using it?

---

### Post by Bastanteroma on 2006-12-09
To clarify, when I say it shut down suddenly I meant in the space between one key click and the next all the lights went dead.

It didn't shut down, it died.

---

### Post by budgie9 on 2006-12-09
Personally I would not think it is Ubuntu itself. Perhaps you should try an older Nvidia driver and see if the same happens. I have seen some strange things with computers but yours is a wierd one I must say. I will be watching this thread with much interest.
I think there is a problem with the computer itself, maybe the screen, but that works at times. Maybe the screen driver chips. 
Static is a problem for some computers and you should be careful when using a computer when there is a lot of static about. Tales of burnt out computers are not that rare, so are holes in the keyboard keys.
I certainly have found a lot of support personal are very reluctant to do anything but deal with the latest from Msoft. Disapointing to be honest, but then again a lot of these guys don't even know what a computer is capable of doing. They only know what the screen they have directly in front of them tells them.

---

### Post by riven0 on 2006-12-09
Did you notice any overheating before your lappy died?

---

### Post by koenn on 2006-12-09
I agree with tech support on this one. 
HP sold you a laptop with Windows (I presume, as you say the first thing you did was **wipe** Windows). So whatever warranty, after sale support, or whatever that came with the deal, probably does not apply if you've modified the product you bought by wiping the OS and replace it with an other. 

HP sold you a laptop with Windows, and with drivers that they know will work with the hardware they sold you. As you replaced the drivers (you had to because you replaced the OS), they can not know that this won't have ill effects on that hardware.

Eliminating pobable causes and reverting to a know, documented state (in this case : a HP laptop with Windows on it) is a normal troubleshooting procedure, and a efficient one. 

If HP sold you a laptop with Windows, it probably came with a restore CD so restoring Windows shouldn't be that hard, and it will give you (or the guys from Tech Support) the change to eliminate the OS as a cause of the problem, if indeed it is a hardware problem. 


Other than that, it may be worth reviewing some power safe settings and see if you can make the problem go away.

---

### Post by Bastanteroma on 2006-12-11
Sad to say the surge protector didn't fix things.  But it turns out the screen isn't entirely off, it's just super super dim, like the backlight isn't on at all.

I'm sympathetic to tech support.  They want me to run diagnostics and such in windows, and I can't, and they're set up to service a bundled product, not just a piece of hardware.  Problem is, the 4th restore dvd of the 4 I burned isn't being recognized by the restore program.  I didn't mean to vilify them, I just hoped that someone might be able to explain with some confidence that this looks like a hardware problem, not something caused by an os.

But no overheating, no signs of failure before it happens.

Before sending it back, I guess I'll put another distro on and run it with the nv driver.

---

### Post by K.Mandla on 2006-12-11
I think that's what I would do. Try a live CD if you don't want to go through a full install. But distro-hop for a little and see if the problem persists.

---

### Post by majoridiot on 2006-12-11
before you wipe it, try a test without booting anything.  boot into bios 
setup and just let it sit... all day if need be.  if it reboots itself or
exhibits the screen problems you describe, then it is certainly a hardware
problem.  if it doesn't, it is possible indication of os conflicts and you 
can try another distro, etc.

if all else fails, install an XP cd from a friend or download one from p2p
and register with your key (which is totally legal), then download and 
install the latest mobo drivers and test from there.

---

### Post by technodigifreak on 2006-12-11
> **Bastanteroma said:**
> Sad to say the surge protector didn't fix things.  But it turns out the screen isn't entirely off, it's just super super dim, **like the backlight isn't on at all.**


You nailed it!  LCD's occasionally have backlight issues.  When it first boots, does your POST show correctly on the screen or does it not even display that?  If it doesn't even display that, then it is most definately a Hardware issue since Linux OR Windows wouldn't have been able to affect any configuration changes at this point in the boot process (because neither of them are on yet!).  If the POST displays correctly, insert your live CD and run that for a while and see if you have the same issue.  If you have the same issue, it's hardware related.  If you don't have the same issue then it's an issue with your installed OS.

Let us know what you find out.

---

### Post by igknighted on 2006-12-11
I had the same laptop with the same issue... if your backlight goes, this is very bad news.  The cost to replace one of these (unless you do it yourself) is around 400$ US, which in my case was about the value of the whole computer, so I ended up scrapping it.  Do a few things first before you despair, however.

1) check your /var/logs for any errors related to the crashes

2) check the vertical and horizontal refresh ranges on your monitor.  Make sure that the display settings you use are within those ranges.

---

