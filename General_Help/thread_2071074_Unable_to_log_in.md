---
title: "Unable to log in"
date: 2012-10-14
forum: General Help
---

### Post by elkingrey on 2012-10-14
Hello,

I've been running Ubuntu for about two years on my old desktop. I'm running 12.04 currently. There have been some issues creeping up for the past few months that I've ignored.

When starting the computer I would get a warning about low battery voltage and pressing f1 to continue or f2 to fix or something rather. Anyway, I ignored and ignored that problem. Eventually, my computer would suddenly go into sleep mode when I was using it. So, I decided to try and fix the problem. I did some studying on line and the best diagnosis I could find was that there is a small battery on the motherboard that needs to be replaced. It is an 8 year old computer after all so I figured that was a good bet. 

I replaced the battery to the motherboard and when starting up I no longer got the low battery voltage problem. Instead I got a new problem that seemed totally unrelated. I can't remember what it was but it also presented itself during startup and offered me the choice between f1 and continuing or f2 and diagnosing. Again, I would choose to continue.

The problem of the computer still going into sleep mode randomly persisted, though. Another thing I should add is that my computer was set up so that it could not be restored from sleep mode. So, every time it went into sleep mode I would have to do a hard shut down. 

Doing more studying online I learned that that setting is in the BIOS. So, I went into my BIOS to allow myself to restore sessions from sleep mode without having to do a hard shut down. Another problem had happened though, possibly as a result of me playing with my voltage battery? I don't know, but the problem is that my entire BIOS was locked. I never set any password to lock the BIOS so I didn't know the password to unlock it, which would allow me to change the sleep mode settings. 

So, I gave up on that for the time being. I would just continue to suffer with a computer that dies on me randomly until I got a new computer. 8 years is a life well lived anyways. I had backups of things just in case the computer died for good.

Well, eventually it did die for good, although I think it is only mostly dead. Now, when I fire up the computer it will bring me to my account log in. When I type in my password and hit enter, it will attempt to log me in, but instead a black screen with some sentences come up briefly, so quickly that I do not have time to read them, and then it returns me to the log in prompt again. It refuses to log me in, almost as if my password is no good.

Unfortunately, my backup was a little old, and there are just a few more files I'd like to extract from that computer if I could. I really just need a few more minutes of time on that computer and then I'm done. 

Can anybody help me to log in and retrieve my files?

---

### Post by Wim Sturkenboom on 2012-10-14
When at graphical login prompt, press <ctrl><alt><Fx> (x being 1..6); you will be taken to a console where you can login. <ctrl><alt><F7> will take you back to graphical environment.

The lines of text that you see is (more than likely) remainders of the bootup, nothing to worry about.

From the console, you might be able to fix your login issue. I'm however not the person to really help with that.

---

### Post by Meschi on 2012-10-14
If your system falls back to the console at the boot process and you see the login prompt it could have happened that your keyboard layout has changed to the american one (not sure if its really american or something else). However the characters "y" and "z" may have changed their position on the keyboard. Maybe your pw contains these chars and you are not able to see the wrong typing?
If you have access to your system again one can look for solutions concerning the graphical interface...

---

### Post by mardybear on 2012-10-14
Hi elkingrey.

Your system is not dead yet. 8 years is just middle-age. I try to keep my systems running as long as possible - frugal choice and helps out the environment. Dead systems make me sad...try to keep it running forever :)

Reset the BIOS. It will undo all the tinkering and give you a fresh start:
[http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm](http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm)

As already suggested, the non-graphical login should allow you to access your system. If you can still complete a non-graphic login, then maybe you just have an X window system problem.

If a non-graphical login doesn't work, then just boot/run your system from a liveCD (set BIOS to boot from CD using Ubuntu live or Puppy linux) to complete your file transfer/backup. Alternatively find a way to reset your Ubuntu password.

If you're able to get the system running again, you may want to temporarily disable all the power save features (sleep, screensaver, etc) until you know it's running stable/reliable.

mardybear

---

### Post by elkingrey on 2012-10-14
Thanks Wim Sturkenboom for your suggestions!

I was able to get console log in no problem. From there I was able to mount my USB and get the remaining files off of the computer that I needed.

Problem solved!

As far as saving the computer goes. Now that I've got everything I need off of it, I may give it an entirely fresh install from scratch. Then I can see if that fixes the other problems I was having. If so, great! If not, then I can either troubleshoot some more, or donate it.

Thanks for the help everybody!

---

### Post by elkingrey on 2012-10-15
> **mardybear said:**
> Hi elkingrey.

Your system is not dead yet. 8 years is just middle-age. I try to keep my systems running as long as possible - frugal choice and helps out the environment. Dead systems make me sad...try to keep it running forever :)

Reset the BIOS. It will undo all the tinkering and give you a fresh start:
[http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm](http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm)

As already suggested, the non-graphical login should allow you to access your system. If you can still complete a non-graphic login, then maybe you just have an X window system problem.

If a non-graphical login doesn't work, then just boot/run your system from a liveCD (set BIOS to boot from CD using Ubuntu live or Puppy linux) to complete your file transfer/backup. Alternatively find a way to reset your Ubuntu password.

If you're able to get the system running again, you may want to temporarily disable all the power save features (sleep, screensaver, etc) until you know it's running stable/reliable.

mardybear

Okay, troubleshooting the BIOS problem again, it won't let me result to defaults unless I unlock it first, and I haven't got any password. I also tried reseating the BIOS battery and that didn't work either. Everything is still locked.

---

### Post by elkingrey on 2012-10-15
> **elkingrey said:**
> Okay, troubleshooting the BIOS problem again, it won't let me result to defaults unless I unlock it first, and I haven't got any password. I also tried reseating the BIOS battery and that didn't work either. Everything is still locked.

Never mind. I found these instructions:

[https://support.dell.com/support/edocs/systems/dim8400/sm/syssetup.htm#wp1052625](https://support.dell.com/support/edocs/systems/dim8400/sm/syssetup.htm#wp1052625)

and that helped to clear the BIOS password. From there I was able to restore settings to default. 

Now I have a new problem, and that is that despite putting my CD ROM drive ahead of my hard drive in boot order, it fails to boot my Ubuntu installation CD.

---

### Post by mardybear on 2012-10-15
hi again elkingrey...

I'm glad you're still tinkering with your old system. You're gonna make a workhorse out of that old 'puter yet :)

Basic troubleshooting:

1. Recheck the BIOS to ensure it saved your changes (boot from CD-rom).

2. Does your laptop have more than one CD-rom or DVD-rom?

3. When you're using the computer, is the CD-rom drive able to identify/load a different/any CD?

4. Are you using a burned Ubuntu CD? Some older drives were not capable of reading a burned CD.

5. If you have an external or backup CD-rom, try swapping hardware to see if you have any better success.

6. Is your Ubuntu CD bootable (ie ISO image, not just a data CD)?

7. As you were tinkering with your CMOS battery/motherboard, reconnect all your CD-rom connections (power supply, both ends of the data cable) to see if this fixes the problem.

mardybear

---

