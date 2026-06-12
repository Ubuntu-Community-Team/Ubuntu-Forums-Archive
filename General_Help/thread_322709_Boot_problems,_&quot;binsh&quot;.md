---
title: "Boot problems, &quot;/bin/sh&quot;"
date: 2006-12-20
forum: General Help
---

### Post by Greevous on 2006-12-20
I restarted my pc this afternoon and when I went to boot in Ubuntu again, I get this:

```
init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS process (2012) terminated with status 1
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default process (2013) terminated with status 1
```

When I boot in recovery mode, basically the same thing happens and it doesn't boot. Is there a way to fix this before I reinstall ubuntu?:confused:

---

### Post by Greevous on 2006-12-20
Well I'm burning a new copy of the Ubuntu iso right now to reinstall. But I'd like to know if the files in my home folder could still be accessed through the live cd. I'd really like to save those, so will I have access to my Linux partitions through the live cd?

Or even better, will reinstalling Ubuntu erase files in my home folder at all?

---

### Post by po0f on 2006-12-20
Greevous,

Boot into the live CD and mount the partition that you have Ubuntu installed to.  Open up a terminal and run the following commands:
```
[FONT="Courier New"]$ mkdir /mnt/current
$ mount /dev/hdXY /mnt/current
$ ls -l /mnt/current/bin/sh[/FONT]
```
(X and Y refer to drive and partition that you have Ubuntu installed to.)

Do you remember doing anything to "fix" the Dash/Bash problem (only relevant if you are using Edgy currently)?

---

### Post by Greevous on 2006-12-20
All I know is that before I rebooted earlier, the terminal would display the same exact line as I mentioned above (about No such directory...) every time I start it. 

I've been doing so many different things in Ubuntu lately that I wouldn't be able to recall exactly what might have triggered this.

---

### Post by po0f on 2006-12-20
Greevous,

Don't worry, it might be a simple fix.  Just do what I posted and we'll see what the problem is.

---

### Post by Greevous on 2006-12-20
Alright, well I'm not worried about losing files now (I've copied them onto removable storage from the mounted drive, thanks!), just the software and settings from before. 

If I can mount any drive that is already on my pc, then I should be able to boot from them as well, right?

---

### Post by po0f on 2006-12-20
Greevous,

Not really, because you can mount partitions that have just data on them, but can you boot from those?  :)

So you backed up your data?  Good, you can back up your settings as well.  Can I assume that your removable drive is /dev/sda1?
```
[FONT="Courier New"]$ tar cvzf /dev/sda1/home-backup.tar.gz /mnt/current/home
$ tar cvzf /dev/sda1/etc-backup.tar.gz /mnt/current/etc[/FONT]
```

From here, we can try to fix the problem, or you can reinstall.

---

### Post by compwiz18 on 2006-12-20
> **Greevous said:**
> Alright, well I'm not worried about losing files now (I've copied them onto removable storage from the mounted drive, thanks!), just the software and settings from before. 

If I can mount any drive that is already on my pc, then I should be able to boot from them as well, right?
If you have to reformat, copy your home directory (**/home/your-username**) to your removable storage.  This way all that'll be left to lose are your programs.

---

### Post by Greevous on 2006-12-20
Actually, the removable drive is under media, probably because it's just a 512 MB flash drive. I'm sure I can't back up my settings onto that.


Edit >> Nope, ran out of space.

---

### Post by po0f on 2006-12-20
Greevous,

You should be able to back up at least /mnt/current/etc.  And are there any settings in your home directory that you want to specifically back up?

---

### Post by Greevous on 2006-12-20
Umm, no, I guess not. I'll probably be spending some time doing all the stuff like panels and desktop settings and beryl manager anyway. That is, if reinstallation is the only option now.

---

### Post by po0f on 2006-12-20
Greevous,

You never posted the output of:
```
[FONT="Courier New"]$ ls -l /mnt/current/bin/sh[/FONT]
```

---

### Post by Greevous on 2006-12-20
Oh sorry. It was :

```
No such file or directory
```

I thought the whole point of that was to retrieve files from my root partition, and it mounted successfully...

---

### Post by compwiz18 on 2006-12-20
> **Greevous said:**
> Actually, the removable drive is under media, probably because it's just a 512 MB flash drive. I'm sure I can't back up my settings onto that.


Edit >> Nope, ran out of space.
You can probably come close...  Mine would **almost** fit and I've got a couple games.  And the ATI drivers.  And pictures and stuff.  Just the settings would probably fit in 50 MBs.

---

### Post by po0f on 2006-12-20
Greevous,

Just run this and try rebooting:
```
[FONT="Courier New"]$ ln -s /mnt/current/bin/dash /mnt/current/bin/sh[/FONT]
```

---

### Post by Greevous on 2006-12-20
> ```
$ tar cvzf /dev/sda1/home-backup.tar.gz /mnt/current/home
$ tar cvzf /dev/sda1/etc-backup.tar.gz /mnt/current/etc
```

What would it actually be saving by backing up those things?

---

### Post by Greevous on 2006-12-20
> **po0f said:**
> Greevous,

Just run this and try rebooting:
```
[FONT="Courier New"]$ ln -s /mnt/current/bin/dash /mnt/current/bin/sh[/FONT]
```

Okay, entered that with no output (I'm guessing none is expected) and I'll try rebooting now.

---

### Post by Greevous on 2006-12-20
po0f, 

I wasn't able to boot into my exisitng Ubuntu install after that. Should I just reinstall it?

---

### Post by po0f on 2006-12-21
Greevous,

Was it the same error this time around?

---

### Post by Greevous on 2006-12-21
Yeah, unfortunately.

---

### Post by po0f on 2006-12-21
Greevous,

I foresee a reinstall in your immediate future (unfortunately).  :)  This problem is a new one on me, sorry we couldn't solve it.

---

### Post by Greevous on 2006-12-21
Hey, don't sweat it. Thank you so much for your help recovering my files. Pleasure working with you.

Greevous out.

---

