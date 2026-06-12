---
title: "Autofs working - but conflicting with /media/~user"
date: 2021-01-25
forum: General Help
---

### Post by frank105 on 2021-01-25
I am building a small plex server.  I have 2 identical drives that I try to keep backed up.  One named Rosi and the second named Hammer.  I have other drives that I use occasionally.  I have autofs mounting the drives and that seems to be working just fine. 

I have autofs mounting under /automnt/Hammer for instance.

But - for some reason Rosi mounts with Autofs correctly but then seems to also try and mount at /media/user/Rosi

I know I deleted everything from fstab about Rosi so it can't be there.  Is there another place that can be trying to mount it there?  Plexserver doesn't actually do that?  Correct?  I can't remember even telling Plexserver about Rosi so that just sounds strange. 

Anyway - any tips, tricks and solutions appreciated!

Regards,

---

### Post by TheFu on 2021-01-25
Gnome with gio/gvfs are the problem mounting automatically otsd autofs. I don't have a GUI on my plex system, so I've never seen the issue. Perhaps if the file manager wasn't running, gvfs/gio wouldn't mount?  Or maybe udisks/udisks2 is doing it?  I purge that from my systems.

Could **sudo chmod 400 /media**  to stop it completely. That would prevent all storage mounts there.

---

### Post by frank105 on 2021-01-26
Hey TheFu - thanks again.  You helped me with my last hiccup too. 

Anyway - those answers are a bit ahead of my skill level - but learning more everyday so I appreciate it.  

I did take a look and I verified that Thunar settings were not set to automount USB drives.  

But  I solved it - sorta.  I am not sure why it works but here is what I  did.  Recall that ROSI and HAMMER were being automatically mounted at  /media/user/ROSI or HAMMER and intermittently.  It is important the all  caps because the new mount points are Rosi and Hammer respectively.   Cruising around I found folders in /mnt named ROSI and HAMMER along with  a third drive I use alot.  So I moved them all into a new subfolder  named Test.  Rebooted and they stopped their craziness.  I am going to  add something in autofs for the third drive and if it all works I will  be deleting Test after a few days of no problems.  

 Let me know if you see any problems with this solution.  I appreciate all the help here always!

---

### Post by TheFu on 2021-01-26
Sorry, but I don't understand the solution.  Too many redirection levels. ;)

```
sudo chmod 400 /media
```
was the only thing needed. That stops all processes from having any access inside /media, which is good for all sorts of reasons, IMHO.

/mnt/ directories don't get removed automatically, so perhaps you were using any still inside there for prior testing? Remember to clean up after yourself or you'll end up with crap all over the place.   /mnt/ is supposed to be used only by admins and only for temporary needs, BTW.  I use /mnt/ and areas under there mainly when bringing new storage up or swapping out old storage. A common use would be to move /home/ onto a new, separate, partition and file system. There's a time when doing these things that both partitions need to be available on the same system, before the quick switch into the final location happens.

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) has and easy to use table which explains the common directories and the purpose for those. It applies to all the major Linuxen, but since it comes from Unix and BSD, it applies there ... or rather, Linux stole what standards already existed on older systems with 40 yrs of thought and proven capabilities.

The gio and gvfs mount stuff is just there to convenience - avoid this for any long term mounts. There are performance penalties in using those.  For a long time, if you used any GUI to access storage that wasn't mounted through the fstab, then gvfs and gio were being used.  These things have had terrible performance for all time. I would make jokes about my grandma carrying flash storage faster than you'd be able to copy over gvfs.  The only reason it was used at all is because the Gnome guys were behind it and usability was, by-far, the most important consideration - even when it was 5x slower.  There have been a number of claims and attempts to make it faster in the last few years.  All I know is that it was bad for 20+ years before then, so I stopped using the GUI for file management.
[https://gitlab.gnome.org/GNOME/gvfs/-/issues/457](https://gitlab.gnome.org/GNOME/gvfs/-/issues/457)
[https://superuser.com/questions/175939/why-is-nautilus-slow](https://superuser.com/questions/175939/why-is-nautilus-slow) says that some GUI programs insist on looking inside every file for extra information.

But if you think it is solved - great. That's what really matters. ;)

---

### Post by frank105 on 2021-01-27
TheFu - You are right.  Whatever I thought solved it - did not.  So marked unsolved.  It is back to periodically mounting the drive back under /media/user .  It flashes an icon on the screen every few seconds.  And you are probably right - something I did temporarily and didn't clean up - but I am USUALLY pretty clean I think I must have forgotten something. 

I am thinking that I need to find what I did to cause this.  sudo chmod 400 /media did not do anything - it is still cycling to mount.  

I am going to do a little more digging to see what I can find and report back. 

Thanks again,

---

### Post by TheFu on 2021-01-27
See post #2 above. Did you purge those packages?

---

