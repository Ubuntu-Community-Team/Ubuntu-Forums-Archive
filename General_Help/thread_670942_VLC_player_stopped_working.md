---
title: "VLC player stopped working"
date: 2008-01-18
forum: General Help
---

### Post by xitdedragon on 2008-01-18
```
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 477 error_code 11 request_code 144 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
 
```

I get this whenever I run vlc now. I looked all over the internet, but it seems like it's an old problem that no one has anymore. I tried a few things people suggest (on older threads), but none of them worked. I don't think I installed or changed anything that might have effected it. I was using it fine and then the sound (in vlc) stopped working. I rebooted and whenever I ran vlc it gave me the above error.

---

### Post by jeffus_il on 2008-01-18
Try turning off all desktop 3d effects.

---

### Post by c0met on 2008-01-18
Have you tried re-installing vlc? If you do that, I'd look at the list of installed files (System >> Administration >> Synaptic Packet Manager >> vlc / properties / installed files) and make a note of all the directories and make sure that you remove those too. Keep in mind that there might be hidden directories with a ./name that need to be removed.

If you do the above, then any config. file that might have been written especially for vlc should have been deleted.

---

### Post by Henrik.Schack on 2008-01-18
Could this be related to the Xorg package update that was just released ?
VLC player isn't the only thing that stopped working for me, after applying this mornings updates my Jungledisk fails with the same error as mentioned here.

---

### Post by ArbitraryC on 2008-01-18
I had exactly the same problem after the xorg update. No 3D desktop effects (in fact, the computer with compiz still works fine).

I backed out the update, and it now works fine again.

---

### Post by dusu on 2008-01-18
I have exactly the same problem with vlc
It worked fine, then an update, and it's now broken !

---

### Post by PaganHippie on 2008-01-18
It's the xorg update all right -- it broke both azureus and boinc for me.

Don't they *test* these things before releasing them?

---

### Post by ArbitraryC on 2008-01-18
I've reported a bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Comments with info on your hardware, software that breaks, etc will help them reproduce the problem and fix it.

---

### Post by Henrik.Schack on 2008-01-18
> **ArbitraryC said:**
> I had exactly the same problem after the xorg update. No 3D desktop effects (in fact, the computer with compiz still works fine).

I backed out the update, and it now works fine again.

What's the steps for backing out the update ?

---

### Post by runris on 2008-01-18
I've got the same problem.. How can I remove the latest update of xorg?

---

### Post by kesman on 2008-01-18
downgrade back to the precious version of Xorg, there's more info on other threads.

---

### Post by ArbitraryC on 2008-01-18
> **Henrik.Schack said:**
> What's the steps for backing out the update ?

This is ONLY APPLICABLE TO GUTSY!!! Doing this on different versions will probably break them worse.

sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

---

### Post by jdong on 2008-01-18
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Security team and archive administrators are aware and currently discussing this problem, and will soon pull the update (in a matter of minutes) from the archive servers.

For now, just sit tight until there's an update on the situation. I don't advise people to try to roll back to old versions of packages or otherwise home-brew fixes unless you want to risk making a mistake doing this and screwing up things even more.

As far as this fix, it's a security fix taken directly from the X.org team and several distros have chosen to adopt this patch. Upstream has been notified regarding this situation too.

---

### Post by neymac on 2008-01-18
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8  
will solve the problem

---

### Post by coltrane on 2008-01-18
I get this now as well, don't think I'll be to quick to update in future.

---

### Post by xitdedragon on 2008-01-18
Hey, no one is perfect. Even teams of software developers. Thanks for everyone that added to the thread. I will probably just live without VLC until its fixed, or possibly downgrade if I really need to.

---

### Post by fuzzyworbles on 2008-01-18
I just want to confirm that I too received with the recent Xorg update a lovely bunch of added "features" such as with VLC, OOo, and on one occasion and full blown system freeze. DO NOT UPDATE Gutsy's Xorg (current as of the date of this post).

I'm currently downgrading as suggested above. I hope it works.

---

### Post by kidford on 2008-01-18
I, too, had this problem.  It's not a big deal, though, since it was really easy to downgrade (though it was frustrating trying to find the solution, but that only took two or three minutes :) )

---

### Post by GerryGG on 2008-01-18
I successfully rolled back too. (Had to reboot before VLC was working again.) How do we find out when the update has been fixed?

---

### Post by oscarsfriend on 2008-01-18
> **GerryGG said:**
> I successfully rolled back too. (Had to reboot before VLC was working again.) How do we find out when the update has been fixed?

 Well, I've already installed it, if that helps any!

---

### Post by the.phantom on 2008-01-18
i just did the latest update ( just came out) and all is right with vlc again here

---

### Post by cytg on 2008-01-18
man .... i was just getting tuned up over this .. updated, booting and hope this works.. This plus the "Gutsy freezes" situation im in too would problary put me over the top, if this dont work!!

edit : worked :) over and out.

---

### Post by Nooreazy on 2008-01-19
This is madness!!!

Same thing happened to me :(

---

### Post by notquitemichael on 2008-01-20
for a quick note:
if you've only got the vlc crashing problem, totem works fine.
save you going through the down-grading problem.

---

