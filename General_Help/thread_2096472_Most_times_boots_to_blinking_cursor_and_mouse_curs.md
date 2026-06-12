---
title: "Most times boots to blinking cursor and mouse cursor"
date: 2012-12-20
forum: General Help
---

### Post by JoeGoalie on 2012-12-20
I'm not sure what's going on as I've never seen a problem like this.  I'm relatively new to linux, but I know the basics pretty well.  It seems like it is a race condition maybe, not sure.  Anyway, what is happening is that in the past week or so when I boot my laptop it often times just boots to a black screen with a blinking cursor and a mouse.  My laptop is a Toshiba Satellite M645-S4080 with Ubuntu 12.10, btrfs (except boot has it's own ext4 partition), and Bumblebee drivers installed.  At first I thought it was an update, so I rolled it back to an earlier snapshot and it booted just fine.  I then uninstalled the one program that wanted to update, thinking that must have been the problem.  When I rebooted after that, it still went to the black screen.  There doesn't seem to be any regular reason why it is going to the black screen, nothing will change between when it works and doesn't work.  Any ideas where to start?

---

### Post by sudodus on 2012-12-20
It is hard to find errors that do not happen every time. I suggest the following to take hardware problems into account:

Have you checked if it works better if you give it some extra time for hardware to be found and started?

The first place to do it is at the grub menu. Click the arrow down and wait for maybe 20 seconds (instead of the default 10 seconds)!

Can it be a failing HDD, that sometimes has problems reading some sector on the disk? Check the S.M.A.R.T. information!

Or if it is a software problem:

Is it *always* working properly when booted with an old kernel? You should repeat testing that, also running typical application programs and tasks.

---

### Post by JoeGoalie on 2012-12-20
> **sudodus said:**
> It is hard to find errors that do not happen every time. I suggest the following to take hardware problems into account:

Have you checked if it works better if you give it some extra time for hardware to be found and started?

The first place to do it is at the grub menu. Click the arrow down and wait for maybe 20 seconds (instead of the default 10 seconds)!

Can it be a failing HDD, that sometimes has problems reading some sector on the disk? Check the S.M.A.R.T. information!

Or if it is a software problem:

Is it *always* working properly when booted with an old kernel? You should repeat testing that, also running typical application programs and tasks.

Well, a grub menu never loads up. Perhaps I can change the wait time in the actual grub configuration somewhere. I honestly don't know how to check SMARTS for a failing hard drive. It's a two year old Intel SSD, so I doubt it's failing, but it's always a possibility. 

On my last attempts to boot up I did get an error this time. Or at least Ubuntu asked me to report an error. It was an xorg error. Also during one of the failed boots I got an error saying it was entering low graphics mode because something had failed to be recognized.

---

### Post by sudodus on 2012-12-20
The grub timeout is set in the file /etc/default/grub, which you must edit as sudo
```
sudo nano /etc/default/grub
```
On my dual (actually multi) boot system, the timeout is 10 seconds, and the hidden timeout is commented away:

```
...
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
...
```
After editing you need to run
```
sudo update-grub
```
to make the change active.

Read more about grub here: [[COLOR="Red"]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

S.M.A.R.T. info (a summary) is often displayed in the BIOS menu system. But you can also get it with the smartctl command

a summary like this:
```
sudo smartctl -H /dev/sda
```

You may need to install it by
```
sudo apt-get install smartmontools
```

and you can get more details according to the manual
```
man smartctl
```

---

### Post by JoeGoalie on 2012-12-21
So, I have no idea what changed, but it seems to be working right now.  Dsv47 private messaged me and suggested I try GDM as the default display manager because it is more tolerant of graphics issues.  I installed it and it did work, but I didn't like the inconsistent feel of the login screen and the desktop.  So, I snapshotted / and uninstalled GDM.  I then went with your suggestion and went into grub.  Menu was already set to hidden, but I changed the time to 30 seconds instead of 10.  I figured I'd start high and continue to lower it if it works.  Well, I forget to do the "sudo update-grub" and rebooted.  It came up just fine.  I then ran the update grub and rebooted again.  It came back up fine and didn't appear to take any longer to boot.  I would think that 20 seconds on a SSD would be noticable.  Either way, it appears to be working and I'm happy with it.  So, I've snap shotted again and we'll see if it stays good.  Thanks for the help, even if I'm not sure what changed. :p

---

### Post by sudodus on 2012-12-21
I'm glad it works now :-)

It could have been some update, that was not quite complete, but now, after a few days, it is complete.

It could have been a bad connection somewhere in the computer. An example: Suddenly my monitor started switching between normal colours and something greenish. After I checked and moved the connection to the monitor cable a little back and forth at the back of the computer, the colours have been good again.

Or something else ...

Anyway, welcome back to the Ubuntu Forums, if the problems return!

---

### Post by JoeGoalie on 2012-12-21
> **sudodus said:**
> I'm glad it works now :-)
 
It could have been some update, that was not quite complete, but now, after a few days, it is complete.
 
It could have been a bad connection somewhere in the computer. An example: Suddenly my monitor started switching between normal colours and something greenish. After I checked and moved the connection to the monitor cable a little back and forth at the back of the computer, the colours have been good again.
 
Or something else ...
 
Anyway, welcome back to the Ubuntu Forums, if the problems return!
 I definitely don't think it was a bad connection.  I did get the some errors early on saying it couldn't connect to the X server (connection refused).  I have no idea what would cause that, but it appears to be fixed anyway.

---

### Post by JoeGoalie on 2012-12-21
Spoke too soon. Got off of work today and it won't boot at all now. Just the blank screen with blinking cursor and mouse. Going to restore a snapshot of when GDM was installed.

---

