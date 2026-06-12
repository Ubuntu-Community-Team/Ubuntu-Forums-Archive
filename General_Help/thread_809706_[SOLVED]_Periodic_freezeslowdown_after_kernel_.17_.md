---
title: "[SOLVED] Periodic freeze/slowdown after kernel .17 upgrade"
date: 2008-05-27
forum: General Help
---

### Post by Ameneon on 2008-05-27
Lately (that is, the last few hours), I've noticed a slight freeze every few seconds (somewhere around 20-30 seconds between each), when checking the system monitor (showing all processes) nothing much appears. The Xorg process is then up at around 10-15%, but that alone shouldn't cause such a noticeable slowdown. First noticed it when the screensaver ran (the matrix screensaver which freezes, quite noticeable when the issue happens), but I figured this was an oddball thing so I didn't check closer. Then went to play my little football manager 2007 game which shows rather fluid motion which again shows off the freezes quite well.

Now, the freeze is not complete, more like a significant slowdown nearing a freeze, and lasts only a second or two, but sufficient enough (obviously) to be annoying. I upgraded to the .17 kernel this morning and subsequently rebooted, not quite sure if this problem was present at that time or not as I've only noticed it now, but I know it was not present prior to upgrade anyway.

So, obviously gonna check some more myself, but anybody else encountered this kind of problem?

---

### Post by Ameneon on 2008-05-28
Seems it's Xorg that's causing this, but can't really see why that would be. Will reboot and/or try the previous kernel to see if that makes any change..

---

### Post by Ameneon on 2008-05-28
Ok, wiser heads than mine have to say why this is, but obviously the kernel upgrade is the cause behind this, although whether the root cause is something in wine or the game itself I don't know, but when booting the .16 kernel again there are no freezes at all. Second thought, can't be neither wine nor game as the problem is visible when just the screensaver runs as well. Doesn't seem to be Xorg either as it does pop up to the same cpu usage as above from time to time, but without the freeze/lagdown symptom that the .17 kernel showed.

Thoughts/ideas?

---

### Post by Ameneon on 2008-06-04
Alas, even the .18 update behaves this way, although it for some reason does seem a bit less frequently? Perhaps just my imagination. Is there any consise page with information on the changes between each kernel release? Found [https://launchpad.net/ubuntu/hardy/+source/linux-meta/+changelog](https://launchpad.net/ubuntu/hardy/+source/linux-meta/+changelog) but that's rather minimal information..

only thing I see there are these;
* Remove linux-restricted-modules-amd64-server meta package.
* Add linux-restricted-modules-server meta package.

which ok, I have an AMD processor but as I'm running the i386 install that shouldn't matter should it?

Oh well, back to .16 for now..I sincerely hope this is not going to remain a problem as I don't want to do a complete reinstall if I don't have to and I cannot live with it as it is.

---

### Post by BlackSwordD2 on 2008-06-04
trust me you are not alone, im having the same issue but i think mines abit more severe. my .17 completely freezes and im now on .18? it works but its like tring to pull teeth with a tooth pick. i found something that might be the culprit a file on mine is running that takes up about 80-100% of my CPU called /usr/bin/X :0 -br

---

### Post by lobo-tuerto on 2008-06-07
How can you tell your kernel version?

I'm experiencing periodic slowdowns as well and they are pretty annoying... :(

I didn't have this kind of problems with Gutsy. Seems like xorg is the culprit.

The slowdowns manifest more often when I'm using the flashplayer (viewing videos on youtube for example), in those cases the firefox process or xorg will take 100% of the cpu for a while.

And no, this has nothing to do with my hardware specs :)

Help!

---

### Post by Ameneon on 2008-06-17
Sorry I haven't replied until now lobo-tuerto, this thread wasn't all that frequent so I've not been checking it. You can check your kernel version by going to the terminal and using the command **uname -a**

Also in the news :) - Today's update to kernel .19 appears to have finally solved the problem (unless it will pop up later in which case I'll have slightly more to go after at least), barring the screensaver having kicked in after upgrade, which it hasn't, I've been using the system in all normal ways the last few hours without slowdowns like earlier.

---

### Post by Sneachtuil on 2008-06-17
Previously I had been taking care of the issue by reloading compiz with:

compiz --replace

I only had the issue a few times (so it may not be related) and the new update, .19, appears to have solved the issue thus far for myself as well.

Note, if you're not using compiz, you could try:

metacity --replace

if you're using Gnome.  Otherwise, I'm not too sure what to say.

---

### Post by Ameneon on 2008-06-17
Not sure who that was for, Sneachtuil, but for myself, the system didn't as much freeze as it lagged every few seconds. Practically unnoticeable if you just browse the web or do simple office type tasks, but for anything that involves somewhat visibly ongoing processes it was a nuisance making the system practically unusable.

But thanks for the suggestion, altho here's to hoping the issue now actually is fixed in any case, for all of us :)

---

