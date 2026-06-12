---
title: "shutdown -h now"
date: 2023-07-14
forum: General Help
---

### Post by Quarkrad on 2023-07-14
I use a terminal command to shut my Desktop off after performing a backup.  Is **shutdown -h now** OK or is there a better command?  (I'm thinking of *crashing down* vs *gentle power down*).  (This is stand-alone Desktop - no networking).

---

### Post by Quarkrad on 2023-07-14
After some more research it looks like this command is OK.  Think I'm trying to over complicate things!

---

### Post by Rubi1200 on 2023-07-14
You don't say what version you are using but if I assume it is a recent one this command can also be used:

```
sudo systemctl poweroff
```

Nothing wrong, though, with what you are doing.

No need to overcomplicate :-)

---

### Post by MAFoElffen on 2023-07-14
Well, this is a legacy thing, which I have some history using and at a point... had problems.

RE; [https://manpages.ubuntu.com/manpages/jammy/en/man8/reboot.8.html](https://manpages.ubuntu.com/manpages/jammy/en/man8/reboot.8.html)

I used to use that same command circa Ubuntu 10.04 LTS. Between 10.04, that command went into sort of a legacy phase, where the command man page changed, by it still took older options as if they were still there.

All I know is that one day, after an update that updated ubuntu-base, using
```

sudo shutdown -h now

```
For telling it to "halt"... Would lock up (freeze) my computer. Doing some research back then, I changed from using that to
```

sudo shutdown -P now

```
And have not had any problems since. It also accepts -p and --poweroff, as the same, as a legacy inclusion. (not documented)

I also use
```

sudo systemctl poweroff

```
All of those currently work, but experience tells me not to use --halt, for the just in cases. But that is just me.

---

### Post by guiverc on 2023-07-14
I'll give my 2c, but it's nothing really extra.

I see no issues with using `sudo shutdown -h now`.

Ubuntu (and GNU/Linux) can be used on many different platforms, including *mainframes* such as s390x, where the power draw can be somewhat extreme, thus its common for the shutdown (*was standard with mainframes*) to only shutdown the OS (*not the power! as that can impact the building the large machine is in*).. thus for some hardware the command will not turn off power & just do what you commanded (ie. HALT the OS).

For most us using only small PCs, or the modern servers, that maybe enough, but some hardware can be expected to have the power remain on.

FYI:  If I'm in a hurry, I just command my systems to shutdown using Linux SysRq commands (ie. REISUO), though what is available & isn't disabled can vary on release.

*Also if wondering, yes modern mainframes use a fraction of the power load of older mainframes.. but I still very much recall the mainframes that took hours to slowly power up so as to not kill the site's power. Powering up was worst, but shutdown also created a huge spike was a problem for other devices using power.*

---

