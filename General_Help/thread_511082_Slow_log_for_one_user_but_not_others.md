---
title: "Slow log for one user but not others"
date: 2007-07-27
forum: General Help
---

### Post by m.musashi on 2007-07-27
This has been a bit of puzzle and so far I can't find a way to fix it.

I am running feisty and about a month or so ago I noticed that it was taking a long time to log in (well, longer than before). After entering my username and password, the panel loads and then the drive activity light lights for a good 10-15 seconds solid and the rest of the desktop fails to load until after that activity. This only happen for my account. There is one other account on the system and the log in time from password to desktop is only seconds. My own log in used to be the same. I tend to mess around a bit adding apps, changing settings and such but I can't identify anything that would have caused this. Nothing special is auto starting either.

I finally got tired of it and reinstalled a couple days ago. I have /home on a separate partition so it's easy. However, the problem didn't go away. It's just as it was before. I figure it has something to do with my settings stored in /home but I have no idea how to track it down. I did delete a bunch of hidden dirs that were for apps I don't have after the reinstall as well as the .gnome and .gnome2 dirs but that didn't change anything. I was considering deleting .gconf too but not sure what that will do.

Any thoughts? Any log I could check to see what's accessing the HD for so long?

Thanks.

---

### Post by m.musashi on 2007-07-27
Hmmm, no thoughts on my little problem? No help on Launchpad either. Guess I've stumped everyone. Reformatting my /home is an option but one I'd rather avoid. If anyone has any thoughts, please share.

---

### Post by jyba on 2007-07-27
You could try the command...
```
dmesg
```
If I understand it correctly it prints out bootup messages along with the time, in seconds, when those messages were generated. Maybe if you reboot with a stopwatch in your hand and note the time when your system hangs, then check it against the output of the 'dmesg' command you might get some idea of what's slowing things down. :)

---

### Post by dando80 on 2007-07-28
Got to System->Preferences->Sessions and play start trimming back the programs you launch with your session. It may become apparent where the problem is.

---

### Post by m.musashi on 2007-07-28
@jyba - dmesg is kind of long. Is there anything particular you would like me to look for and post or just the whole thing?

@dando80 - I don't think it's related to the programs launching with my session simply because that hasn't changed (unless one of them is acting up or something). As far as I remember, these are all the defaults.

-evolution alarm notifier
-network manager
-power manager
-restricted drivers manager
-update notifier
-volume manager

I don't know why power manager loads as it's a desktop but i guess it also moniters turning off the moitor and such. Anything there look suspicious?

Thanks

---

### Post by dando80 on 2007-07-29
Did you try to isolate a problem session member by process of elimination?

---

### Post by m.musashi on 2007-07-30
> **dando80 said:**
> Did you try to isolate a problem session member by process of elimination?

Yes, but nothing seemed to make any difference. I've also attached the full dmesg output in a file (sorry it's zipped - it was too large and wouldn't upload). Maybe it will help. Remember, this only happens to one user and not the other. If it was a system setting of some sort I wouldn't expect that kind of behavior. I think it has to be related to my particular settings but pinning it down is proving to be difficult.

Thanks for the help.

---

### Post by dando80 on 2007-07-30
There doesn't seem to be any problems in the dmesg log. Can you get to a virtual terminal while it is loading the desktop and run top to see what it might be?

---

### Post by m.musashi on 2007-07-30
> **dando80 said:**
> There doesn't seem to be any problems in the dmesg log. Can you get to a virtual terminal while it is loading the desktop and run top to see what it might be?

That was a good idea but I don't think I learned much. No one process stayed on top for the whole time. It kept changing from nautilus to gnome-panel to gweather or something. All seemed relatively normal start up stuff. I did see apt-check briefly as well as restricted-manager.

Is there a way to write the top output to a log? Or something else that will monitor what is happening that I can't send to a log so it's easier to read?

Thanks again.

---

### Post by yknivag on 2007-07-30
Hi there,

You have the update manager, restricted drivers and gweather loading at start up.  All of these need a network connection.  Is your networking up, running and connected when these first attempt or is the system waiting for DHCP from your router?

It may be worth comparing the ouput from dmesg and list of programs startin at start up between the two profiles.

Finally, do you have any other desklets or desktop backgrounds/themes that the system needs to load up? Maybe these too could slow it down. Try turning them off and rebooting.

---

### Post by m.musashi on 2007-07-30
You know, that's a good theory. I recently switched from cable to dsl but I'm not sure how that would be related. Since it's an always on connection it should take long for it to connect. I also changed my gateway but again, that shouldn't cause 15 secs of drive activity. Also, that kind of problem should manifest itself on all users not just one. No other desklets are loading. Just the little weather applet on the panel and it was there long before this problem started. Nothing else is auto loading either - at least nothing I know of or added to my session. Just the items I listed above.

I appreciate the help. On the chance that it is related to dhcp, how would I determine that everything is waiting for that?

---

### Post by m.musashi on 2007-08-04
Thanks for the help and suggestions. I finally figured this out but it was really more luck than anything. I got a replacement drive and did a clean install of feisty and then copied all my /home files. I did not copy the hidden files since I didn't want end up with the same problem. The new drive seemed like a good excuse to clean this up. However, I noticed that the new /home was a lot smaller than the old one - by about 30GB. I figured that wasn't good and started to investigate. Well, I found that the .trash dir had well over 20GB in it and another .local (maybe) had about 10GB. The odd thing was that the trash itself (on the panel) had been emptied but for some reason a ton of music files that I had deleted were still in there. Removing those files from .trash solved the problem. Weird.

Thanks again.

---

