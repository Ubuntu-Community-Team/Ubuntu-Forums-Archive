---
title: "Partial rm -rf /*"
date: 2020-01-29
forum: General Help
---

### Post by speedphoenix on 2020-01-29
**This is not a plea to recover deleted personal data**

I did something very stupid today and ran rm -rf /* (without sudo).
I quickly realized that even without root privileges, that command would be very harmful and stopped it with ^C.

Most of my HOME directory is still there, but was missing:
Some directories under /, like /tmp. those came back (at least those I aware of) after rebooting
The ~/Pictures folder (which is sad because I had quite many and relatively important ones)
The .bashrc (which I recovered from /etc/skel/.bashrc, so only my custom aliases and env variables are lost

I do not know if there are more things lost. Is there a command to see what might be missing?
When I stopped the rm command it was around /etc (and giving me permission denied messages), so why did ~/Pictures and ~/.bashrc get deleted, but not the rest of ~/?
I know it's unlikely and against the first sentence of this post, but there wouldn't happen to be a way to recover lost data, even after a reboot, would there?

---

### Post by dragonfly41 on 2020-01-29
Do not act in haste. There are ways but you must research how to approach this. Presumably you have no backups.
First point to emphasise is to stop using this drive now. The more you use it the greater the risk that you will wipe any chance of recovery.
Ideally you will do your data recovery work on another PC or laptop.
You will manually remove your drive, place it in a drive caddy or USB container (you may need to buy), and analyse as an external drive on a second computer via USB cable.
Your purchase list may require another drive of same capacity to act as a clone.
And a third drive of same capacity into which recovered files can be saved. This might be a USB flash drive.
Given these resources you can research these tags to read _many_ threads in this forum
testdisk
photorec
forensic data recovery
R-Linux

After the recovery exercise (which can take a long time, perhaps overnight runs) use one of your drives for future backups.
You can try to recover without cloning first but you stand the risk of losing all your data.
In particular, follow the forum threads at testdisk/photorec web site.

Some Tutorials: 
 (from a quick search .. not the best sources)

[https://knackforge.com/blog/selvam/restoring-removed-files-rm-rf-linux-testdisk](https://knackforge.com/blog/selvam/restoring-removed-files-rm-rf-linux-testdisk)

---

### Post by speedphoenix on 2020-01-29
That's to restore the drive, but I only lost some pictures (that will probably be very corrupted by the time I restore them). It's a shame to have lost them and it makes me kinda sad, but I can live without them.
My machine seems to be working perfectly fine, but since some files disappeared I am wondering if there are other significant things missing (maybe config files that I don't see right away?)

[U]Are there commands to scan for generic files that should be there?
[/U]
Also do you know why ~/Pictures and ~/.bashrc were deleted? is there a hard link to them somewhere?

---

### Post by dragonfly41 on 2020-01-29
Same process whether it is a drive or a file.
But I would just take a gamble and install/try photorec and specify as filters the extensions used in photos folder.

---

### Post by TheFu on 2020-01-29
/tmp/ gets wiped and recreated as needed at boot.  Nothing important should ever be in there.

For normal users, the only files that could be deleted are inside their HOME directory.  The OS is fine.
Just create a new userid, add it to the sudo group and start using that instead.

Versioned backups are not optional.  Please setup that ASAP. Learn from this mistake.  About once a yaer, I'll make a dumb mistake too and will use the backups to get those files back.  When I was first learning Unix, my mistakes happened more often, 25+ yrs later, they are down to about 1-2 a year.

As for why ~/Pictures and ~/.bashrc ... it s because those files are in your HOME and the permissions allowed it.  Learning Unix file permissions would be good. It is basic knowledge for any Unix-like system

---