### Post by Ameneon on 2008-06-19
D'mn it is today's words, boys and girls. Ok, so after first reboot after installing the new kernel all seemed dandy, and I believe also yesterday it was the same (although now come to think of it after I fired up virtualbox to watch the EC's the system started lagging, but I attributed it then to resource usage from virtualbox). Today same behaviour shown while using virtualbox, but now that one is closed and the system is doing just like before, intermittently lagging for no apparent reason except xorg showing to get a higher load for a second or two.

I'm really really really gonna hate it if I have to reinstall, only thing I'll hate more is if a reinstall shows the same behavior after. Anybody at all got a clue as to what is causing this? Any of you guys who had this problem earlier gotten it back again or is it still gone for you?

And here I was so optimistic :(

Oh well. Just hope the .16 kernel isn't too old now.

---

### Post by Ameneon on 2008-06-20
Mm, so now it's showing itself directly after a fresh reboot with only FF3, Thunderbird, Nautilus and Totem running. Can't even watch a movie when it's like that. Only thing that's different (aside from the various updates that have come since then) from the first boot on the .19 kernel is that I ran virtualbox setup again due to the new kernel, but as that's not running now that shouldn't matter I'd assume?

Luckily the .16 kernel still works fine and without a hitch. I imagine sooner or later I'll be forced to change tho =\

---

### Post by Ameneon on 2008-06-24
Mmkay, now I'm confused. The .19 kernel is offered through the updates again? What gives?

---

### Post by Zorael on 2008-06-24
New version.
```
linux (2.6.24-19.34) hardy-proposed; urgency=low

  [Amit Kucheria]

  * Revert "Update lpia configs to move modules into the kernel"
  * LPIA: More conservative culling of LPIA config
    - LP: #240938

 -- Tim Gardner <tim.gardner@canonical.com>  Thu, 05 Jun 2008 09:30:31 -0600
```

---

### Post by Ameneon on 2008-06-24
TY :)

Peculiar though, using the same version number. I guess I could see if this one finally fixes the lag problem or not, however I've sort of given up at this point. Thanks for the answer in any case! :)

---

### Post by Ameneon on 2008-06-27
mmkay, that update was no unified success, never managed to get to the login prompt even. Welp, at least .16 still works..

---

### Post by ender1598 on 2008-06-30
I'm having similar problems lately too.  The last update I had was around 38 total and involved a reboot.  Ever since then while I'm running WoW I have this horrible intermittant freezes.  Sometimes they'll last up to 10 seconds and when I tab over to another screen to check the system monitor I'm completely pegged out.  Xorg seems to be what's causing these freezes but it only happens in game.  Never had anything like this before...  framerate was always smooth and no issues really.  I wish there was a way to undo whatever was in that update.  I'll keep watching this thread if there's any progress on fixing this problem.

---

### Post by PadreSol on 2008-07-12
Xorg seems to be the problem.  It's not clear what though.  I actually will be switching to another distro.  I've been using Ubuntu for a couple of months (Hardy) and it's terrible.  I've built my own kernels so I have the latest kernel code.  Luckily there are a lot of distros to choose from.  Good for us consumers.

---

### Post by Ameneon on 2008-08-06
While I haven't paid very much attention apparently the most recent kernel updates (still in the .19 family - can we say oops?) bring up the GUI logon again but still show off these freezes. If it was just the game I could live with it (but not precisely love it) but the system isn't usable when it is like this. I wonder why it seems to be only certain systems though, or rather, what specific hardware/software configuration is causing this for us.

As long as .16 still works all is quite ok though, but of course I'm not married to ubuntu although I'm likely gonna stick it on the msi wind I am getting..

On a sidenote, since I have a couple of games that work considerably better in Windows than in Linux (HL and Portal, mainly) I've kept my XP installation along the way and every so often boot into it to install updates and such, although it's been a couple of months since I did it, when I booted to it the other day. Updated audio drivers - reboot (huh? audio drivers? Reboot? Why?), after a process that took several minutes. Updated windows - another several minutes, and another reboot.

For all the grumping that can be done because of the frequent ubuntu updates, we are not talking the same game even when comparing windows updates with their ubuntu counterparts. Now if only the rest of the world would see the light..

---

### Post by Ameneon on 2008-08-06
Edited (duplicate post)

---

### Post by Ameneon on 2008-10-23
Alas, this problem is still present. I could live without the game (would hate it, but could live with it), but having the video freeze every few seconds when watching a movie is just not doable. After the new video drivers I can't revert back to .16 again either unfortunately, so I guess it's time for me to start troubleshooting this or ultimately go back to xp if I can't find the solution. Any tips on what I should start looking at (I've been in .16 since last post hence not working at it in the meantime)?

---

### Post by Ameneon on 2008-10-25
Well, I'll be damned. When googling for "excessive cpu usage xorg" (as opposed to just searching these forums which I've done so far to no avail) this launchpad entry with comments appeared; [https://bugs.launchpad.net/ubuntu/+bug/178400](https://bugs.launchpad.net/ubuntu/+bug/178400). And interestingly enough, one user mentions that shutting down System Monitor prevent the spikes in cpu usage from xorg. So, I tried this, and lo and behold, the system is now usable again. I guess I should've thought of something that simple but clearly I'm just not that smart.

As to why that should matter I guess one would need better knowledge of ubuntu than me to say.

Oh well. Consider me pleased and the matter solved :P

---

