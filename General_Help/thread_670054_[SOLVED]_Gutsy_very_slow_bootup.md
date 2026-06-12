---
title: "[SOLVED] Gutsy very slow bootup"
date: 2008-01-17
forum: General Help
---

### Post by mirzmaster on 2008-01-17
Hello,

I'm trying to help a friend of mine that recently became a Ubuntu user.  He is running Gutsy on an eMachines laptop.

Recently he started experiencing very long boot up times (I'm not certain when it started or how long this has been happening).

I installed bootchart on his machine and I've attached the resultant graph.

Now, I don't know enough to be able to tell him what exactly is wrong, but you can see that a 180 second boot up is simply unacceptable.  If I had to take a guess, based on the chart, it looks like perhaps one process is holding up the rest of the startup processes.

It's also clear from the chart that the usplash process is utilizing a considerable amount of CPU time.  Is this normal or problematic?

I'd appreciate whatever help this community can provide!

---

### Post by kesman on 2008-01-17
Edit the grub menu entry for ubuntu NOT to contain words "splash" and "quiet", then you'll be ably to see what's going on during the boot.

---

### Post by K.Mandla on 2008-01-17
It's definitely usplash that's causing the holdup. If you get a faster boot time after removing splash and quiet from the boot command, edit /boot/grub/menu.lst to remove those lines from the default options, then *sudo update-grub* to make those changes permanent.

If it's not usplash, see if you can decode the output on the screen to see what's causing the delay.

---

### Post by mirzmaster on 2008-01-17
Yeah, that is the same info logged to syslog, right?  I've taken a look at that but I'm not comfortable saying what the issue is from that.  There appear to be multiple points at which a large amount of time is spent and no error is logged.

I also have found this thread on long startup times related to usplash:  [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075).  Seems like it could be a known issue.

I've made the change to his /etc/usplash.conf file, but he won't be able to test it until tomorrow (it's very late here :) ).  I'm hoping that will take care of it!

---

### Post by mirzmaster on 2008-01-17
Just a side question:  What does "sudo update-grub" do exactly?  What happens behidn the scenes?

I notice that my changes to menu.lst often get lost with keneral or grub updates.  For example, I have a Windows boot option in there that disappears everytime one of these updates occurs.  Is update-grub a command that could help me out?

---

### Post by kesman on 2008-01-17
I lose every change maid to the menu.lst -file every time I run update-grub. Maybe that shouldn't be ran?

---

### Post by mirzmaster on 2008-01-17
> **kesman said:**
> I lose every change maid to the menu.lst -file every time I run update-grub. Maybe that shouldn't be ran?

Well it's a good thing I didn't run it then.  ;)

As well, I can report that my friend's problem has been fixed after updating usplash.conf with the correct screen dimensions, as advised in the thread I linked to earlier.

Thanks for your help, everyone! :)

---

