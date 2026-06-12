---
title: "Windows XP Stops booting at mup.sys"
date: 2008-03-13
forum: General Help
---

### Post by Joshua on 2008-03-13
I'm not sure if this is the right place to post this, but I figured it might help someone.  On top of that, it's a bit of a "thank you" to Ubuntu for another way it's helped me out.

So I have an Averatec laptop with Windows XP and a couple partitions of Ubuntu.  I recently updated all the patches for Windows, but I don't know if that has anything to do with this.  I was shutting my computer down (from Windows) and it looked like it locked up, so I held the power button down to do a hard restart.  When it came back up, it wouldn't get past the Windows splash screen with that progress bar at the bottom of the screen.  So I tried "Safe Mode."  It listed what it was doing but it kept stopping when it got to loading the mup.sys file.

After doing lots of web searching I couldn't find anything that explained how to fix it.  So I booted into Ubuntu and tried to mount the Windows partition so I could do some tinkering with that mup.sys file.  In Ubuntu I got an error that said something about not being able to mount the Windows partition because it was marked with an unsafe shutdown.  It gave a command to force the Windows partition to mount, so I typed it in (with sudo) and it mounted.  After a restart into Windows again, everything booted fine.

Not sure why it worked, but it looks like everything is fine and it really saved me.  I hadn't been able to get into Windows for over a week.  Thanks Ubuntu!

---

### Post by Rio517 on 2008-05-20
Hi Josh, 

Did you ever figure this out.  I'm having exactly the same problem.  Right before the issue happened for me, Ubuntu updated my nvidia firmwar.  I'm wondering if it's related to that.

I'm freaking out!  So I hope you found a solution!  Thanks!

-Mario

---

### Post by Joshua on 2008-07-01
> **Rio517 said:**
> Did you ever figure this out.  I'm having exactly the same problem.  Right before the issue happened for me, Ubuntu updated my nvidia firmwar.  I'm wondering if it's related to that.

I know this is really late.  Hopefully, you aren't still having this problem.  I'm not sure if your problem is the same or not.  Most of the times I've had problems after updating the Nvidia Drivers, it has been due to having an xorg.conf file that doesn't get updated.

My problem this time seemed to stem from doing a hard restart in Windows.  The hard restart apparently tagged the Windows partition so that when the Windows startup process got to that mup.sys file it wouldn't boot.  When I went into Ubuntu and tried to mount the Windows partition, Ubuntu saw that there was a problem with the partition and only allowed me to mount it after I typed in that additional command to force the partition to mount.

I assumed that, in forcing the partition to mount, Ubuntu changed some sort of internal label on the partition so that when I tried to boot in Windows again it didn't see anything wrong.

If you have the same problem that I had, you might be able to boot into Ubuntu, and click on the Windows partition (it usually shows up under the Places menu).  Ubuntu will try to mount that partition and put an icon on your desktop, but it will give an error that says something about the partition not shutting down properly as well as a command you can use that will force the partition to mount.  Open the terminal application and type in that command with the word "sudo " in front of it to run it as the root user.  It will ask for a password.  Type your password, and the partition should mount.  Then, if you shutdown Ubuntu and boot into Windows it should work.

Good Luck.

---

