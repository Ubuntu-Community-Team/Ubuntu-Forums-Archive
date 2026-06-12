---
title: "Excessive swap use with USB HD mount"
date: 2008-05-22
forum: General Help
---

### Post by ugm6hr on 2008-05-22
This has got me confused :confused:

I have an Acer 5051AWXMi laptop running Ubuntu 8.04 AMD64.

It works just fine.  Except for one thing I can't explain.

I also have a WD Passport 120GB USB2 HD.  It is divided into 2 equal partitions - NTFS and ext3.  The NTFS partition still has the WD autorun software on.

I have used this HD before, with no issues.  In fact, I used Grsync to restore my /home files following my new installation with Hardy after creating a separate /home partition.  I have also accessed files from it since on occasion.

When it is plugged in, both partitions are auto-mounted by nautilus, and it offers to "autorun" something for me (not sure what) - I always cancel.  Only thing I can think of is the WD software, which is designed to autorun on Windows.

Yesterday, on plugging in, it mounts both partitions, and then my laptop almost locks up with excessive CPU use (up to 100% on System Monitor).  Most strikingly, my internal HD will not stop writing - System Monitor recognises a gradual filling of my 1GB swap partition (from almost 0 initially) until fully used.  Then the HD writes continue (presumably over-writing swap).

Note I haven't even accessed the external HD yet.  I thought perhaps the auto-mount was at fault, so I tried to disable that in Removable Drives and Media - but there is no option for it (although I have disabled everything there).  I also removed Grsync just in case - not sure why that would have been at fault.  I also stopped Tracker from startup sessions - and rebooted (required a hard reset) - still no luck.

Nautilus no longer opens a browser window or offers to autorun (having disabled all the "auto" options in Removable Drives and Media), but the problem persists.

I thought it could be a HD problem - but when I boot the Hardy LiveCD, the WD Passport works as expected.

As a final trial, I have backed all the data onto another HD, and am going to see if the problem still occurs after formatting the 2 partitions completely.

If that also fails, I think I'm going to try re-installing Hardy.  I'm hoping that the LiveCD allows you to re-install without having to format the /home partition...

I am sure that this is something really obvious, but I have no idea what...

Other info:
top identifies *kswapd0* & *wdp* as the main processor users after plugging the HD in.
Had a look through system log, and can't see anything that stands out, but then I don't really know what I'm looking for.

---

### Post by chrisccoulson on 2008-05-22
Do you see anything from:
```
tail -f /var/log/syslog
```
...when this happens?

---

### Post by ugm6hr on 2008-05-22
I had a look through syslog, and didn't see anything unusual.

The problem is that once plugged in, my laptop is essentially unusable, so the only way to look at syslog (or do anything) is by hard-resetting and checking the log after a reboot.  Obviously, I'm trying to avoid doing that repeatedly (I've already done it about 5 times now).

I will try and get back with the actual output - but that will take 2 reboots!

I'm seriously thinking that a reinstallation may actually be quicker (and less wearing on the HD) at this time.

Just to confirm - formatting the USB HD did not change anything.  Also, plugging in flash disks works OK.

---

### Post by chrisccoulson on 2008-05-22
I was thinking actually running 'tail -f' before you connect the drive, so you can monitor the output as it rolls out on the terminal (although if the screen freezes as well then it won't be much use).

Do you know what driver it is mounting with (ntfs or ntfs-3g)?

You could try adding an entry in your fstab for the drive where you can specify each of the drivers to see if it has any effect. You could also try using the 'noauto' option to stop it from being auto-mounted when you plug it in (i think it will stop it from auto-mounting, but I'm not sure). Then you could manually try mounting it from a TTY to see if you see the same behaviour.

---

### Post by ugm6hr on 2008-05-22
I will give the tail -f a go.  The screen does update, it is just a bit slow - but Terminal works if already running.  As I said - I won't easily be able to copy and paste the output (since the laptop doesn't work properly at that stage) - so I would need to know what I should look out for.

I am assuming it uses ntfs-3g (isn't that default in Hardy for read/write support).

As for fstab - I have never fiddled with that before, so I'd need a bit more direction.  The problem is that experimentation means that I have to reboot (hard reset) again if it freezes, which I am trying to avoid.

Much as I would like to solve the problem (to learn a bit) - I also don't want to repeatedly hard-reset.

At the moment - I am backing up my /home partition using the LiveCD in case I head towards a reinstallation.

---

### Post by chrisccoulson on 2008-05-22
Just another point though - there's probably no need to do a hard reboot. Have a look at [http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") (in particular - the Raising Elephants section).

I'm not sure what specifically you could look for in the log. You will see a few things as the drive is detected and it is mounted. Perhaps looking for anything that says 'Filesystem panic' might be a good start, although I don't think a filesystem error would cause the behaviour you see.

TBH, if swap increases quite fast, then it suggests a memory leak. That might be in the ntfs.3g driver, which is why it might be worth trying the ntfs driver to rule it out.

I would try mounting it manually from a terminal with both drivers (without logging in to GNOME, to prevent it from being auto-mounted). This may pinpoint the problem. I'm at work at the moment, so I'll try and help out a bit more later if someone else hasn't already or you've already done a re-install.

---

### Post by ugm6hr on 2008-05-22
> **chrisccoulson said:**
> Just another point though - there's probably no need to do a hard reboot. Have a look at [http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") (in particular - the Raising Elephants section).

TBH, if swap increases quite fast, then it suggests a memory leak. That might be in the ntfs.3g driver, which is why it might be worth trying the ntfs driver to rule it out.

That SysRq keyboard shortcut is interesting.  I've seen it mentioned before, but that wikipedia entry explains it well.  Cheers for that.

I've also heard the term "memory leak" before, but don't really understand it.  I'm going to go do a bit of googling on the subject.

While I'm not IT illiterate, I think this is probably a bit beyond me to resolve.  Even if I identified the problem, I need to be able to access that HD (it is my main backup HD), so I think I'll just go reinstall at this stage while I am at my dad's (and hence have access to additional HDs to transfer and retrieve files from).

Nonetheless, thanks for the help.  I know how irritating it can be to offer help to someone who decides to just do whatever they want anyway...

---

